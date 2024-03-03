## Proof Repair across Quotient Type Equivalences

This repo contains the artifact for "Towards Proof Repair in Cubical Agda" by Cosmo Viola, Max Fan, and Talia Ringer. The paper is currently under submission ([preprint](https://arxiv.org/abs/2310.06959)). This repo contains the artifacts as-submitted.

There are two parts to this artifact:

- An internal view of proof across quotient type equivalences in Cubical Agda (located in [`cubical`](cubical)). This is currently manual due to engineering and theoretical limitations of cubical type theory.
- An external view of proof repair across quotient type equivalences (via setoids) in Coq (located in `/pumpkin-pi`). This is automated by a prototype that extends the original pumpkin-pi automation.

## Cubical Agda Manual Case Studies
To run our Cubical Agda case studies, you should install [Cubical Agda](https://github.com/agda/cubical)
The main corresponding files for our case studies in Cubical Agda can be found in the following locations:

- [`cubical/grothendieck_int_equiv.agda`](cubical/grothendieck_int_equivalence.agda) (for the integer case study in Cubical Agda)
- [`cubical/equivalence_queue.agda`](cubical/two_list_queue_equivalence.agda) (for the queue case study in Cubical Agda)


## Quotient Types Extension to Pumpkin Pi
To fetch and build everything, make sure you have Coq 8.9.1 installed (later versions are not currently supported).

Then, to build everything, run:
```
cd pumpkin-pi/plugin
./build.sh
```

To run the relevant case studies files, run:
```
./setoids.sh
```

which will first run the setoid repair tests contained within `pumpkin-pi/plugin/coq/ToSetoidTest.v`,then build the following two case studies:
- `pumpkin-pi/plugin/coq/playground/grothendieck_int_equivalence_repair_tool.v` (for the integer case study in Coq)
- `pumpkin-pi/plugin/coq/playground/TwoListQueue/two_list_queue_equivalence_repair_tool.v` (for the queue case study in Coq)

The script will also build `UIPList.v`, as a dependency of the queue case study. 
In our queue case study, we parameterize over lists/queues of type A, where UIP holds on A. `UIPList.v` proves that if UIP holds on A, it will hold on list A. 
We do not assume it for all types, so we are not adding an axiom to our theory. 


## Funding Acknowledgements
This research was developed with funding from the Defense Advanced Research Projects Agency. 
The views, opinions, and/or findings expressed are those of the author(s) and should not be interpreted as representing the official views or policies of the Department of Defense or the U.S. Government.
