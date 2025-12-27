# Information Theory: How to Count the World

## Course Overview

This curriculum is designed for students in the **Montgomery Blair High School (MBHS) Magnet Program**. It leverages their background in calculus and linear algebra to present information theory as a unifying "meta-language" for science, using a discrete/algebraic approach.

**Course Title:** Information Theory: How to Count the World

**Prerequisites:** Applied Statistics (concurrent or prior)

**Level:** Advanced Magnet Elective

---

## Unit 1: The Geometry of Surprise

**Focus:** Develop the notion of "information" from the perspective of counting possibilities.

### Topics

- **Information as Counting Possibilities:** A heuristic discussion of what "information" means. Why does learning that a rare event occurred tell us more than learning a common event occurred? Developing the intuition that information should be inversely related to probability, and that we need a way to count the "number of possibilities" a system can be in.

- **Multiplicative Interaction of Probabilities:** When events are independent, their joint probability multiplies: P(A and B) = P(A) × P(B). Exploring concrete examples (coin flips, dice rolls, DNA sequences) to see how the number of possible outcomes grows multiplicatively.

- **The Notion of "Average Probability":** When we have a distribution with multiple outcomes, we want to characterize it by some kind of "typical" or "average" probability. The arithmetic mean of probabilities doesn't capture the multiplicative nature of independent events. Instead, we need the geometric mean: for probabilities p₁, p₂, ..., pₙ, the geometric mean is (p₁ × p₂ × ... × pₙ)^(1/n). This is the natural "average" for multiplicative quantities.

- **The Logarithm as a Transformation:** The logarithm transforms geometric means into arithmetic means: log(geometric mean of probabilities) = arithmetic mean of log(probabilities). This is the key insight: by taking logarithms, we move from a multiplicative space (probabilities) to an additive space (information), where arithmetic means make sense. Recognizing that if information is additive (the information from two independent events should add), but probabilities multiply, the logarithm is the natural bridge: log(ab) = log(a) + log(b).

- **Entropy as Expected Surprisal:** Now that we're in the additive space (after taking logarithms), we can take weighted arithmetic means directly. Defining entropy H = -Σ Pⱼ log Pⱼ as the weighted arithmetic mean of -log(p) values. This is the expected surprisal of a distribution—the average number of bits needed to describe an outcome. We then "back out" that the surprisal function I(x) = log(1/p) = -log(p) is what we're averaging: the surprisal of each individual outcome. Connecting this back to counting possibilities: if an event has probability 1/N, it represents one of N equally likely outcomes, and I(x) = log N. Entropy is the mathematical measure that quantifies uncertainty; information theory is the meta-language that uses this measure to understand patterns across domains.

- **Jensen's Inequality:** A geometric exploration of why mixing or blurring distributions always increases uncertainty. Using the convexity of -log to show that H(weighted average) ≥ weighted average of H. This fundamental inequality will be essential for understanding relative entropy in the next unit.

- **Perspective:** Exploring how entropy quantifies uncertainty across diverse domains: (1) **Biological Diversity**—measuring genetic sequence diversity in populations, protein conformational entropy in folding, and ecological diversity indices; (2) **Neural Coding**—how sensory systems encode information (e.g., retinal ganglion cells transmitting visual information with varying entropy depending on scene complexity); (3) **Thermodynamics**—entropy as a measure of disorder in physical systems (the connection between information entropy and thermodynamic entropy); (4) **Data Compression**—why some files compress better than others (text with repeated patterns has lower entropy than random data); (5) **Language and Communication**—letter and word frequencies in natural languages (English has lower entropy than random letter sequences, enabling efficient encoding); (6) **Quantum Mechanics**—entropy in quantum states and measurement uncertainty. These examples show that entropy is a universal measure of "how much we don't know" across physical, biological, computational, and quantum systems.

---

## Unit 2: Relative Entropy (KL Divergence)

**Focus:** Measuring the "distance" between probability distributions and understanding how encoding with the wrong model costs extra bits.

### Topics

- **Defining Relative Entropy:** Introducing D(P||Q) = Σ P(x) log(P(x)/Q(x)) as a measure of "surprise mismatch"—how many extra bits you need when you use distribution Q to encode events from distribution P. Building intuition: if you think a coin is fair (Q) but it's actually biased (P), how much extra information do you waste?

- **Connection to Entropy:** Showing that D(P||Uniform) = log|X| - H(P), which reveals the extra bits beyond the minimum (entropy) when using a uniform code. This connects relative entropy directly to the entropy we developed in Unit 1.

- **Non-Negativity and Identity:** Using Jensen's inequality (from Unit 1) to prove that D(P||Q) ≥ 0, with equality if and only if P = Q. This establishes relative entropy as a proper "distance" measure (though not symmetric).

