---
{"title":"A Brief History of Intelligence","author":"Max Bennett-Bennett","EndDate":"2025-09-28","publisher":null,"dg-publish":true,"permalink":"/BookNotes/A Brief History of Intelligence/","dgPassFrontmatter":true,"noteIcon":""}
---

[status:: Done]
[format:: kindle/paperback]

>[!tip] Back to my [[__Index/Some Books I Have Read\|BookList]]

# Comments

# Highlights
> The physicist Richard Feynman left the following on a blackboard shortly before his death: “What I cannot create, I do not understand.” The brain is our guiding inspiration for how to build AI, and AI is our litmus test for how well we understand the brain.

-----
### Summary of Breakthrough #1: Steering
Our ancestors from around 550 million years ago transitioned from a radially symmetric brainless animal, like a coral polyp, to a bilaterally symmetric brain-enabled animal, like a nematode. And while many neurological changes occurred across this transition, a surprisingly broad set of them can be understood through the lens of enabling a singular breakthrough: that of navigating by steering. These include:

- A bilateral body plan that reduces navigational choices to two simple options: go forward or turn
- A neural architecture for valence in which stimuli is evolutionarily hard-coded into good and bad
- Mechanisms for modulating valence responses based on internal states
- Circuits whereby different valence neurons can be integrated into a singular steering decision (hence a big cluster of neurons we identify as a brain)
- Affective states for making persistent decisions as to whether to leave or stay
- The stress response for energy management of movements in the presence of hardship
- Associative learning for changing steering decisions based on previous experience
- Spontaneous recovery and reacquisition for dealing with changing contingencies in the world (making continual learning work, even if imperfectly)
- Eligibility traces, overshadowing, latent inhibition, and blocking for (imperfectly) tackling the credit assignment problem

All of these changes made steering possible and solidified our ancestors’ place as the first large multicellular animals who survived by navigating—moving not with microscopic cellular propellers but with muscles and neurons. And all these changes, along with the predatory ecosystem they begot, laid the foundation for breakthrough #2, which was when learning finally took its central role in the function of our brains.
#### Highlights
> Shortly thereafter, these cells evolved into what scientists call the “last universal common ancestor,” or LUCA. LUCA was the genderless grandparent of all life; every fungus, plant, bacteria, and animal alive today, including us, descend from LUCA.  

> Although both are large multicellular organisms that feed on other life, only the animal-survival strategy of killing level-two multicellular life requires fast and specific reflexes.* The original purpose of neurons and muscles may have been the simple and inglorious task of swallowing. 

> This means that a neuron needs to encode a range of natural variables that can vary by a factor of over a million all within a firing rate ranging only from 0 to 500 spikes per second. This could be reasonably called the “squishing problem”: neurons have to squish this huge range of natural variables into a comparably minuscule range of firing rates.  

> Here’s the beauty: Adaptation solves the squishing problem.  

> If dopamine is the something-good-is-nearby chemical, then serotonin is the something-good-is-actually-happening chemical. Dopamine drives the hunt for food; serotonin drives the enjoyment of it once it is being eaten. 

