---
author: Shannon, E. C.
title: A Mathematical Theory of Communication
journal: The Bell System Technical Journal
year: "1948"
volume: XXVII/3
pages: 379–423
language: English
---
# Introduction
**Communication** = reproducing at one point either exactly or approximately a message selected at another point. Messages have **meaning** (refer to or are correlated according to some system with physical or conceptual entities), but this is irrelevant to the engineering problem. Messages are **selected from a set** of possible messages.
**Measure of information:** *N* (number of possible messages), or *f*(*N*) where *f* is monotonous. Typically *f* = `log`, because
1) *practical:* parameters in engineering tend to vary linearly with the log of possibilities (time, bandwidth, number of relays etc.),
2) *intuitive:* 2 punched cards = twice as much information = square of the possibilities of one,
3) *mathematically more suitable:* working with `log` is easy. ==Binary digit = "bit" (J. W. Tukey)== A decimal digit ≈ 3⅓ bit ($=\log_{10} M / \log_{10} 2$).
**Communication system** = a system of five parts:
1. *information source* – produces the message,
2. *transmitter* – creates a signal from the message,
3. *channel* – the medium of transmission,
4. *receiver* – reconstructs the message from the signal,
5. *destination* – the receiver (person or machine) of the message.
Classification of communication systems:
- *discrete* – both message and signal are a sequence of discrete symbols (e. g. telegraphy),
- *continuous* – both message and signal are treated as continuous functions (e. g. radio, tv),
- *mixed* – both discrete and continuous variables are involved (e. g. PCM transmission of speech).
# Part I: Discrete Noiseless Systems
## 1. The Discrete Noiseless Channel
A sequence of elementary symbols $S_1 \cdots S_n$ can be transmitted. Telegraphy: `{ "·", "–", letter-space, word-space }` (technically: `^v`, `^^^v`, `vvv`, `vvvvvv` – durations: 2, 4, 3, 6 units of time).
How to measure the capacity of the channel?
Teletype: 32 symbols, each has the same duration → channel capacity = *n* symbol/sec = 5*n* bit/sec (maximum transmit rate).
###### Definition:
$$
C = \lim_{T \to \infty}  \frac{\log{N(T)}}T
$$
where $N(T)$ is the number of allowed signals of duration *T*.
The total number $N(T)$ is equal to the sum of the numbers of sequences ending in $S_1, \ldots, S_n$:
$$
C = \log {X_0},
$$
where $X_0$ is the largest real solution of the characteristic equation $X^{-t_1} + \cdots + X^{-t_n} = 1$.
A general type of **restriction of the sequences:** the machine has a number of possible states $a_1, \ldots, a_m$, each state allowing a subset of $S_1 \cdots S_n$ to be transmitted. When one of these is transmitted, the state changes according to the state and the symbol. It can be proved that for such restrictions $C$ will exist and can be calculated:
###### Theorem 1:
Let $b^{\langle s \rangle}_{i j}$ be the duration of the *s*<sup>th</sup> symbol which is allowable in $a_i$ and leads to $a_j$. Then $C = \log W$ where $W$ is the largest real root of the determinant equation:
$$
\DeclarePairedDelimiter\abs{\lvert}{\rvert}
	\abs[\Big]{\sum_s W^{-b^{\langle s \rangle}_{i j}} - \delta_{i j}} = 0
$$
where $\delta_{i j} = 1$ if $i = j$ and is zero otherwise.
## 2. The Discrete Source of Information
Statistical knowledge of the source can reduce the required capacity of the channel. E. g. telegraphy: the shortest symbol stands for the most frequent letter (E) etc. The successive symbols are chosen according to certain probabilities depending on preceding choices and the particular symbols in question. A **discrete source** can be considered a **stochastic process.**
Examples:
1. Natural languages.
2. Quantized signals (PCM, television).
3. Mathematically defined abstract stochastic processes (letter distribution, digram/trigram distribution, word distribution – artificial languages).
## 3. The Series of Approximations to English
1. Zero-order approximation: 26 letters + space with equi-probable.
2. First-order appr.: symbols imitate the frequency of letters in English text.
3. Second-order appr.: symbols follow the digram structure of English.
4. Third-order appr.: same, with trigram distribution.
5. First-order word approximation: using an English dictionary with word frequencies.
6. Second-order word appr.: the word transition probabilities follow English.
A sufficiently complex stochastic process will give a satisfactory representation of a discrete source.
## 4. Graphical Representation of a Markoff Process
These stochastic processes are **discrete Markoff process:** states $S_1, \cdots, S_n$ have an $n × n$ transition probability matrix where $p_i(j)$ is the probability that the system goes from state $S_i$ to $S_j$. The letters are labels of the transitions. In case of trigrams the shape of the transition matrix is $n×n^2$.
## 5. Ergodic and Mixed Sources
Ergodic: in an ergodic process every sequence produced by the process is the same in statistical properties. (All of the above artificial languages are ergodic.) Roughly: statistical homogeneity. The criteria of an ergodic process are:
1. The graph does not consist of isolated parts $A$ and $B$ such that it is impossible to go from one to another and vice versa, along the direction of arrows.
2. The greatest common divisor of the lengths of circuits is 1 (they are relative primes).
If the second condition is violated, by a shift of $0 .. d-1$ any sequence can be made statistically equivalent to any other. We are not interested in these cases.
If the first condition is violated, the graph can be separated into a set of subgraphs each of which satisfies the first condition. This corresponds to a case when there are several different sources $L_1, L_2, L_3, \cdots$ which are each ergodic, and the components have probabilities of $p_1, p_2, \cdots$ to be chosen, after which the sequence is generated from that component.
If $P_i$ is the probability of state $i$ and $p_i(j)$ the transition probability to state $j$, then for the process to be stationary the $P_i$ must satisfy equilibrium conditions:
$$
P_j = \sum_i P_ip_i(j)
$$
In the ergodic case with any starting conditions the probabilities $P_j(N)$ of being in state $j$ after $N$ symbols approach the equilibrium values as $N \rightarrow \infty$.
## 6. Choice, Uncertainty and Entropy
Knowing the probabilities $p_1, \cdots, p_n$ of a set of events, can we find a measure of how much "choice" is involved in the selection of the event of how uncertain we are of the outcome?
Let $H(p_1, \cdots, p_n)$ be a measure.
1. It should be continuous in the $p_i$.
2. If $p_i = \frac{1}{n}$ for $\forall n \in \{1 .. n\}$, then $H$ should be a monotonic increasing function of $n$ (with equally likely events there is more choice of uncertainty when there are more possible events).
3. If a choice be broken down into successive choices, $H$ should be the weighted sum of the individual values of its successors.
###### Theorem 2:
The only $H$ satisfying the three above assumptions is of the form:
$$
H = -K\sum_{i=1}^np_i\log p_i
$$
where $K$ is a positive constant.
Quantities of the form **$H = -\sum p_i \log p_i$** play a central role in information theory as measures of information, choice and uncertainty. $H$ is called **entropy.**