- **Simple Discrete Examples:** Calculating KL divergence for concrete cases: comparing a fair coin (P) vs. a biased coin (Q), comparing an empirical distribution to a theoretical one, and comparing different discrete distributions.

- **Asymmetry and Interpretation:** Understanding why D(P||Q) ≠ D(Q||P) in general, and what each direction means. The forward direction D(P||Q) measures the cost of using Q when P is true; the reverse measures the cost of using P when Q is true.

- **Perspective:** Exploring contexts where predictions (Q) are compared to reality (P): (1) **Betting and Prediction Markets**—horse race odds vs. actual outcomes, sports betting, election predictions; (2) **Weather Forecasting**—predicted probability distributions vs. observed weather patterns; (3) **Machine Learning**—model predictions vs. true labels, measuring how well a classifier matches the true data distribution; (4) **Hypothesis Testing**—comparing observed data to theoretical null hypotheses (e.g., Hardy-Weinberg equilibrium in population genetics); (5) **Economics**—market model predictions vs. actual market behavior, portfolio risk models; (6) **Physics**—theoretical predictions vs. experimental observations (e.g., quantum state predictions vs. measurement outcomes). These examples show that KL divergence quantifies the "cost" of using the wrong model across prediction, modeling, and scientific inference contexts.

---

## Unit 3: Typicality and the Law of Large Numbers

**Focus:** Understanding why, when you have many samples, nearly all outcomes fall into a "typical" set, and how this fundamental property (the AEP) connects to the Central Limit Theorem, revealing a deep symmetry in how randomness behaves.

### Topics

- **The Typical Set and AEP:** Understanding why, in large samples, nearly all outcomes fall into a "typical" subset of equal probability, even though individual sequences are rare. Proving that for *n* trials, P(x₁, ..., xₙ) ≈ 2⁻ⁿᴴ. This shows that the "volume" of likely outcomes is roughly 2ⁿᴴ. Visualizing why outcomes "clump" together in high-dimensional space, losing their individual complexity. The AEP (Asymptotic Equipartition Property) tells us that when you have many samples, almost everything behaves typically—this is a fundamental tool for understanding what happens in the limit.

- **The AEP as a Discrete Central Limit Theorem:** Establishing the symmetry between the Central Limit Theorem (CLT) and the Asymptotic Equipartition Property (AEP). The CLT tells us about the *shape* of noise (how sums of random variables distribute), while the AEP tells us about the *volume* of typical sequences (how many typical sequences there are, measured by entropy). Both describe concentration: outcomes concentrate around typical values. This reveals a deep connection between probability theory and information theory. **Pedagogical note:** Here we're viewing AEP through the lens of probability theory (AEP as a discrete CLT). In Unit 4, we'll flip this perspective and view CLT through the lens of information theory (CLT as a two-part encoding), revealing the same deep structure from the opposite direction.

- **High-Dimensional Concentration:** Visualizing why outcomes "clump" together in high-dimensional space. Understanding how the typical set occupies a tiny fraction of the total space, yet contains almost all the probability. This geometric intuition helps us understand why the AEP works: most of the "volume" of possibilities is irrelevant—only the typical set matters.

- **Large Deviations and Sanov's Theorem:** Using relative entropy (from Unit 2) to understand how far an empirical distribution can deviate from the true distribution. Sanov's theorem shows that the probability of observing an empirical distribution Q when the true distribution is P decays exponentially with n·D(Q||P). This connects the AEP (typical behavior) to large deviations (atypical behavior), showing how relative entropy quantifies how "atypical" something is.

- **Perspective:** Comparing the *shape* of noise in Quantum Physics (CLT) with the *volume* of typical sequences in a signal (AEP, measured by entropy). Exploring how concentration of measure appears across domains: statistical physics (how systems concentrate around equilibrium), machine learning (how training concentrates around typical solutions), and communication (how messages concentrate in typical sets for efficient encoding). Information theory provides the unifying framework for understanding these patterns.

---

## Unit 4: The Universal Two-Part Description: Data Compression and Optimal Encoding

**Focus:** Understanding how data compression works, how to encode data optimally, and the universal two-part description of data. This unit completes the connection between information theory and the real world by showing how the same two-part structure that simplifies physical systems (mean and variance) also simplifies information systems (model and error) and philosophical foundations (the relationship between the specific and the general).

### Topics

- **Two-Part Encoding: The Universal Two-Part Description:** Introducing the idea that any data can be described as "Model Description + Residual Error." The model captures the regularities (the "universal" structure), while the error captures what's left over (the "particular" deviations). When you have enough data, this two-part structure becomes the best possible: you can't do better than describing the model and then encoding the residuals. This mirrors the two-number reduction: the "mean" corresponds to the "model" (universal structure), and the "variance" corresponds to the "error" (particular deviations). Note: the model itself (the parameters like mean and variance) still needs to be encoded—we're talking about the *structure* of the encoding (two parts), not that the parameters are free. In the discrete case, we can be concrete: describe the distribution pattern, then encode the specific outcomes.

