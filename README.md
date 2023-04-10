# Numerical Inversion of Laplace Transforms Using the Euler Method of Abate and Whitt

In the Mathematica notebook _EulerILT_and_usage_examples.nb_ I provide the Mathematica function _EulerILT_ , which uses the Euler algorithm described by Abate and Whitt in [1], to numerically invert Laplace transforms. The function _EulerILTwithTruncationError_, also provided in _EulerILT_and_usage_examples.nb_, is the same as _EulerILT_, but includes an estimate of the truncation error of the procedure (see [1] for details). The function _EulerILT_ (and _EulerILTwithTruncationError_) is basically the translation from UBASIC to Mathematica of the algorithm EULER of pages 7 and 8 of [1].

## Installation

Copy the function EulerILT (or EulerILTwithTruncationError) into a Mathematica notebook and evaluate it.

## Usage

1. You have to write the Laplace transform function you want to invert numerically f[s,p1,p2,...] in the form f[s,{p1,p2,...}]. Here s is the Laplace variable and p1,p2,... are parameters of the function. If there are no parameters and the function is just f[s], then write it as f[s,{}].
2. EulerILT[f,t, {p1,p2,...}] returns the numeric value of the inverse Laplace transform of f[s,{p1,p2,...}] evaluated at point t.


## References

[1] Abate, J., Whitt, W. The Fourier-series method for inverting transforms of probability distributions. Queueing Systems 10, 5–87 (1992). [https://doi.org/10.1007/BF01158520](https://doi.org/10.1007/BF01158520)

## License

This work is licensed under the UNLICENSE license. See the LICENSE file for more information.
