\clearpage 
# Distributions 

## Discrete Distrbutions {#app:DiscreteDistributions}

  **Bernoulli**             $Ber(p)$
  ------------------------- --------------------------------------
  Parameters:               $0 < p < 1$, probability of success
  PMF:                      $P[X=1] = p, \; P[X=0] = 1-p$
  Inverse CDF:              $F^{-1}(u) = \text{if}\  (u < p), 1 \ \text{else} \ 0$
  Expected Value:           $E[X] = p$
  Variance:                 $Var[X] = p(1-p)$
  Arena Generation:         DISC(p,1,1.0,0`[,Stream]`)
  Spreadsheet Generation:   = IF(RAND()$<$ p, 1, 0)
  Modeling:                 the number of successes in one trial

  **Binomial**              $Binom(n,p)$
  ------------------------- --------------------------------------------------------------
  Parameters:               $0 < p < 1$, probability of success, $n$, number of trials
  PMF:                      $P[X=x] = \binom{n}{x}p^{x}(1-p)^{n-x} \quad x=0,1,\ldots,n$
  Inverse CDF:              no closed form available
  Expected Value:           $E[X] = np$
  Variance:                 $Var[X] = np(1-p)$
  Arena Generation:         not available, use convolution of Bernoulli
  Spreadsheet Generation:   = BINOM.INV(n,p,RAND())
  Modeling:                 the number of successes in $n$ trials

  **Shifted Geometric**     Shifted Geo($p$)
  ------------------------- ----------------------------------------------
  Parameters:               $0 < p < 1$, probability of success
  PMF:                      $P[X=x] = p(1-p)^{x-1} \quad x=1,2,\ldots,$
  Inverse CDF               $F^{-1}(u) = 1 + \left\lfloor \frac{ln(1 - u)}{ln(1 - p)} \right\rfloor$
  Expected Value:           $E[X] = 1/p$
  Variance:                 $Var[X] = (1-p)/p^2$
  Arena Generation:         1 + AINT(LN(1-UNIF(0,1))/LN(1-p))
  Spreadsheet Generation:   = $\text{1 + INT(LN(1-RAND())/LN(1-p))}$
  Modeling:                 the number of trials until the first success

  **Negative Binomial Defn. 1**   NB1($r,p$)
  ------------------------------- ------------------------------------------------------------------
  Parameters:                     $0 < p < 1$, probability of success, $r^{th}$ success
  PMF:                            $P[X=x] = \binom{x-1}{r-1}p^{r}(1-p)^{x-r} \quad x=r,r+1\ldots,$
  Inverse CDF:                    no closed form available
  Expected Value:                 $E[X] = r/p$
  Variance:                       $Var[X] = r(1-p)/p^2$
  Arena Generation:               use convolution of shifted geometric
  Spreadsheet Generation:         use convolution of shifted geometric
  Modeling:                       the number of trials until the $r^{th}$ success

  **Negative Binomial Defn. 2**   NB2($r,p$)
  ------------------------------- ----------------------------------------------------------------
  Parameters:                     $0 < p < 1$, probability of success, $r^{th}$ success
  PMF:                            $P[Y=y] = \binom{y+r-1}{r-1}p^{r}(1-p)^{y} \quad y=0,1,\ldots$
  Inverse CDF:                    no closed form available
  Expected Value:                 $E[Y] = r(1-p)/p$
  Variance:                       $Var[Y] = r(1-p)/p^2$
  Arena Generation:               use convolution of geometric
  Spreadsheet Generation:         use convolution of geometric
  Modeling:                       the number of failures prior to the $r^{th}$ success

  **Poisson**               Pois($\lambda$)
  ------------------------- ----------------------------------------------------------------------
  Parameters:               $\lambda > 0$
  PMF:                      $P[X=x] = \frac{e^{-\lambda}\lambda^{x}}{x!} \quad x = 0, 1, \ldots$
  Inverse CDF:              no closed form available
  Expected Value:           $E[X] = \lambda$
  Variance:                 $Var[X] = \lambda$
  Arena Generation:         POIS($\lambda$`[,Stream]`)
  Spreadsheet Generation:   not available, approximate with lookup table approach
  Modeling:                 the number of occurrences during a period of time

