# Use this for the ideas before adding to the actual page

# For Homepage: 

Main Idea: We collaborate to calibrate emerging or even non-existing models in both developed and developing market. 

Target client: Institutions or individuals seeking a calibrated model that they can put into production with minimum effort.

Target contributor: Anyone can contribute. No matter you are a college student who have a passion to learn about quantitative modeling or you are a professional researcher who have suceeded in developing models. We have a pool of models waiting for your calibration and perfection. More importantly, we will make your contributions seen and make your voice heard. Most importantly, we have a incentive program ......

# For the first project -- Fixed Income -- Rate Modeling: 

Need to update derivation and code

# For the second project -- Mortgage Tokenizaiton: 




Swap Rate

$$
\begin{tikzpicture}
  \draw [|-|] [thick] (0,0) node[below] {$t$} -- (2,0) node[below] {$t+1$}
  -- (2,0) -- (4,0)   node[below] {$t+2$}
  -- (4,0) -- (10,0) node[midway, below] {$\ldots$} node[below] {$t+n$};
  \coordinate[label=center:$\text{Pay fix rate S(t, t+n)}$] (A) at (1.5,0.5);
  \coordinate[label=left:$\text{Receive float rate L(t+i-1, t+i)}$] (A) at (4.5,-0.75);
\end{tikzpicture}
$$