> Only much later, after bringing psychologists into his lab, did Pavlov begin to view psychic stimulation not as a confound to be eliminated but as a variable worthy of analysis. Ironically, it was a digestive physiologist with the goal of eliminating psychic stimulation who became the first to understand it. 
{ #ref-5630}


> Eligibility traces, overshadowing, latent inhibition, and blocking are ubiquitous across Bilateria. 
{ #ref-10155}


> These tricks for navigating the credit assignment problem evolved as far back as the very first brains to make associative learning work. 
{ #ref-20035}


> Along with acquisition, extinction, spontaneous recovery, and reacquisition, this portfolio of tricks make up the foundation of the neural mechanisms of associative learning, mechanisms that are embedded deep into the inner workings of neurons, neural circuits, and brains themselves. 
{ #ref-22725}


----
### Summary of Breakthrough #2: Reinforcing
Our ancestors from around five hundred million years ago transitioned from simple wormlike bilaterians to fishlike vertebrates. Many new brain structures and abilities emerged in these early vertebrate brains, most of which can be understood as enabling and emerging from breakthrough #2: reinforcement learning. These include

- Dopamine became a temporal difference learning signal, which helped solve the temporal credit assignment problem and enabled animals to learn through trial and error.
- The basal ganglia emerged as an actor-critic system, enabling animals to generate this dopamine signal by predicting future rewards and to use this dopamine signal to reinforce and punish behaviors.
- Curiosity emerged as a necessary part of making reinforcement learning work (solving the exploration-exploitation dilemma).
- The cortex emerged as an auto-associative network, making pattern recognition possible.
- The perception of precise timing emerged, enabling animals to learn, through trial and error, not only what to do but when to do it.
- The perception of three-dimensional space emerged (in the hippocampus and other structures), enabling animals to recognize where they were and remember the location of things relative to other things.

Reinforcement learning in early vertebrates was possible only because the mechanisms of valence and associative learning had already evolved in early bilaterians. Reinforcement learning is bootstrapped on simpler valence signals of good and bad. Conceptually, the vertebrate brain is built on top of the more ancient steering system of bilaterians. Without steering, there is no starting point for trial and error, no foundation on which to measure what to reinforce or un-reinforce.
![Pasted image 20250930221755.png](/img/user/_assets/images/Pasted%20image%2020250930221755.png)

Steering bilaterians made it possible for later vertebrates to learn through trial and error. And trial and error in vertebrates, in turn, made it possible for the even more perplexing and monumental breakthrough that would follow. It was early mammals who first figured out how to engage in a different flavor of trial and error: learning not by doing but by imagining.

#### Highlights
> Thorndike summarized his result in his now famous law of effect: Responses that produce a satisfying effect in a particular situation become more likely to occur again in that situation, and responses that produce a discomforting effect become less likely to occur again in that situation. 
{ #ref-38159}


> Indeed, Thorndike’s trial and error learning often goes by another name: reinforcement learning. 
{ #ref-28569}


> The second breakthrough was reinforcement learning: the ability to learn arbitrary sequences of actions through trial and error. 
{ #ref-35463}


> Minsky realized that reinforcement learning would not work without a reasonable strategy for assigning credit across time; this is called the temporal credit assignment problem. 
{ #ref-26190}


> Any attempt to understand how reinforcement learning works in vertebrate brains surely had to begin with a little neuromodulator we have already seen: dopamine. 
{ #ref-63859}


> To solve the temporal credit assignment problem, brains must reinforce behaviors based on changes in predicted future rewards, not actual rewards. 
{ #ref-63216}


> In other words, the hypothalamus is, in principle, just a more sophisticated version of the steering brain of early bilaterians; it reduces external stimuli to good and bad and triggers reflexive responses to each. 
{ #ref-11654}


> This was the first problem of pattern recognition, that of discrimination: how to recognize overlapping patterns as distinct. 
{ #ref-51036}


> This is the second challenge of pattern recognition: how to generalize a previous pattern to recognize novel patterns that are similar but not the same. 
{ #ref-47830}


> This trick is called auto-association; neurons in the cortex automatically learn associations with themselves. 
{ #ref-11775}


> Auto-association suggests that vertebrate brains use content-addressable memory—memories are recalled by providing subsets of the original experience, which reactivate the original pattern. 
{ #ref-7179}


> This creates what is called the invariance problem: how to recognize a pattern as the same despite large variances in its inputs. 
{ #ref-45485}


-----
### Summary of Breakthrough #3: Simulating
The primary new brain structure that emerged in early mammals was the neocortex. With the neocortex came the gift of simulation—the third breakthrough in our evolutionary story. To summarize how this occurred and how it was used:
- Sensory neocortex evolved, which created a simulation of the external world (a world model).
- The agranular prefrontal cortex (aPFC) evolved, which was the first region of the frontal neocortex. The aPFC created a simulation of an animal’s own movements and internal states (a self model) and constructed “intent” to explain one’s own behavior.
- The aPFC and sensory neocortex worked together to enable early mammals to pause and simulate aspects of the world that were not currently being experienced—in other words, model-based reinforcement learning.
- The aPFC somehow solved the search problem by intelligently selecting paths to simulate and determining when to simulate them.
- These simulations enabled early mammals to engage in vicarious trial and error—to simulate future actions and decide which path to take based on the imagined outcomes.
- These simulations enabled early mammals to engage in counterfactual learning, thereby offering a more advanced solution to the credit assignment problem—enabling mammals to assign credit based on causal relationships.
- These simulations enabled early mammals to engage in episodic memory, which allowed mammals to recall past events and actions, and use these recollections to adjust their behavior.
- In later mammals, the motor cortex evolved, enabling mammals to plan and simulate specific body movements.

Our mammalian ancestors from a hundred million years ago weaponized the imaginarium to survive. They engaged in vicarious trial and error, counterfactual learning, and episodic memory to outplan dinosaurs. Our ancestral mammal, like a modern cat, could look at a set of branches and plan where it wanted to place its paws. Together, these ancient mammals behaved more flexibly, learned faster, and performed more clever motor skills than their vertebrate ancestors.

Most vertebrates at the time, as with modern lizards and fish, could still move quickly, remember patterns, track the passage of time, and intelligently learn through model-free reinforcement learning, but their movements were not planned.

And so, thinking itself was born not within the clay creatures of Prometheus’s divine workshop, but instead in the small underground tunnels and knotted trees of a Jurassic Earth, birthed from the crucible of a hundred million years of dinosaur predation and our ancestor’s desperate attempt to avoid fading into extinction. That is the real story of how our neocortex and our inner simulation of the world came into being. And as we will soon see, it was from this hard-won superpower that the next breakthrough would eventually emerge.

This next breakthrough has been, in some ways, the hardest breakthrough to reverse engineer in modern AI systems; indeed, this next breakthrough is a feat we don’t typically associate with “intelligence,” but is, in fact, one of our brain’s most impressive feats.
#### Highlights
> The Helmholtz machine was, in principle, similar to other neural networks; it received inputs that flowed from one end to the other. But unlike other neural networks, it also had backward connections that flowed the opposite way—from the end to the beginning. 
{ #ref-40857}


> Hinton designed this network to learn with two separate modes: recognition mode and generative mode. 
{ #ref-40354}


> But Helmholtz suggested that human perception was doing something more than this. He suggested that instead of simply clustering incoming input patterns based on their correlations, human perception might optimize for the accuracy with which the inner simulated reality predicts the current external sensory input. 
{ #ref-19322}


> Most modern generative models are more complicated than the Helmholtz machine, but they share the essential property that they learn to recognize things in the world by generating their own data and comparing the generated data to the actual data. 
{ #ref-39658}


> Some neuroscientists refer to perception, even when it is functioning properly, as a “constrained hallucination.” Without sensory input, this hallucination becomes unconstrained. 
{ #ref-54627}


> Fittingly, Hinton even called the learning algorithm to train his Helmholtz machine a “wake-sleep algorithm.” Recognition step was when the model was “awake”; the generation step was when the model was “asleep.” 
{ #ref-779}


> This is exactly what we would expect from a generative model: perception and imagination are not separate systems but two sides of the same coin. 
{ #ref-13011}


> What we mean when we say “X caused Y” is that in the counterfactual case where X did not occur, then Y did not occur either. This is how we tease out the difference between correlation and causation. 
{ #ref-39797}


> Without counterfactuals, there is no way to distinguish between causation and correlation. 
{ #ref-55417}


> When imagining future events, you are simulating a future reality; when remembering past events, you are simulating a past reality. Both are simulations. 
{ #ref-43347}


> The only nonmammals that have been demonstrated to have such episodic memory are birds and cephalopods, the two groups of species that seem to have independently evolved their own brain structures for rendering simulations. 
{ #ref-14356}


> In AI, this process is called “generative replay” or “experience replay” and has been shown to be an effective solution to catastrophic forgetting. This is why the hippocampus is necessary for creating new memories, but not for retrieving old ones; the neocortex can retrieve memories on its own after a sufficient amount of replay. 
{ #ref-2287}


> In other words, the aPFC learns to model the animal itself, inferring the intent of behavior it observes, and uses this intent to predict what the animal will do next. 
{ #ref-37891}


-----
### Summary of Breakthrough #4: Mentalizing
There are three broad abilities that seem to have emerged in early primates:
- Theory of mind: inferring intent and knowledge of others
- Imitation learning: acquiring novel skills through observation
- Anticipating future needs: taking an action now to satisfy a want in the future, even though I do not want it now

These may not, in fact, have been separate abilities but rather emergent properties of a single new breakthrough: the construction of a generative model of one’s own mind, a trick that can be called “mentalizing.” We see this in the fact that these abilities emerge from shared neural structures (such as the gPFC) that evolved first in early primates. We see this in the fact that children seem to acquire these abilities at similar developmental times. We see this in the fact that damage that impairs one of these abilities tends to impair many of them.

And most important, we see this in the fact that the structures from which these skills emerge are the same areas from which our ability to reason about our own mind emerges. These new primate areas are required not only for simulating the mind of others but “ also for projecting yourself into your imagined futures, identifying yourself in the mirror (mirror-sign syndrome), and identifying your own movements (alien-hand syndrome). And a child’s ability to reason about her own mind tends to precede a child’s development of all three of these abilities.

However, the best evidence for this idea goes all the way back to Mountcastle. The main change to the brain of early primates, besides its size, was the addition of new areas of neocortex. So if we are to stick to the general idea—inspired by Mountcastle, Helmholtz, Hinton, Hawkins, Friston, and many others—that every area of neocortex is made up of identical microcircuits, this imposes strict constraints on how we explain the newfound abilities of primates. It suggests that these new intellectual skills must emerge from some new clever application of the neocortex and not some novel computational trick. This makes the interpretation of theory of mind, imitation learning, and anticipation of future needs as nothing more than an emergent property of a second-order generative model a nice proposal—all three abilities can emerge from nothing more than new applications of neocortex.

All these abilities—theory of mind, imitation learning, and anticipating future needs—would have been particularly adaptive in the unique niche of early primates. Dunbar argues that the social-brain hypothesis and the ecological-brain hypothesis are two sides of the same coin. The ability to mentalize may have simultaneously unlocked both the ability to successfully forage fruits and to successfully politick. The pressures of both frugivorism and social hierarchies may have converged to produce continual evolutionary pressure to develop and elaborate brain regions—such as the gPFC—for modeling your own mind.
#### Highlights

> Karl Friston, the pioneer of the theory of active inference, offers an alternative interpretation of the motor cortex. While the prevailing view has always been that the motor cortex generates motor commands, telling muscles exactly what to do, Friston flips this idea on its head: Perhaps the motor cortex doesn't generate motor commands but rather motor predictions. 

> Any level of goal, whether high-level or low-level goals, has both a self model in the frontal neocortex and a model-free system in the basal gan-glia. The neocortex offers a slower but more flexible system for training, and the basal ganglia offers a faster but less flexible version for well-trained paths and movements.

> This act of inferring someone's intent and knowledge is called "theory of mind"—80 named because it requires us to have a theory about the minds of others. It is a cognitive feat that evidence suggests emerged in early pri-mates. And as we will see, theory of mind might explain why primates have such big brains and why their brain size correlates with group size.

> There have now been numerous experiments confirming this. The granular prefrontal cortex becomes uniquely active during tasks that require self-reference, such as evaluating your own personality traits, general self-related mind wandering, considering your own feelings, thinking about your own intentions, and thinking about yourself in general.

-----
### Summary of Breakthrough #5: Speaking
Early humans got caught in an unlikely perfect storm of effects. The dying forests of the African savannah pushed early humans into a tool-making meat-eating niche, one that required the accurate propagation of tool use across generations. Proto-languages emerged, enabling tool use and manufacture skills to successfully propogate across generations. The neurological change that enabled language was not a new neurological structure but an adjustment to more ancient structures, which created a learning program for language; the program of proto-conversations and joint attention that enables children to tether names to components of their inner simulation. Trained with this curriculum, older areas of the neocortex were repurposed for language.

From here, humans began experimenting with using this proto-language with unrelated individuals, and this kicked off a feedback loop of gossip, altruism, and punishment, which continuously selected for more sophisticated language skills. As social groups expanded and ideas began hopping from brain to brain, the human hive mind “emerged, creating an ephemeral medium for ideas to propagate and accumulate across generations. This would have begged for bigger brains to store and share more accumulated knowledge. And perhaps due to this, or enabling it, cooking was invented, offering a huge caloric surplus that could be spent on tripling the size of brains.

And so, from this perfect storm emerged the fifth and final breakthrough in the evolutionary story of the human brain: language. And along with language came the many unique traits of humans, from altruism to cruelty. If there is anything that truly makes humans unique, it is that the mind is no longer singular but is tethered to others through a long history of accumulated ideas.

#### Highlights
> Linguists make a distinction between declarative and imperative labels. An imperative label is one that yields a reward: "When I hear sit, if I sit, I will get a treat" or "When I hear stay, if I stop moving, I will get a treat." This is basic temporal difference learning—all vertebrates can do this. Declarative labeling, on the other hand, is a special feature of human language. A declarative label is one that assigns an object or behavior an arbitrary symbol-"That is a cow," "That is running" —without any imperative at all. No other form of naturally occurring animal communication has been found to do this.

> An analogy to DNA is useful. The true power of DNA is not the products it constructs (hearts, livers, brains) but the process it enables (evolution), In this same way, the power of language is not its products (better teaching, coordinating, and common myths) but the process of ideas being trans-ferred, accumulated, and modified across generations. 

