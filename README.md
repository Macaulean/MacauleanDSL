# MacauleanDSL

## Fork history and integrated pull requests

MacauleanDSL is a public fork of [Macaulean/Macaulean](https://github.com/Macaulean/Macaulean),
created in the Macaulean organization on October 13, 2026 to bring together the
Macaulay2 DSL and its verification work in Lean.

The fork started from upstream `main`. Its `main` branch was then fast-forwarded
to the head of upstream PR #41, commit
[`0e2231ba340d7cb2bd7748f6d54aa4032dc8b483`](https://github.com/Macaulean/MacauleanDSL/commit/0e2231ba340d7cb2bd7748f6d54aa4032dc8b483).
That commit already contained the complete dependency stack below, so all eleven
PR heads were incorporated with their original commit history, without separate
merge commits. This integration did not merge or close the upstream PRs.

| Upstream PR | Included work |
| --- | --- |
| [#30](https://github.com/Macaulean/Macaulean/pull/30) | Macaulay2 interpreter for integer and rational arithmetic |
| [#31](https://github.com/Macaulean/Macaulean/pull/31) | Scoped M2 DSL with `open M2` and bare Macaulay2 inputs |
| [#32](https://github.com/Macaulean/Macaulean/pull/32) | Branching, short-circuit Booleans, and blocks |
| [#33](https://github.com/Macaulean/Macaulean/pull/33) | Immutable lists, sequences, ranges, and indexing |
| [#34](https://github.com/Macaulean/Macaulean/pull/34) | Functions, closures, and lexical binding |
| [#36](https://github.com/Macaulean/Macaulean/pull/36) | Rational polynomial rings and sparse polynomial operations |
| [#37](https://github.com/Macaulean/Macaulean/pull/37) | Buchberger's algorithm and polynomial reduction in the DSL |
| [#38](https://github.com/Macaulean/Macaulean/pull/38) | Semantic indexing, mathematical views, and intent approval |
| [#39](https://github.com/Macaulean/Macaulean/pull/39) | Stage 2 pilot: agent proof jobs with isolated kernel replay |
| [#40](https://github.com/Macaulean/Macaulean/pull/40) | Proofs of polynomial arithmetic semantics |
| [#41](https://github.com/Macaulean/Macaulean/pull/41) | Coefficientwise arithmetic contracts |

The obsolete combined experiment [#35](https://github.com/Macaulean/Macaulean/pull/35)
was deliberately omitted in favor of its replacements, #36 and #37. Draft PRs
#31 and #39 were included as part of the current stack; inclusion here does not
imply completion of their broader roadmaps or a proof of full Gröbner-basis
correctness.

For the univariate GCD implementation, proved input-derived execution budget,
total correctness, and reusable worksheet certificates, see
[GCD verification](docs/m2-gcd.md).

## Upstream project

The project [Bridging proof and computation](https://www.renaissancephilanthropy.org/bridging-proof-and-computation-a-verified-leanmacaulay2-interface) integrates the theorem-proving capabilities of Lean with the computational power of Macaulay2.

We are working on a tactic for Lean that, on appropriate goals, calls Macaulay2 to perform a computation and then uses the result of the computation to produce a proof of the goal.

Initially, we would like the tactic to cover:
* ideal membership and
* factorisation (for integers, polynomials,...).

Once these initial goals are achieved, the infrastructure that we will develop should make it easier to add more features.

We are supported by [AI For Math fund](https://www.renaissancephilanthropy.org/ai-for-math-fund).

## How to install Macaulay2

### macOS
```
brew install Macaulay2/tap/M2
```

### Ubuntu
```
sudo add-apt-repository ppa:macaulay2/macaulay2
sudo apt install macaulay2
```

### Other systems
See the [wiki](https://github.com/Macaulay2/M2/wiki).

## Links

* [LeanM2](https://github.com/riyazahuja/lean-m2) (+ [fork](https://github.com/mattrobball/leanm2_fork))
* [Lean-Oscar](https://github.com/todbeibrot/Lean-Oscar)
* [mrdi file format](https://arxiv.org/abs/2309.00465)

##  Tests (Lean)

From command line:
```
lake build MacauleanTest
```

## Pure M2 worksheet: QQ polynomials

`import Macaulean.Interpreter.DSL` followed by `open M2` enables bare inputs such
as `R = QQ[x,y];` and `(x+y)^2`. Polynomial execution uses pure Lean, not the
external M2 server. See [the polynomial interface and verification boundary](docs/m2-polynomials.md)
and [the checked worksheet](MacauleanTest/InterpreterPolynomialsDSL.lean).
