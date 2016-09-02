SPECTRA[SolveLMI] - Solve Linear Matrix Inequalities



Calling sequence

SolveLMI(A, listofranks, options)



Parameters

A - linear matrix with rational coefficients

listofranks (optional) - a list [r1,...,rp] of integers

options (optional) - a set of options.


Description

o The command SolveLMI solves the linear matrix inequality A>=0 (A positive semi-definite) where A is the
  input linear matrix.

o if listofranks is not given or listofranks is the empty list, then by default listofranks:=[0,1,...,m-1]
  where m is the size of A. If r is in listofranks, SolveLMI checks whether A>=0 has a solution x such that
  A has rank r at x. Solutions of rank strictly smaller than the expected rank might be returned.

o if options is not given, or if it is the empty set, the output of SolveLMI is a vector x with A>=0 at x,
  if and only if such a point exists. Otherwise, the output is the empty list [].
  Possible options:
        o rank   - outputs the rank of A at the solutions
        o deg    - outputs the algebraic degree of the solutions
        o rur    - outputs rational univariate representations of the solutions
        o allpts - outputs all solutions. By default, that is if allpts is not in options,
	           SolveLMI returns the first computed solution
        o regul  - outputs information about regularity assumptions
        o debg   - debugger for internal procedures

Related work

Henrion, Naldi, Safey El Din: Exact algorithms for linear matrix inequalities, 2015 (http://arxiv.org/abs/1508.03715)


Examples

> with(SPECTRA);

                                                                                       [SolveLMI]

> A:=Matrix([[1,X1,X2],[X1,1,X3],[X2,X3,1]]):
> SolveLMI(A);

                                                                      [[X1 = [1, 1], X2 = [-1, -1], X3 = [-1, -1]]]

> SolveLMI(A,[0]);   

                                                                                           []

> SolveLMI(A,[1],{rnk,deg,rur,allpts});
[[[[X1 = [1, 1], X2 = [-1, -1], X3 = [-1, -1]], 1, 4], [[X1 = [-1, -1], X2 = [1, 1], X3 = [-1, -1]], 1, 4], [[X1 = [-1, -1], X2 = [-1, -1], X3 = [1, 1]], 1, 4], [[X1 = [1, 1], X2 = [1, 1], X3 = [1, 1]], 1, 4]],

      4        2                  3                  2                   2                  2
    _Z  - 42 _Z  - 64 _Z + 105, _Z  - 21 _Z - 16, [_Z  + 16 _Z + 19, 2 _Z  + 8 _Z + 26, 4 _Z  + 4 _Z - 44]]
# spectra
