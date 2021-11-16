# Formula

## Bellman equations

$$
V(s) = \max_{a \in A(s)}\sum_{s' \in S}P_{a}(s'|s)[r(s,a,s') + \gamma V(s')]
$$

## UCT

$$
\pi (s) := \arg\max_{a \in A(s)} Q(s, a) + 2C_{p}\sqrt{\frac{2lnN(s)}{N(s, a)} }
$$

## TD

$$
Q(s, a) = Q(s, a) + \alpha [r + \gamma V(s', a') - Q(s, a)]
$$

### Q-learning

$$
Q(s, a) = Q(s, a) + \alpha [r + \gamma max_{a'}Q(s', a') - Q(s, a)]
$$

### SARSA

$$
Q(s, a) = Q(s, a) + \alpha [r + \gamma Q(s', a') - Q(s, a)]
$$

## Reward shaping

$$
Q(s, a) = Q(s, a) + \alpha [r + F(s, s') + \gamma V(s', a') - Q(s, a)]\\
F(s, s') = \gamma \Phi(s') - \Phi(s)
$$

For Grid world, potential function:
$$
\Phi(s) = \frac{1}{|x(g) - x(s)| + |y(g) + y(s)|}
$$

## N-step TD

$$
G_{\tau}^{n} = \sum_{i = \tau + 1}^{min(\tau + n, T)}\gamma ^{i - \tau - 1}r_{i}
\\
\textit{If } \tau + n < T \textit{ then } G_{\tau}^{n} = G_{\tau}^{n} + \gamma^{n}Q(S_{\Tau + n}, A_{\tau + n})
\\
Q(S_{\Tau}, A_{\tau}) = Q(S_{\tau}, A_{\tau}) + \alpha [G_{\tau}^{n} - Q(S_{\Tau}, A_{\tau})]
$$

## Approximate Q-function Representation

For Q-learning:
$$
w^{a}_{i} = w^{a}_{i} + \alpha[r + \gamma max'_{a}Q(s', a') - Q(s, a)]f_{i}(s, a)
$$

For SARSA: 
$$
w^{a}_{i} = w^{a}_{i} + \alpha[r + \gamma Q(s', a') - Q(s, a)]f_{i}(s, a)
$$