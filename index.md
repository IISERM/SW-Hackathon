# Vision

The aim of this hackathon is to come up with algorithms to solve problems in biology and bio-computation. The organizers feel that programming is in everyone's blood, for we are inherently algorithmic. Hence, the questions do **not** expect that you know some fancy set of functions to solve these problems. They just need you to think about how you would go about doing something.

Most of the questions are **not** inherently biological in nature. Biology however does provide motivation to solve these problems.

Feel free to contact the organizers if you need additional information.

# [Click here for Rules](./rules)

# [Click here for Results](./2022/results.md)

# Questions

## Question 1[20 Marks]

Dr. Charles Adami and Dr. Chris Ofria are building a software platform for simulating evolution. The first step is to simulate DNA replication and mutation over generations. DNA often fails to copy accurately and the following are the 3 main types of mutations it undergoes-

1. Base Substitution &rarr; Substitution of a base by a different one.
2. Insertion &rarr; Insertion of a new base.
3. Deletion &rarr; Deletion of an existing base.

The probability of these mutation is different. The lab has decided to store DNA sequences in a [FASTA](https://en.wikipedia.org/wiki/FASTA_format) file. Your job as an intern in their lab is to create a function that takes the path of a fasta file, the probabilities of these 3 types of mutations, and the number of generations and simulate DNA replication over the given number of generations. The final output is the evolved DNA sequence. The function should also print the total number of mutations and the difference in the length of the final DNA strand and the initial one. You can use this [fasta file](./seq.fasta) for testing the code.

### Input

`FASTA file path`, `Probability of substitution`, `Probability of Insertion`, `Probability of Deletion`, `Number of Generations`

### Output

1. Final DNA strand after evolution
2. Total number of mutations
3. Difference in the length of the final DNA strand and the initial one


## Question 2[40 Marks]

A set of 5 islands have been recently discovered in the Pacific Ocean. The islands have remained untouched for long, as a result,  there lies a great bounty of flora and fauna as well as some undiscovered species of birds and animals. Dr. Peter Prasad and Dr. Rosemary Jain, who take an introductory course in Evolutionary Biology at the Pacific Institute of Evolutionary Science, Education and Research, had decided to send a bunch of 50 students, 10 each to these islands for studying the diversity of birds there. 

During their tiring semesters, the students have **diligently and honestly** gone birding everyday and collated their data weekly. They caught birds and banded their legs to ensure that birds are not double counted. After a tiresome work of 3 months, the students have sent all their data in excel files to the instructors. Your job, as an honorary TA of the course and the chief data analyst of their lab, is to analyze this data and study the bird diversity of these islands.

The first step in studying biodiversity is to check if the data is complete. In order to make a statement about the species diversity of a region, a data analyst needs to make sure that most of the unique species in a region have been discovered. In order to do that, the analyst first needs to plot a species accumulation curve and check if it reaches saturation. A species accumulation curve is a plot between the cumulative number of species and the sampling effort(number of weeks in this case). Here's an example of 2 species accumulation curves, one of them reaching saturation-

![SpeciesAccumulationCurve](./SpeciesAccumulationCurve.jpg)

If a species accumulation curve does reach saturation, the next step is to calculate the diversity index. The **Shannon-Weiner index** is a good measure of the [alpha-diversity](https://en.wikipedia.org/wiki/Alpha_diversity) of an island. It's given by-

$$
H=-\sum\limits_{i} p_i\ln p_i
$$

where $$p_i$$ is the proportional abundance of a given species.


In order to compare the diversity of different islands, one can use **Sorensen's coefficient of similarity**. which is a good indicator of **beta-diversity**. It's given by-

$$
C_s = \frac{2a}{2a+b+c}\\
a = \text{Number of species common between site 1 and 2}\\
b = \text{Number of species unique to site 1}\\
c = \text{Number of species unique to site 2}\\
$$

Find the Sorensen's coefficient for all the combinations of the islands where species accumulation curve has attained saturation. 

[Here](./BirdData.zip) is the data collected by the students.

### Input

The excel sheets containing the data collated by the students.

### Output

1. Species Accumulation Curves for each island.
2. Shannon-Weiner Diversity index of each island where species accumulation curve has attained saturation.
3. Sorensen's coefficient between each island where species accumulation curve has attained saturation.


## Question 3[60 Marks]

It is well known that multiple codons in RNA can code for the same amino acid. And, given an RNA sequence, it's easy to find the corresponding amino acid chain. However, the reverse is not so trivial. Given an amino acid chain, there are multiple RNA sequences that code for it.

You are applying for an internship in computational biology. Your prospective PI wants to gauge your algorithmic and computational skills. So, he has asked you to find all the RNA sequences that can code for a given amino acid sequence.

You can use the following amino acid sequence(hypothetical) for testing your code-
`His-Gln-Tyr-Phe-Lys`

This would be helpful-

![CodonAcidMap](./CodonRnaMap.jpeg)

**Note:** Ignore start and stop codons.


### Input

Amino acid sequence

### Output

All possible RNA sequences that code for the given amino acid sequence.


## Question 4[100 Marks]

Fascinated by [Conway's Game of life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life), a mathematical biologist, who believes that **"Life is a difficult proposition"** has decided to make life more complicated. Here are the rules of his game-

Each cell in an $$2N\times 2N$$ grid is in one of the 2 possible states, live(1) or dead(0). Each cell interacts with it's 8 neighbours and it's own state after the interaction is given by a rule which is different in different parts of the grid. He divides the grid into 4 parts and follows the rules given below-

* Upper Left Half &rarr; $$E_{final}=\left\{
	\begin{array}{ll}
		0 & \mbox{if } \text{all eight neighbors are 1} \\
		1 & \mbox{if all eight neighbors are 0} \\
        A.B.C + D.E.F + G.H.I + B.C & \mbox{otherwise}
	\end{array}
\right.$$

* Upper Right Half &rarr; $$E_{final}=\left\{
	\begin{array}{ll}
		0 & \mbox{if } \text{all eight neighbors are 1} \\
		1 & \mbox{if all eight neighbors are 0} \\
        A.B.C + D.E.F + G.H.I + E.F & \mbox{otherwise}
	\end{array}
\right.$$

* Lower Left Half &rarr; $$E_{final}=\left\{
	\begin{array}{ll}
		0 & \mbox{if } \text{all eight neighbors are 1} \\
		1 & \mbox{if all eight neighbors are 0} \\
        A.B.C + D.E.F + G.H.I + H.I & \mbox{otherwise}
	\end{array}
\right.$$

* Lower Right Half &rarr; $$E_{final}=\left\{
	\begin{array}{ll}
		0 & \mbox{if } \text{all eight neighbors are 1} \\
		1 & \mbox{if all eight neighbors are 0} \\
        A.B.C + D.E.F + G.H.I + A.C & \mbox{otherwise}
	\end{array}
\right.$$

Here, the operations involved are binary addition and multiplication and the labels A to I have been given as per the following scheme-

![Scheme](./grid.png)

Further, in an "iteration", the number of cells interacting with their neighbors is a radom integer between $$2N$$ and $$N^2$$. These are picked randomly and every interaction can potentially change the grid for the next interaction within the same iteration. Assume that the boundaries are periodic. Your job is to apply these rules on [this](./darwin.png) image for 420 iterations.

### Input

A given image.

### Output

An image showing the final state after 420 iterations.


## Question 5[100 Marks]

A new species of bacteria named "Isingotetragonous" has been discovered recently. The bacteria live in colonies that are roughly square in shape. An individual bacteria doesn't survive for long if it's separated from its colony. Each bacteria has a structure called "Spink Filament" on it's surface that comes in 2 shapes. The bacteria can change the shape of "Spink Filament" from one form to the other. Depending on the shape of the "Spink Filament" on the bacteria in it's immediate vicinity(the 8 bacteria around it) and the bacteria next to them(the 16 bacteria surrounding these 8 bacteria), the bacteria secretes a chemical called "Hamiltonine" responsible for strengthening the integrity of the colony. However, the strength of the colony is also temperature dependent and too much of "Hamiltonine" at a low temperature can cause disintegration of the colony. So, as the temperature changes, the bacteria change the structure of the "Spink Filament" in such a manner that the concentration of "Hamiltonine" is optimum for maintaining the structural integrity of the colony. However, the process of changing the structure of the "Spink Filament" is not perfect, hence the concentration of "Hamiltonine" is not definite at a given temperature. There are small fluctuations. 

Dr. Jay Joseph has proposed the following mathematical model for this-

For a colony of $$N\times N$$ bacteria,

$$\text{Concentration of Hamiltonine}(H)=\sum\limits_{i=1}^{N\times N}\left(-J\sum\limits_{j=1}^{8}\sigma_i\sigma_j -K \sum\limits_{k=1}^{16}\sigma_i\sigma_k \right)$$

where $$\sigma_l = \pm 1$$ represents the 2 shapes of the filament. You need to deal with the summation at the edges in the following manner: During the loop over the bacteria cells, let each bacteria interact with every cell near it and the cells next to the neighboring cell.

$$\text{Probability of having H amount of Hamiltonine at a given temperature T}(P(H, T))\propto e^{-\frac{H}{kT}}$$

Here, `J`, `K` and `k` are constants whose value has been proposed by Dr. Anand. Your job as an intern in his lab is to calculate the average value of "Hamiltonine" for the given probability distribution and generate a few probable configurations for the bacterial colony on the basis of the shape of filaments. 


Since the probability distribution is Boltzmannian, we can use the following algorithm to simulate it-
* Take a random $$N\times N$$ matrix consisting of -1 and +1. Take this as your initial configuration.
* Generate a new configuration $$\nu'$$ by changing the shape of a few "Spink filaments" in the matrix. This change of configurations would cause a change in the concentration of "Hamiltonine". 

$$\Delta H_{\nu\nu'}=H_{\nu'}-H_{\nu}$$

* If $$\Delta H_{\nu\nu'}$$ is negative or zero, accept this change of configurations. Else, draw a random number u between 0 and 1. If $$\Delta H_{\nu\nu'}\geq u$$, accept the change, else reject it. In simpler terms-

$$
\nu(t) = \nu,\\
\nu(t+1) = \nu' \text{ when } \Delta H_{\nu\nu'}\leq 0,\\
\nu(t+1) =
\left\{
	\begin{array}{ll}
		\nu'  & \mbox{if } e^{-\frac{\Delta H_{\nu\nu'}}{kT}} \geq u \\
		\nu & \mbox{if } e^{-\frac{\Delta H_{\nu\nu'}}{kT}} < u
	\end{array}
\right.
$$

* Repeat this process for a few thousands steps. This will cause the configuration to settle down around a more probable value. Remember that initially, we started in some random configuration which may not be very probable at a given temperature.
* Now, continue this process for a few thousand steps more, but this time take the average of concentration at, say every 100 steps. Make sure that more than 40% percent of the configurations are being accepted.
* This average is the average value of the concentration. You can display the configuration at the end of the simulation as a probable configuration. Use black and white colors to represent +1 and -1 in the matrix.

Note that the configuration you attain at the end is not the most probably configuration, but a highly likely one.

You can use these values for testing your code-
`N=500`
`J=2 units`
`K=0.5 units`
`T=3 units`
`k=1 units`

### Input

`N`, `J`, `K`, `T` and `k`

### Output

1. Average concentration of Hamiltonine.
2. The configuration at the end of the simulations represented by an image.


## Question 6[120 Marks]

Remember those 50 students who birded **diligently and honestly** at the newly discovered islands. 30 of them caught the same disease(unnamed as of now) during their stay at the islands. A team of experts at the Pacific Institute has determined the cause of the disease to be bites from a new species of mosquitos found only on these islands. Some of these students were still infected when they returned to the campus and have now caused an outbreak in the city. It has been discovered that `Anopheles stephensi`(Malaria Vector) is the vector of this newly discovered disease too. Dr. Parul Ghara has proposed the following model has been proposed to model the spread of this disease-

Human population is an `nXn` grid with each cell having `h` humans(hosts) some Anopheles Stephensi mosquitoes(vector). Assume that the number of infected humans in each cell is drawn from a uniform distribution between `0` and `h` and the number of mosquitoes in each cell is drawn from a uniform distribution between `0` and `m`. All vectors are initially uninfected. The host and the vector grids are updated in the following manner:

* The probability of a mosquito biting a human in a grid cell is `α`. We assume that the mosquito is not able to travel much in its lifetime so it cannot infect hosts outside its grid cell.
* The probability of a human getting infected is `β` and the chance of other mosquitoes getting infected is `γ`.
* Human death and birth rate per capita is `δ` and the mosquito death and birth rate per capita is `η`.
* To simulate the micromovement in humans we assume that `θ%` of humans in the neighbouring cells interact with the mosquito in a cell.
* The probability of a human recovering is `λ`.

Each timestep is 1 day. Your job is to simulate this like a discrete time model and make 2 gifs, one of the host and the other of the vector grid for 150 timesteps.

For testing the code, use these values-
`n=300`
`h=500`
`m=1000`
`α=0.35`
`β=0.4`
`γ=0.75`
`δ=0.000039`
`η=0.4`
`θ=10`
`λ=0.07`


### Input

`n`, `h`, `m`, `α`, `β`, `γ`, `δ`, `η`, `θ`, `λ`

### Output

A gif showing the evolution for 150 steps.


# Done!

- Rename all your files as `Qx.ext`
- Put them into a zip/tar file with name `DWH-<teamname>.zip`/`DWH-<teamname>.tar`
- Mail them to `turingclub@iisermohali.ac.in`

# Enjoy!

Good Luck!

# Want a look at the earlier hackathons. Here they are-

- [DWH 2020](2020)
- [DWH 2021](2021)

{% include mathjax.html %}
