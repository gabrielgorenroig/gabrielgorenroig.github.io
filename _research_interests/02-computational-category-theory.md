---
title: Computational Category Theory
---

Computational category theory means two things, essentially: from the applied side, it means computer algebra for category theory. From the theoretical side, it means a theory of _presentations_ for category theory (as in "group presentations"). I am interested in it for both applied and theoretical reasons.

On the applied side, being able to compute answers to categorical questions algorithmically seems fundamental to making category theory more applicable in the sciences. [Categorical database theory](https://categoricaldata.net/) is an excellent example of application where it is crucial—if the idea is to make any sense at all-to not only develop a mathematical theory at a semantic level but also explicitly develop its syntactic and algorithmic counterpart.

On the theoretical side, I am interested in how syntax *refines* semantics, in the sense that new phenomena arise when we become stricter about our notions of mathematical equivalence. For instance, once we have focused on syntactic descriptions we can narrow the scope even further to the *finite* ones and analyze the classes of *finitely presentable* objects that arise.

In my work, an interesting example of this phenomenon came up when trying to understand the syntactic representations of [profunctors](https://ncatlab.org/nlab/show/profunctor), which is an important point for categorical database theory. In particular, the fundamental equivalence between functors $$\mathcal{C}^\text{op} \times \mathcal{D} \to \mathsf{Set}$$ and functors $$\mathcal{C}^\text{op} \to \mathsf{Set}^\mathcal{D}$$ does not carry over to the world of finite syntactic descriptions. This is the main observation that led to the paper [Presenting Profunctors](https://arxiv.org/abs/2404.01406).
