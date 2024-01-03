---
layout: post
title:  "Yearning for Yet More Python Packaging Best Practices"
date:   2024-01-02
---
_Epistemic status: Technically, a professional opinion_

Today at my work, we had a debate about how libraries should declare the support of their dependencies. Some practices are uncontroversial. In particular, if a library `A` declares a depedency on library `B`, it seems natural for the author of `A` to declare a lower bound on the version of `B`:

```python
install_requires = [
    "B>=1.0.1"
]
```

This makes intuitive sense, since it is likely that there is some additional functionality in versions of `B` greater than `1.0.1` that `A` depends on.

Furthermore, if there is some _undesired_ change in a subsequent version, we may specify an upper bound.

```python
install_requires = [
    "B>=1.0.1,<2"
]
```

However, an interesting question arises when we consider the following; should a library preemptively declare an upper bound on versions, or should it wait for a breaking change to be introduced? For example, if I write a library that depends on `requests`, it seems like it may be a bit bold to declare that "any version of requests greater than 2.31.0" will be supported, which is the implication of `requests>2.31.0`. A related but perhaps more concrete question is whether a version specifier such as `requests>=2.31.0` implies that the author has actually taken precautions to test with versions greater than `2.31.0`, in order to ensure their compatibility.

The side arguing that library authors' possess a positive duty to test with higher versions contends that unsuspecting installers of a library should not be subjected to errors because they have found an incompatibility with a potentially new version of the dependency. This makes sense, but ideally with good use semantic versioning, should only rarely occur.

The side arguing against contends that the upper bound restriction is too restrictive for library consumers, which is, in my opinion, a more realistic concern.

However, it does not appear that there is any broadly accepted Python best practice for this. It appears that the [Python Packaging User Guide](https://packaging.python.org/en/latest/discussions/install-requires-vs-requirements/) has some examples of lower bound dependencies without upper bounds, as well as some prose to support only adding upper bounds in the case of a known incompatibility. I haven't found any other authoritative sources. Additionally, many popular Python packages have some dependencies in which they do not provide an upper bound. Despite this, I am still surprised there is not more official guidance for public library authors.

My team did discuss some strategies for mitigating this issue though. One idea I liked was to have a timed CI job (not a part of the PR pipeline), that tested the library with the most recent allowed versions of the dependencies. This would allow the library author's to quickly discover potential incompatibilities without having to block PRs for reasons unrelated to them.

Another interesting idea was to have a `dependabot` like resource that listened for new releases of dependencies and created PRs automatically for testing them with the library, as well as bumping an upper bound version. This seems more complicated to me, and it forcibly restricts the usage of new versions of dependencies with older versions of the library, but it does allow consumers to guarantee that every version that satisifies the dependency specifier in fact works correctly.

Alas, we decided to have relaxed version specifiers, but I hope someone in the community will decide this for us, so we don't have to spend the time!