\newpage

  **Discrete Uniform**      DU($a, b$)
  ------------------------- --------------------------------------------------------
  Parameters:               $a \leq b$
  PMF:                      $P[X=x] = \frac{1}{b-a+1} \quad x = a, a+1, \ldots, b$
  Inverse CDF:              $F^{-1}(u) = a + \lfloor(b-a+1)u\rfloor$
  Expected Value:           $E[X] = (b+a)/2$
  Variance:                 $Var[X] = \left( \left( b-a+1\right)^2 -1 \right)/12$
  Arena Generation:         a + AINT((b-a+1)\*UNIF(0,1))
  Spreadsheet Generation:   =RANDBETWEEN(a,b)
  Modeling:                 equal occurrence over a range of integers

## Continuous Distrbutions {#app:ContinuousDistributions}

  **Uniform**               $U(a,b)$
  ------------------------- ----------------------------------------------------------
  Parameters:               a = minimum, b = maximum, $-\infty < a < b < \infty$
  PDF:                      $f(x) = \frac{1}{b-a}$ for $a \leq x \leq b$
  CDF:                      $F(x) = \frac{x-a}{b-a} \; \text{if} \; a \leq x \leq b$
  Inverse CDF:              $F^{-1}(p) = a + p(b-a) \; \; \text{if} \; 0 < p < 1$
  Expected Value:           $E[X]=\frac{a+b}{2}$
  Variance:                 $V[X] = \frac{(b-a)^2}{12}$
  Arena Generation:         UNIF(a,b`[,Stream]`)
  Spreadsheet Generation:   = a + RAND()\*(b-a)
  Modeling:                 assumes equally likely across the range,
                            when you have lack of data, task times

  **Normal**                $N(\mu,\sigma^2)$
  ------------------------- -------------------------------------------------------------
  Parameters:               $-\infty < \mu < +\infty$ (mean), $\sigma^2 > 0$ (variance)
  CDF:                      No closed form
  Inverse CDF:              No closed form
  Expected Value:           $E[X] = \mu$
  Variance:                 $Var[X] = \sigma^2$
  Arena Generation:         NORM($\mu,\sigma^2$`[,Stream]`)
  Spreadsheet Generation:   = NORM.INV(RAND(), $\mu$, $\sigma$)
  Modeling:                 task times, errors

