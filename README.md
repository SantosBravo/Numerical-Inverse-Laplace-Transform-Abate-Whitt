# Numerical Inversion of Laplace Transforms Using the Euler Algorithm of Abate and Whitt

Mathematica implementation of the EULER algorithm of Abate and Whitt [1] for numerically inverting Laplace transforms. It is essentially a translation from UBASIC to Mathematica of the algorithm EULER on pages 7–8 of [1]. Since Mathematica supports arbitrary-precision arithmetic, roundoff error can be controlled simply by raising the working precision. This is important because the series involved is alternating.

## Functions

All functions are defined in `EulerILT_and_usage_examples.nb`.

| Function | A (aa) | n (ntr) | m (mEuler) | Working precision | Typical accuracy in the examples* | Returns |
|---|---|---|---|---|---|---|
| `EulerILT` | 19.1 | 15 | 11 | machine | ~1e-8 (relative) | value |
| `EulerILTwithErrors` | 19.1 | 15 | 11 | machine | same as `EulerILT` | `{value, truncation error, discretization error, total error estimate}` |
| `EulerILTplus` | 30 | 100 | 30 | 30 digits | ~1e-13 | value |
| `EulerILTplusPLUS` | 80 | 200 | 40 | 65 digits (default) | ~1e-35 | value |

\* The accuracy is limited by the discretization error, which is approximately exp(-A) |f(3t)| (see [2], Eq. (11)).

## Installation

Open `EulerILT_and_usage_examples.nb` in Mathematica and evaluate the cells that define the functions, or copy the definitions you need into your own notebook and evaluate them. No packages are required.

## Usage

1. Write the Laplace transform you want to invert, f(s, p1, p2, ...), in the form `f[s_, {p1_, p2_, ...}]`. Here `s` is the Laplace variable and `p1, p2, ...` are the parameters. If there are no parameters, write `f[s_, {}]`.
2. `EulerILT[f, t, {p1, p2, ...}]` returns the numerical value of the inverse Laplace transform of `f[s, {p1, p2, ...}]` at the point `t > 0`.

Example (exact result: Exp[-x^2/(4t)]/Sqrt[t]):

```mathematica
f[s_, {x_}] := Sqrt[Pi/s] Exp[-x Sqrt[s]];
EulerILT[f, 1, {2}]              (* 0.367879444..., exact value 0.367879441... *)
EulerILTwithErrors[f, 1, {2}]    (* {value, truncation error, discretization error, total error estimate} *)
EulerILTplus[f, 1, {2}]          (* uses 30 digits *)
EulerILTplusPLUS[f, 1, {2}]      (* uses 65 digits by default; an optional fourth argument sets the precision *)
```

## Notes and limitations

- With `EulerILTplus` and `EulerILTplusPLUS`, use exact numbers (for example `8/10` instead of `0.8`, and an exact `t`); otherwise machine-precision numbers limit the accuracy and a warning is printed.
- The error estimates are practical estimates, not rigorous bounds.


## References

[1] Abate, J., Whitt, W. The Fourier-series method for inverting transforms of probability distributions. Queueing Systems 10, 5–87 (1992). [https://doi.org/10.1007/BF01158520](https://doi.org/10.1007/BF01158520)

[2] Abate, J., Whitt, W. Numerical inversion of Laplace transforms of probability distributions. ORSA Journal on Computing 7, 36–43 (1995). [https://doi.org/10.1287/ijoc.7.1.36](https://doi.org/10.1287/ijoc.7.1.36)

## License

This work is licensed under the Unlicense. See the `UNLICENSE` file for more information.
