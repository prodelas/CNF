# CNF and D&P Algorithm Implementations

It contains code in `Haskell` which implements the retrieval of a given
a propositional formula a conjunctive normal form of it.

The following list represents a list of the functions involved in the
the code:

1. The fnc:

		clausularform :: Formula -> Formula

1. The subsumption algorithm (limited number of variables):

		sieveClauseList :: [Ic] -> [Ic]

1. Transform a formula and with a set of formulas into a set of
of clauses:

		form2claus :: Formula -> [[Literal]]
		setform2clausImp :: [Formula] -> [[Literal]]

1. The Davis&Putnam algorithm:

		unsatisfiable:: [[Literal]] -> Bool
		satisfiable :: [[Literal]] -> (Bool, [[Literal]])

1. The deduction theorem:

		deductionTheorem :: [Formula] -> Formula -> [Formula].

1. Semantic implication:

		sImplies :: [Formula] -> Formula -> Bool
		extsImplies :: [Formula] -> Formula -> (Bool,[Literal])

1. Recognise whether a formula is a tautology or not:

		tautological :: Formula -> Bool

1. Recognise whether two formulae are equivalent or not:

		isLogEquiv :: Formula -> Formula -> Bool


Let us nuance something else:

1. `distribute`: apply `dak` as many times as necessary to arrive at the clause form.
clausular form. Uses the `alternation` function which measures the minimum number
of times it needs to be applied.

1. `associate`: apply the `aka` function to a formula in clause form
the minimum number of times necessary for all conjunctions and disjunctions to be left-associative.
disjunctions are left-associated.

1. `clausularform`: apply the above functions in the appropriate order
to transform a formula into an equivalent formula that is in clausal form.
clausular form.

1. `form2claus`: Given a formula, the `form2claus` function extracts its
clauses. It removes tautological clauses and repeated literals from each
repeated literals from each of the clauses.

1. `setform2claus`: Given a set (list) of formulas, extract their clauses.
It removes tautological clauses and repeated literals in each of the clauses.
clause.

1. `unsatisfiable`: Given a list of clauses, returns `True` or `False` depending on whether the clause set is unsatisfiable or satisfiable. It makes use of the Davis&Putnam algorithm.

1. `satisfiable`: Given a list of clauses, returns `True` or `False`, depending on whether the clause set is satisfiable or not.
It also returns a list of literals, which when interpreted as true, satisfies
interpreted as true, satisfies the set; in case of being
unsatisfiable, it gives the empty list.

1. `form2claus`: Does the same as `setform2claus`.

1. `sImplies`: Given a set of formulae, and a formula, it says if
it is a logical consequence of the set of formulas.

1. `extsImplies`: Same as above, except that in the case that the implication is false, it also gives a list of literals whose
implication is false, it also gives us a list of literals to show why the implication is false.
shows us why the implication is false.