\newpage

  **Exponential**           EXPO($1/\lambda$)
  ------------------------- -------------------------------------------------------------------------------
  Parameters:               $\lambda > 0$
  PDF:                      $f(x) = \lambda e^{-\lambda x} \; \text{if} \; x \geq 0$
  CDF:                      $F(x) =     1 - e^{-\lambda x} \; \text{if} \; x \geq 0$
  Inverse CDF:              $F^{-1}(p) = (-1/\lambda)\ln \left(1-p \right)  \; \; \text{if} \; 0 < p < 1$
  Expected Value:           $E[X] = \theta = 1/\lambda$
  Variance:                 $Var[X] = 1/\lambda^2$
  Arena Generation:         EXPO($\theta$`[,Stream]`)
  Spreadsheet Generation:   = $(-1/\lambda)$LN(1-RAND())
  Modeling:                 time between arrivals, time to failure
                            highly variable task time

  **Weibull**               WEIB($\beta$, $\alpha$)
  ------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Parameters:               $\beta > 0$ (scale), $\alpha > 0$ (shape)
  CDF:                      $F(x) = 1- e^{-(x/\beta)^\alpha} \; \text{if} \; x \geq 0$
  Inverse CDF:              $F^{-1}(p) = \beta\left[ -\ln (1-p)\right]^{1/\alpha}  \; \; \text{if} \; 0 < p < 1$
  Expected Value:           $E[X] = \left(\dfrac{\beta}{\alpha}\right)\Gamma\left(\dfrac{1}{\alpha}\right)$
  Variance:                 $Var[X] = \left(\dfrac{\beta^2}{\alpha}\right)\biggl\lbrace 2\Gamma\left(\dfrac{2}{\alpha}\right) - \left(\dfrac{1}{\alpha}\right)\biggl(\Gamma\left(\dfrac{1}{\alpha}\right)\biggr)^2\biggr\rbrace$
  Arena Generation:         WEIB(scale, shape`[,Stream]`)
  Spreadsheet Generation:   = $(\beta)(-\text{LN}(1-\text{RAND}())\wedge(1/\alpha)$
  Modeling:                 task times, time to failure

  **Erlang**                Erlang($r$,$\beta$)
  ------------------------- --------------------------------------------------------------------------------------------------
  Parameters:               $r > 0$, integer, $\beta > 0$ (scale)
  CDF:                      $F(x) = 1- e^{(-x/\beta)}\sum\limits_{j=0}^{r-1}\dfrac{(x/\beta)^j}{j} \; \text{if} \; x \geq 0$
  Inverse CDF:              No closed form
  Expected Value:           $E[X] = r\beta$
  Variance:                 $Var[X] = r\beta^2$
  Arena Generation:         ERLA($E[X], r$`[,Stream]`)
  Spreadsheet Generation:   = GAMMA.INV(RAND(), $r$, $\beta$)
  Modeling:                 task times, lead time, time to failure,

  **Gamma**                 Gamma($\alpha$,$\beta$)
  ------------------------- ------------------------------------------
  Parameters:               $\alpha > 0$, shape, $\beta > 0$ (scale)
  CDF:                      No closed form
  Inverse CDF:              No closed form
  Expected Value:           $E[X] = \alpha \beta$
  Variance:                 $Var[X] = \alpha \beta^2$
  Arena Generation:         GAMM(scale, shape`[,Stream]`)
  Spreadsheet Generation:   = GAMMA.INV(RAND(), $\alpha$, $\beta$)
  Modeling:                 task times, lead time, time to failure,

  **Beta**                  BETA($\alpha_1$,$\alpha_2$)
  ------------------------- -------------------------------------------------------------------------------------
  Parameters:               shape parameters $\alpha_1 >0$, $\alpha_2 >0$
  CDF:                      No closed form
  Inverse CDF:              No closed form
  Expected Value:           $E[X] = \dfrac{\alpha_1}{\alpha_1 + \alpha_2}$
  Variance:                 $Var[X] = \dfrac{\alpha_1\alpha_2}{(\alpha_1 + \alpha_2)^2(\alpha_1 + \alpha_2+1)}$
  Arena Generation:         BETA($\alpha_1$,$\alpha_2$`[,Stream]`)
  Spreadsheet Generation:   BETA.INV(RAND(), $\alpha_1$, $\alpha_2$)
  Modeling:                 activity time when data is limited, probabilities

  **Lognormal**             LOGN$\left(\mu_l,\sigma_l\right)$
  ------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------
  Parameters:               $\mu = \ln\left(\mu_{l}^{2}/\sqrt{\sigma_{l}^{2} + \mu_{l}^{2}}\right) \quad \sigma^{2} = \ln\left((\sigma_{l}^{2}/\mu_{l}^{2}) + 1\right)$
  CDF:                      No closed form
  Inverse CDF:              No closed form
  Expected Value:           $E[X] = \mu_l = e^{\mu + \sigma^{2}/2}$
  Variance:                 $Var[X] = \sigma_{l}^{2}  = e^{2\mu + \sigma^{2}}\left(e^{\sigma^{2}} - 1\right)$
  Arena Generation:         LOGN($\mu_l,\sigma_l$`[,Stream]`)
  Spreadsheet Generation:   LOGNORM.INV(RAND(), $\mu$, $\sigma$)
  Modeling:                 task times, time to failure

  **Triangular**            TRIA(a, m, b)
  ------------------------- -----------------------------------------------------------------------------------
  Parameters:               a = minimum, m = mode, b = maximum
  CDF:                      $F(x) =  \dfrac{(x - a)^2}{(b - a)(m - a)} \; \text{for} \; a \leq x \leq m$
                            $F(x) = 1 - \dfrac{(b - x)^2}{(b - a)(b - m)} \; \text{for} \;m < x \leq b$
  Inverse CDF:              $F^{-1}(u) = a + \sqrt{(b-a)(m-a)u} \; \text{for} \;  0 < u < \dfrac{m-a}{b-a}$
                            $F^{-1}(u) = b - \sqrt{(b-a)(b-m)(1-u)} \; \text{for} \; \dfrac{m-a}{b-a} \leq u$
  Expected Value:           $E[X] = (a+m+b)/3$
  Variance:                 $Var[X] = \dfrac{a^2 + b^2 + m^2 -ab -am -bm}{18}$
  Arena Generation:         TRIA(min, mode, max`[,Stream]`)
  Spreadsheet Generation:   implement $F^{-1}(u)$ as VBA function
  Modeling:                 task times, activity time when data is limited





