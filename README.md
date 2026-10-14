<!-- solve-problem:8751e951-2014-405a-9ffc-5a4c15b49e01 -->
# Universal zipper unfolding of convex polyhedra

A [Tangle Solve problem](https://solve.tangle.tools/problems/8751e951-2014-405a-9ffc-5a4c15b49e01).

## What is the problem?

Let P be a convex polyhedron in ℝ³. Cutting P's surface along a collection of edges/curves and flattening into the plane yields an *unfolding*; the unfolding is *nonoverlapping* if the flattened surface pieces have disjoint interiors. An unfolding is a *zipper* (or single-source, single-sink) unfolding if the cut graph is a **single path** — one connected cut with no branching, starting at one point on the surface and ending at another. The cut path may traverse the interior of faces (it need not follow edges of the polyhedron); it must not self-intersect except possibly sharing endpoints (definitions vary — see Warnings).

**Open question:** Does every convex polyhedron admit a nonoverlapping zipper unfolding?

Formal setting: input is the combinatorial and geometric description of a convex polyhedron (vertices, faces, or an oracle for the surface); output is a cut path γ on ∂P (a polyline crossing finitely many faces) such that ∂P \ γ is a topological disk whose planar development is nonoverlapping. The related edge-restriction variant (cut path must lie on the 1-skeleton) is known to fail for some polyhedra and must not be conflated with this general question.

## Why does it matter?

A positive answer means any convex polyhedral shell can be fabricated from sheet material by cutting along one continuous seam — attractive for manufacturing (laser/Waterjet cutting, sheet-metal) and for origami-inspired deployable structures, where a single seam simplifies actuation and sealing. It would also refine the grand open problem of whether every convex polyhedron has a nonoverlapping edge unfolding (TOPP, Demaine–O'Rourke's *Geometric Folding Algorithms*, Ch. 22), showing that an extremely constrained cut structure suffices. A negative answer (an explicit counterexample polyhedron) would be the first such, with major implications for the edge-unfolding problem.

## What's already known?

- **Edge unfoldings:** Open since ~1975 (Shephard) whether every convex polyhedron has a nonoverlapping unfolding cutting only along edges; all known nonoverlapping unfoldings of convex polyhedra via algorithms are "general" cuts. No convex polyhedron is known to lack a nonoverlapping unfolding of any kind.
- **Zipper edge unfoldings:** Demaine, Demaine, Lubiw, Shallit & Shallit (2010) showed that restricting *both* the zipper structure and edge-only cuts fails: there exist convex polyhedra (e.g., certain tetrahedra, and a polyhedron with every vertex odd-degree) admitting no nonoverlapping zipper *edge* unfolding. They also show families (e.g., all Platonic solids, "nested tetrahedra" constructions) that do have zipper edge unfoldings.
- **General zipper unfoldings:** Open. No counterexample is known even with arbitrary cuts, and no general theorem produces zipper unfoldings. Non-edge (general-cut) unfoldings are known nonoverlapping for, e.g., infinitesimally truncated vertices and orthogonal polyhedra, but none of these techniques enforces the single-path constraint.
- Tools used: source unfoldings, ridge trees, cut locus analysis, spanning-paths on cut trees, shortest-path arguments.

## What would count as solving it?

1. **Positive:** A proof that every convex polyhedron admits a nonoverlapping zipper unfolding — i.e., an explicit construction of a cut path (possibly described via the cut locus or a Hamiltonian path in a suitable structure) with a nonoverlap proof. Even a proof for a broad class (all simplicial polyhedra, all polyhedra with ≤ n vertices for growing n) would be major partial progress.
2. **Negative:** An explicit convex polyhedron and a proof that no single cut path on its surface yields a nonoverlapping planar development. This requires ruling out uncountably many cut paths — the hard direction.
3. **Algorithmic refinement:** A polynomial-time algorithm that, given a polyhedron, outputs a nonoverlapping zipper unfolding (given 1).

## How to start

1. Read Demaine & O'Rourke, *Geometric Folding Algorithms* (2007), Chapter 22 (edge unfoldings) and Chapter 24, for the background landscape and the source/ridge-tree machinery.
2. Read Demaine et al. (2011), "Zipper unfoldings of polyhedral complexes" — it defines the zipper model precisely and contains the negative edge-only results; understand exactly which obstructions there use edge-ness.
3. Natural approach: the source unfolding cuts along the full cut locus (a tree); a zipper unfolding asks whether a single path in/near the cut tree (or the ridge tree) suffices. Study whether a spanning path of the ridge tree of the star unfolding avoids overlap for "most" polyhedra; characterize when it fails.
4. Obstacle: nonoverlap proofs are inherently global; the single-path constraint destroys the locality that makes source unfoldings provably nonoverlapping. Consider starting with flat-vertex-free simplicial polyhedra or perturbation/continuity arguments.

## Key references

- E. D. Demaine and J. O'Rourke, *Geometric Folding Algorithms: Linkages, Origami, Polyhedra*, Cambridge Univ. Press, 2007. — The standard reference; Chs. 21–25 cover polyhedron unfolding, source unfoldings, and the open edge-unfolding problem.
- E. D. Demaine, M. L. Demaine, A. Lubiw, A. Shallit, J. Shallit, "Zipper Unfoldings of Polyhedral Complexes," *Proc. 22nd Canad. Conf. Comput. Geom. (CCCG 2010)*; extended in *Graphs and Combinatorics* (2012/2013) (verify journal details). — Defines zipper unfoldings, gives positive results (e.g., Platonic solids) and negative results for zipper *edge* unfoldings of convex polyhedra.
- TOPP (Topology and Open Problems Project) Problem 77 / Demaine–O'Rourke open-problem list. — Tracks status of zipper-unfolding and related unfolding questions. (verify numbering against the current list)
- Open Problem Garden / "Unfolding polyhedra" entries. — Secondary tracking of the edge-unfolding and general-unfolding problems. (verify)

## Warnings

- **Do not conflate the edge-only zipper question (settled negatively) with the general cut-path question (open).** The census record explicitly flags this; a "solution" that only addresses edge cuts is not a solution.
- Definition subtlety: some papers require the zipper path to be simple (non-self-intersecting); others allow the two endpoints to coincide ("closed zipper"). Fix the convention up front.
- "Nonoverlapping" means disjoint interiors; boundary touching is allowed.
- Beware of claimed counterexamples from the nonconvex world (e.g., Schlickenrieder's thesis, nonconvex zipper results) — the problem here is strictly for convex polyhedra, where no nonoverlap failure is known for any cut structure.
- Negative-direction proofs face a quantifier over continuum-many cut paths; naive enumeration of "cut types" is a known dead end.

---
*`ALGO-000153` · unverified*

## Acceptance guidance

1. **Positive:** A proof that every convex polyhedron admits a nonoverlapping zipper unfolding — i.e., an explicit construction of a cut path (possibly described via the cut locus or a Hamiltonian path in a suitable structure) with a nonoverlap proof. Even a proof for a broad class (all simplicial polyhedra, all polyhedra with ≤ n vertices for growing n) would be major partial progress.
2. **Negative:** An explicit convex polyhedron and a proof that no single cut path on its surface yields a nonoverlapping planar development. This requires ruling out uncountably many cut paths — the hard direction.
3. **Algorithmic refinement:** A polynomial-time algorithm that, given a polyhedron, outputs a nonoverlapping zipper unfolding (given 1).

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/8751e951-2014-405a-9ffc-5a4c15b49e01?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000153.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000153)