- **The Central Limit Theorem as a Two-Part Description:** Exploring how the CLT shows that when you have many samples, any distribution (regardless of its complexity) simplifies to a Gaussian, which is completely characterized by just two numbers: the mean (average) and variance (spread). All the other details about the distribution become irrelevant when you have enough data. This is a profound simplification: infinite complexity → two numbers. Using the AEP (from Unit 3) to understand why this happens: the typical set concentrates around the mean with a spread given by the variance. **Pedagogical note:** This flips the perspective from Unit 3: there we viewed AEP as a discrete CLT (information theory through probability theory's lens). Here we view CLT as a two-part encoding (probability theory through information theory's lens). This back-and-forth reveals the same deep structure from complementary angles, showing how the same mathematical pattern appears whether we're thinking about the concentration of probability (CLT) or the encoding structure revealed by entropy (AEP).

- **When Two Parts are Not Enough: Higher-Order Encodings:** Recognizing that the reduction to two numbers (mean and variance) and two-part encoding (model + error) are only the leading terms. When we have smaller datasets, care about convergence rates, need more precision, or have limited resources, we need higher-order terms. Just as we can refine a model by adding corrections (model + first-order error + second-order error + ...), we can refine our encoding structure. These higher-order terms correspond to higher-order entropies (conditional entropies of higher order, capturing dependencies beyond the simple model). This mirrors how distributions have more detailed statistics beyond mean and variance: the third statistic (skewness) captures asymmetry, the fourth statistic (kurtosis) captures tail behavior, and so on. The two-part/two-number structure is the main term of a deeper expansion that includes corrections. This completes the deep connection: just as physical systems have a full expansion (mean + variance + skewness + kurtosis + ...), information systems have (model + first-order error + second-order error + ...). The same mathematical structure governs both how physical systems simplify (reduction to statistics) and how information systems compress (encoding structure). When we need perfect reconstruction, we need all the statistics (all moments). As we allow approximations or have limited resources, we can use fewer bits, and the higher-order terms become less important. **Important note:** The "two numbers" (mean, variance) themselves need encoding—we're describing the asymptotic structure where the model description becomes relatively small compared to the data. In the discrete case, we can be concrete about this; the rigorous continuous case involves differential entropy and gets very technical.

- **Perspective:** Exploring how the reduction to two numbers (and when we need more) appears across essentially all domains of knowledge: **Physics and Mathematics**—statistical mechanics (energy and entropy), quantum mechanics (expectation values and uncertainty), the Central Limit Theorem; **Biology**—population genetics (mean fitness and variance), ecological diversity indices; **Social Sciences**—demographic patterns, economic distributions, voting behavior; **Literary Theory**—the tension between general narrative structures and specific textual details, the way individual works participate in larger genres; **Philosophy**—the relationship between individual experiences and general concepts, how specific examples give rise to abstract principles, the structure of knowledge itself; **Machine Learning**—bias and variance tradeoff, the fundamental tension between model complexity and generalization; **Art and Aesthetics**—the balance between general principles of beauty and specific artistic expressions; **Data Compression**—lossy compression (JPEG, MP3) where the tradeoff between bits and quality is essential. **Rate Distortion Theory** (requiring differential entropy for rigorous treatment) provides the mathematical framework for understanding this tradeoff in continuous systems: the rate-distortion function R(D) tells us the minimum bits needed for a given distortion level, completing Shannon's theory alongside channel capacity. This universal pattern suggests a deep structural principle underlying how complexity simplifies when you have many samples—a principle that appears to be a fundamental feature of how the world (and our understanding of it) is organized. The reduction to two numbers (with higher-order corrections when needed) is not just a mathematical curiosity; it is a universal pattern that structures reality itself.

---

## Implementation Notes for MBHS

- **Finitary Approach:** All concepts are introduced via discrete sums and combinatorics to keep the focus on the "logarithm of probability" rather than integral calculus.

- **Computation:** Students use Google Colab or Python to simulate Huffman trees and calculate the entropy of natural languages vs. code.

- **Synthesis:** The course concludes by showing that the **CLT** and **AEP** are two sides of the same "Concentration of Measure" coin—one describes the limits of physical noise, the other the limits of human (and biological) communication. A key pedagogical insight throughout the course is the back-and-forth between these perspectives: viewing AEP as a discrete CLT (Unit 3) and then viewing CLT as a two-part encoding (Unit 4) reveals the same deep structure from complementary angles. This perspective-flipping demonstrates how information theory serves as a unifying meta-language: the same mathematical patterns (quantified by entropy and related measures) appear whether we're thinking about probability distributions, entropies, or the structure of knowledge itself.

