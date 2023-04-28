# Understanding quantum information and computation
[toc]

## 1. Lesson 1 - Single System

1. classical information
   1. Information $X$ from a finite set of numbers $\sum$, which can be described with probability such as $P(X=0)=\frac{1}{4}$, $P(X=1)=\frac{3}{4}$
   1. state vector
      1. Description form(state vector(simple) vs. density matrix(general))
      2. Description Bridge between classical information and quantum information is using **column vector** $(\frac{1}{4}, \frac{3}{4})^T=\frac{1}{4}|0\rangle+\frac{3}{4}|1\rangle$
      3. there exists a Matrix-verctor-multiplication $M$ such that $M|a\rangle=|f(a)\rangle$ where $f:\sum \rightarrow \sum$ and $a\in \sum$.
      4. **Column vector**  $|0\rangle=(1,0)^T, |1\rangle=(0,1)^T$
      5. **Row vector** $\langle0|=(1,0), \langle1|=(0,1)$
      6. **Relationship** of Row vector * column vector = scalar ($|a\rangle \langle b|=1$, if $a==b$); column vector * row vector = M. has 1 in the (a,b)-entry, otherwise 0. e.g. state $|0\rangle \langle1|=\begin{array}{cc} &
                  \begin{array}{cc} 0 & 1\end{array}
                  \\
                  \begin{array}{cc}
                  0 \\
                  1 \end{array}
                  &
                  \left(
                  \begin{array}{cc}
                  0 & 1\\
                  0 & 0 \\
                  \end{array}
                  \right)\end{array}$.
   2. operations
      1. **Deterministic operation**: Matrix contains only one 1 for each column and 0 for others entries.
      2. **Probabilistic operation**: described by stochastic matrix(1.nonnegative number if matrix,2. column sum is 1. e.g.(case study state 0 comes then nothing, if state 1 comes probibility 1/2 0 or 1/2 1)(that means the first column of matrix is $(1, 0)^T$, the second column is $(\frac{1}{2}, \frac{1}{2})^T$) Column indicates the input state, the rows describe the output probability for each output.
      3. **Relationship** between deterministic operation and probabilistic operation: probabilistic operation can be descrbied by deterministic operation with scalar()
2. quantum information
   1. state vector
      1. column vector (complex number for entries, sum of absolute value squared of entries is 1)
      2. amplitudes (the complex number in entries are often called amplitudes, work like probabilities but they aren't probabilities)
   2. standard basis measurements
      1. outcomes are classical states
      2. probability are absolute value squared entries of quantum state vector.
   3. unitary operations
      1. $U^\dagger U = U U^\dagger = 1$, $\sigma_x,\sigma_y,\sigma_z$
      2. Phase Operation $\begin{pmatrix}
                           1 & 0\\
                           0 & e^{i\theta}
                        \end{pmatrix}$,  S $(\theta=\frac{\pi}{2})$, T $(\theta=\frac{\pi}{4})$
      3. Input $|0\rangle$ output the first column as state vector, input $|1\rangle$ output the second column as state vector.

## 2. Lesson 2 - Multiple System(system compound)

1. classical states
   1. n tuple $(a_1,..,a_n) \in \sum_1 \times...\times \sum_n$
   2. Probabilistic states (X, Y), assume X and Y are INDEPENDENT then P(X,Y)=P(X)P(Y)
   3. **Operation**
      1. Tensor product describes operations in compound system, it is bilinear
      2. $|\pi\rangle=|\Phi\rangle\otimes|\Psi\rangle=\sum_{(a,b)\in\Sigma\times\Gamma}\alpha_a\beta_b|a\rangle|b\rangle$ then $\langle a b|\pi\rangle=\langle a |\Phi\rangle \langle b |\Psi\rangle$ 
      3. **Tensor products of matries** $M=\sum_{a,b\in\Sigma}\alpha_{ab}|a\rangle\langle b|$, $N=\sum_{c,d\in\Gamma}\beta_{cd}|c\rangle\langle d|$, **then** $M\otimes N=\sum_{a,b} \sum_{c,d} \alpha_{ab}\beta_{cd}|ac\rangle\langle bd|$
   4. Measurement of probabilistic state
      1. (X,Y), what happens when measure X and do nothing to Y?
      2. $P(X=a) = \sum_b P((X,Y)=(a,b))$ and $P(Y=b)=\frac{P((X,Y)=(a,b))}{P(X=a)}$
      3. Assume arbitary state $(X,Y)= \sum_{(a,b)\in\Sigma\times\Gamma}p_{ab}|ab\rangle=\sum_a |a\rangle \otimes \sum_b p_{ab}|b\rangle$, take one a out then $P(X=a)=\sum_b p_{ab}$ and condition on "a" **then** probabilistic state of Y is $\frac{\sum_b p_{ab}|b\rangle}{\sum_c p_{ac}}$
2. Quantum states
   1. Measurement For (X,Y), $P(X=a)=\sum_b|\langle ab| \Psi\rangle|^2=\sum_b|\alpha_{ab}|^2$, and condition on a then Y is $|a\rangle \otimes \frac{\sum_b\alpha_{ab} |b\rangle}{\sum_b|\alpha_{ab}|^2}$
   2. Unitary operation
      1. SWAP
      2. Controll-U on Y **then** $|0\rangle\langle0| \otimes 1_Y +|1\rangle\langle 1|\otimes U = \begin{pmatrix}
                                       1_Y & 0 \\
                                       0 & U
                                    \end{pmatrix}$
         if the second qubit is controll, $1_Y \otimes|0\rangle\langle0| + U \otimes|1\rangle\langle 1|$
      3. Controll-Controll-Gate(Toffoli gate)
         1. Controll-U on Y **then** $|0\rangle\langle0| \otimes 1_Y \otimes 1_Y +|1\rangle\langle 1|\otimes (|0\rangle\langle0| \otimes 1_Y +|1\rangle\langle 1|\otimes U)$