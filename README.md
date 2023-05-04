Download Link: https://assignmentchef.com/product/solved-csc336s-assignment-3
<br>
Please write your family and given names and <strong>underline </strong>your family name on the front page of your paper.

All questions <strong>must </strong>be written in latex, and compiled to a single pdf. Plots (7 for Q1 and 2 for Q3) must in embedded in latex. All code and output of Q1, Q3 and Q4 should be <em>embedded </em>into latex. Code and output should be embedded with fixed-width fonts, e.g. Courier. Font size of all fonts must be 12. Linespacing set to 1.1.

What to submit:

<ul>

 <li>The single pdf file 00A3.pdf (with embedded code and output).</li>

 <li>The latex source file of A3.</li>

 <li>Any source code you wrote (for computation, plots, etc).</li>

 <li>Plot files (7 for Q1 and 2 for Q3) in eps and png format.</li>

</ul>

Thus, the code and plots will be available within latex/pdf, <em>as well as </em>separately.

<ol>

 <li>This question involves the study of the outbreak of an epidemic in a population and its eradication with vaccinations. The study of spreading of infectious diseases is mainly done by numerical Ordinary Differential Equations (ODEs), which are not the topic of CSC336 (but of CSC436). However, numerical ODE solvers, essentially convert a system of ODEs to a sequence of nonlinear systems. Each nonlinear system of the sequence relates unknown quantities at a time point (or step), in terms of known quantities at the previous time point, while the initial state is given (known). In this way, the values of various quantities at several time points are computed and studied.</li>

</ol>

Assume there is a population of <em>N </em>people, which remains constant over time. Assume that each person belongs to one of the five groups: susceptible, exposed (to become infected after incubation), infected/ious, recovered/immune and vaccinated/immune. The infected/ious persons transmit the virus at a given rate β to the susceptible and make them exposed, the exposed become infected/ious after a certain incubation period α<sup>−</sup><sup>1 </sup>(also given), the infected/ious recover at a given rate γ, and stay immune thereafter. Furthermore, the susceptible get vaccinated at a given rate ρ, and become immune immediately after vaccination and stay immune thereafter. The population of <em>N </em>persons is replenished at a given death and birth rate µ, and all newborns are susceptible.

In an instance of this problem, at each time point <em>i</em>, the following 5 × 5 nonlinear system needs to be solved:

<em><sup>x</sup></em><sub>1</sub>(<em>i</em>) = <em><sup>x</sup></em><sub>1</sub>(<em>i</em>−1) + <em>h</em>µ<em>N </em>− <em>h</em>µ<em><sup>x</sup></em><sub>1</sub>(<em>i</em>) − <em>h </em><sup>β </sup><em><sup>x</sup></em><sub>1</sub>(<em>i</em>) <em><sup>x</sup></em><sub>3</sub>(<em>i</em>) − <em>h</em>ρ<em><sup>x</sup></em><sub>1</sub>(<em>i</em>)                                                                                 (1a)

<em>N</em>

(<em>i</em>)         (<em>i</em>−1)                (<em>i</em>)               (<em>i</em>)              <sup>β </sup>(<em>i</em>)      (<em>i</em>)

<em>x</em><sub>2 </sub>= <em>x</em><sub>2 </sub>− <em>h</em>α <em>x</em><sub>2 </sub>− <em>h</em>µ<em>x</em><sub>2 </sub>+ <em>hx</em><sub>1 </sub><em>x</em><sub>3                                                                                                                 </sub>(1b)

<em>N</em>

<em><sup>x</sup></em><sub>3</sub>(<em>i</em>) = <em><sup>x</sup></em><sub>3</sub>(<em>i</em>−1) − <em>h</em>γ <em><sup>x</sup></em><sub>3</sub>(<em>i</em>) − <em>h</em>µ<em><sup>x</sup></em><sub>3</sub>(<em>i</em>) + <em>h</em>α <em><sup>x</sup></em><sub>2</sub>(<em>i</em>)  (1c) <em><sup>x</sup></em><sub>4</sub>(<em>i</em>) = <em><sup>x</sup></em><sub>4</sub>(<em>i</em>−1) + <em>h</em>γ <em><sup>x</sup></em><sub>3</sub>(<em>i</em>) − <em>h</em>µ<em><sup>x</sup></em><sub>4</sub>(<em>i</em>) (1d) <em><sup>x</sup></em><sub>5</sub>(<em>i</em>) = <em><sup>x</sup></em><sub>5</sub>(<em>i</em>−1) + <em>h</em>ρ<em><sup>x</sup></em><sub>1</sub>(<em>i</em>) − <em>h</em>µ<em><sup>x</sup></em><sub>5</sub>(<em>i</em>).             (1e)

In the above, <em>x</em><sup>(<em>i</em>) </sup>= [<em>x</em><sub>1</sub><sup>(<em>i</em>)</sup>, <em>x</em><sub>2</sub><sup>(<em>i</em>)</sup>, <em>x</em><sub>3</sub><sup>(<em>i</em>)</sup>, <em>x</em><sub>4</sub><sup>(<em>i</em>)</sup>, <em>x</em><sub>5</sub><sup>(<em>i</em>)</sup>]<em><sup>T </sup></em>represents the vector of numbers of susceptible, exposed, infected/ious, recovered/resistant/immune and vaccinated/immune persons, respectively, at time point <em>i</em>, and these are the five unknowns that need to be computed at the <em>i</em>th time point (step), assuming the quantities of the previous time point <em>i </em>− 1 are already computed, and the initial state, <em>x</em><sup>(0) </sup>= [<em>x</em><sub>1</sub><sup>(0)</sup>, <em>x</em><sub>2</sub><sup>(0)</sup>, <em>x</em><sub>3</sub><sup>(0)</sup>, <em>x</em><sub>4</sub><sup>(0)</sup>, <em>x</em><sub>5</sub><sup>(0)</sup>]<em><sup>T </sup></em>is given. While in practice <em>x</em><sup>(</sup><em><sub>j</sub><sup>i</sup></em><sup>) </sup>are integers, we treat them as continuous variables. Also, <em>h </em>is a small stepsize in time, that, in this instance, is given and fixed. Also note that, although some simplifications can be applied to this system, we just treat it as a general 5 × 5 nonlinear system. Finally, note that it is not required that you understand the details of how this nonlinear system arises. You take the system as granted.

<ul>

 <li>[<em>5 points</em>] Write the system (1a)-(1e) in standard form <em>f </em>(<em>x</em><sup>(<em>i</em>)</sup>) = Indicate all components of <em>f </em>. Write (by hand, i.e.</li>

</ul>

in latex) the Jacobian matrix for this system. Indicate all entries (some in terms of <em>x</em><sup>(</sup><em><sub>j</sub><sup>i</sup></em><sup>))</sup>).

<ul>

 <li>[<em>8 points</em>] Consider Newton’s method for this system. One iteration of Newton’s includes computation of the form solve <em>J</em>(<em>x</em>(<em>i</em>,<em>k</em>−1))<em>s</em>(<em>i</em>,<em>k</em>−1) =− <em>f </em>(<em>x</em>(<em>i</em>,<em>k</em>−1)) compute <em><sub>x</sub></em>(<em>i</em>,<em>k</em>) = <em><sub>x</sub></em>(<em>i</em>,<em>k</em>−1) + <em><sub>s</sub></em>(<em>i</em>,<em>k</em>−1)</li>

</ul>

Note that <em>i </em>is the time point index, while <em>k </em>is the index for Newton’s iteration, the former remaining constant through all Newton iterations (all <em>k</em>).

Write a matlab or equivalent script that, given <em>N </em>= 38<em>e</em>6, α<sup>−</sup><sup>1 </sup>= 6, β = 0. 25, γ = 0. 06, µ = 0. 01/365, ρ = 300µ, <em>h </em>= 1/2, <em>x</em>1(0) = <em>N </em>− <em>x</em>2(0) − <em>x</em>3(0) − <em>x</em>4(0), <em>x</em>2(0) = 20<em>e</em>3, <em>x</em>3(0) = 30<em>e</em>3, <em>x</em>4(0) = 850<em>e</em>3, and <em>x</em>5(0) = 0, computes <em>x</em>(1) by Newton’s method with tolerance 10<sup>−6</sup>. Use maxit = 10, and as stopping criterion the infinity norm of the <em>residual </em>vector. The Jacobian must be solved using <em>backslash</em>. At each Newton iteration, output <em>x</em><sup>(1,<em>k</em>) </sup>(the five values computed), the sum of the five values and the infinity norm of the residual. See script testnl.m (in the course website) for some template. Comment on the number of Newton iterations and on how the residual behaves as the iterations proceed.

– 2 –

<ul>

 <li>[<em>7 points</em>] Consider now a simulation time period from 0 to <em>t<sub>end </sub></em>= 150 (can be viewed as a period of 150 days), divided</li>

</ul>

<em>t<sup>end </sup></em>in <em>nstep </em>=       periods of stepsize (length) <em>h </em>= 1/24 (or <em>dt</em>), and that, at each time point <em>i</em>, giv en the state at time point <em>h</em>

<em>i </em>− 1, a nonlinear system of the form (1a)-(1e) is solved by Newton’s method with tolerance 10<sup>−6</sup>. Write a script that, given the same parameters as in (b), except that ρ = 0 (and <em>h </em>= 1/24), computes <em>x</em><sup>(<em>i</em>)</sup>, for <em>i </em>= 1,…, <em>nstep</em>. Do NOT output and do NOT sav e the results of each Newton iteration. Save, but do NOT output, the number of Newton iterations at each timestep. Save, but do NOT output, the results (<em>x</em><sup>(<em>i</em>)</sup>) from each time point. They will be used later for plotting. Output the initial values <em>x</em><sup>(0) </sup>and their sum, the computed final <em>x</em><sup>(<em>nstep</em>) </sup>(five values at time <em>t<sub>end</sub></em>), and their sum, as well as the maximum number of each type of persons among all time points (steps). Output also which <em>day </em>the maximum number of infected persons occurs.

Plot <em>x</em><sub>1</sub><sup>(<em>i</em>)</sup>, <em>x</em><sub>2</sub><sup>(<em>i</em>)</sup>, <em>x</em><sub>3</sub><sup>(<em>i</em>)</sup>, <em>x</em><sub>4</sub><sup>(<em>i</em>) </sup>and <em>x</em><sub>5</sub><sup>(<em>i</em>) </sup>versus <em>ih</em>, <em>i </em>= 0,…, <em>nstep </em>(index of time point scaled by <em>h</em>), in one plot, using solid (red), dashed (green), dashed-dotted (blue), dotted (black), and plain dot (cyan, ’c.’) lines. Add proper legend, labels for axes, etc. Use axis tight; <em>after </em>the plot.

In another plot, plot the number of Newton’s iteration at each timestep, versus the index of the timestep. Add labels for axes. Use axis([1 nstep 0.9 2.1]); <em>after </em>the plot. See script nlflu.m (in the course website) for some template.

<ul>

 <li>[<em>5 points</em>] Do another simulation for time period from 0 to <em>t<sub>end </sub></em>= 365, with <em>h </em>= 1/24, and otherwise the same parameters as in (b), i.e. with ρ = 300µ. Output the same quantities and do the same plots as in (c), with the same axis specifications.</li>

 <li>[<em>15 points</em>] Do another simulation for time period from 0 to <em>t<sub>end </sub></em>= 365, with <em>h </em>= 1/24, and with the same parameters as in (b) (i.e. with ρ = 300µ), except that β = 25/4, as if measures are taken to reduce contacts by a factor of 4. Output the same quantities and do the same plots as in (c), with the same axis specifications.</li>

</ul>

In addition, in a another plot, plot <em>x</em><sub>2</sub><sup>(<em>i</em>)</sup>, <em>x</em><sub>3</sub><sup>(<em>i</em>)</sup>, versus <em>ih</em>, <em>i </em>= 0,…, <em>nstep</em>, in one plot, using dashed (green) and dashed-dotted (blue) lines. Add proper legend, labels for axes, etc. Use axis tight; <em>after </em>the plot.

Place the first plot from (c) and the first from (d) side-by-side. Place the first and last plots from (e) side-by-side. Place the three plots of number of iterations side-by-side in 1 × 3 format. Comment on all results of (c), (d) and (e), including output and plots.

<em>Notes: </em>Do not use any symbolic calculation of any sort. The derivatives should be derived by hand and hard-coded into the Jacobian matrix.

<ol start="2">

 <li>[To be done by hand/latex, no coding.] Let <em>f </em>(<em>x</em>) = <em>x </em>sin(<em>x</em>) − 1.</li>

</ol>

<ul>

 <li>[<em>1 points</em>] Determine graphically the number of roots of <em>f </em>(<em>x</em>) = 0 in the interval [0, π]. (<em>Hint</em>: Rewrite equation <em>f </em>(<em>x</em>) = 0 to make graphing by hand easy.)</li>

 <li>[<em>2 points</em>] Show mathematically that <em>f </em>has a unique root in [ , ].</li>

 <li>[<em>1 points</em>] Consider the fixed-point iteration scheme <em>x</em><sup>(<em>k</em></sup><sup>+1) </sup>= <em>g</em>(<em>x</em><sup>(<em>k</em>)</sup>), with <em>g</em>(<em>x</em>) = . Show mathematically that <em>g </em>has a unique fixed point, say <em>x </em>*, in [ , ].</li>

 <li>[<em>8 points</em>] Find a (closed) interval <em>I </em>of length at least , that contains <em>x </em>*, so that, if <em>x</em><sup>(0) </sup>∈<em>I</em>, the iteration <em>x</em><sup>(<em>k</em></sup><sup>+1) </sup>= <em>g</em>(<em>x</em><sup>(<em>k</em>)</sup>) converges to <em>x </em>*. Specify <em>I </em>and explain. (You can specify the endpoints of <em>I </em>in terms of π.) (e) [<em>4 points</em>] What is the order of convergence of the iteration scheme in (d)? Justify mathematically.</li>

</ul>

(f)        [<em>6 points</em>] Show that the iteration <em>x</em><sup>(<em>k</em></sup><sup>+1) </sup>= <em>g</em>(<em>x</em><sup>(<em>k</em>)</sup>) converges to <em>x </em>*, if <em>x</em>

(Note: If you have already shown this in (d), you can skip this question.)

<sup>(0) </sup>= π , and indicate the computed (g) [<em>3 points</em>] Apply by hand one Newton iteration to <em>f </em>(<em>x</em>) = 0, with starting guess <em>x</em>

2 <em>x</em>(1).

<ol start="3">

 <li>[To be done by hand/latex, except (e).]</li>

</ol>

<ul>

 <li>[<em>3 points</em>] Use Newton’s Divided Differences, to construct a interpolating polynomial <em>p</em><sub>1</sub>(<em>x</em>) of the function <em>f </em>(<em>x</em>) = <em>e</em><sup>−<em>x </em></sup>(i.e. <em>f </em>(<em>x</em>) = exp(−<em>x</em>)), based on the data points <em>x</em><sub>0 </sub>=− 1 and <em>x</em><sub>1 </sub>= Show the NDD table, and the interpolating polynomial <em>p</em><sub>1</sub>(<em>x</em>).</li>

</ul>

<em>Note</em>: It is fine to leave quantities such as <em>e</em><sup>−1 </sup>and <em>e </em>in the presentation of the table entries and polynomial coefficients, as long as you reasonably simplify all terms.

– 3 –

<ul>

 <li>[<em>3 points</em>] Giv e the polynomial interpolation error formula for this problem. Note that the formula involves an unknown point ξ.</li>

</ul>

Using the formula, find a (sharp) bound of the (absolute value of the) error for any <em>x</em>∈[−1, 1]. Indicate the interval ξ belongs to, when <em>x</em>∈[−1, 1].

Using the formula, find a (sharp) bound of the (absolute value of the) error for any <em>x</em>∈[1, 2]. Indicate the interval ξ belongs to, when <em>x</em>∈[1, 2].

<ul>

 <li>[<em>4 points</em>] Use Newton’s Divided Differences, to construct the lowest degree interpolating polynomial <em>p</em><sub>2</sub>(<em>x</em>) of the function <em>f </em>(<em>x</em>) = <em>e</em><sup>−<em>x </em></sup>(i.e. <em>f </em>(<em>x</em>) = exp(−<em>x</em>)), based on the data points <em>x</em><sub>0 </sub>=− 1, <em>x</em><sub>1 </sub>= 0 and <em>x</em><sub>2 </sub>= Show the NDD table, and the interpolating polynomial <em>p</em><sub>2</sub>(<em>x</em>).</li>

</ul>

<em>Note</em>: It is fine to leave quantities such as <em>e</em><sup>−1 </sup>and <em>e </em>in the presentation of the table entries and polynomial coefficients, as long as you reasonably simplify all terms.

<ul>

 <li>[<em>5 points</em>] Giv e the polynomial interpolation error formula for this problem. Note that the formula involves an unknown point ξ.</li>

</ul>

Using the formula, find a (sharp) bound of the (absolute value of the) error for any <em>x</em>∈[−1, 1]. Indicate the interval ξ belongs to, when <em>x</em>∈[−1, 1].

Using the formula, find a (sharp) bound of the (absolute value of the) error for any <em>x</em>∈[1, 2]. Indicate the interval ξ belongs to, when <em>x</em>∈[1, 2].

<ul>

 <li>[<em>10 points</em>] Giv e the Taylor polynomials <em>t</em><sub>1</sub>(<em>x</em>) and <em>t</em><sub>2</sub>(<em>x</em>) of degree 1 and 2, respectively, that arise by expansion of <em>f </em>(<em>x</em>) = <em>e</em><sup>−<em>x </em></sup>about <em>x </em>= Write a MATLAB script that uses <em>polyfit </em>to compute the polynomials <em>p</em><sub>1</sub>(<em>x</em>) and <em>p</em><sub>2</sub>(<em>x</em>), interpolating <em>f </em>(<em>x</em>) at 2 and 3 equidistant data points in [−1, 1], respectively. The script then evaluates the four polynomials, <em>p</em><sub>1</sub>, <em>p</em><sub>2</sub>, <em>t</em><sub>1</sub>, <em>t</em><sub>2</sub>, and the function <em>f </em>at 100 equidistant evaluation points in [−1, 1]. Let <em>v</em><sub>1</sub>, <em>v</em><sub>2</sub>, <em>u</em><sub>1</sub>, <em>u</em><sub>2 </sub>and <em>v <sub>f </sub></em>be the vectors of values of <em>p</em><sub>1</sub>, <em>p</em><sub>2</sub>, <em>t</em><sub>1</sub>, <em>t</em><sub>2 </sub>and <em>f </em>, respectively, at 100 equidistant evaluation points in [−1, 1]. In one plot, graph <em>v</em><sub>1</sub>, <em>v</em><sub>2</sub>, <em>t</em><sub>1 </sub>and <em>t</em><sub>2 </sub>and <em>v <sub>f </sub></em>versus the evaluation points. Use solid, dashed, dotted, dotted-dashed and solid lines, respectively, and appropriate legend and labels. In another plot, graph <em>v <sub>f </sub></em>− <em>v</em><sub>1</sub>, <em>v <sub>f </sub></em>− <em>v</em><sub>2</sub>, <em>v <sub>f </sub></em>− <em>u</em><sub>1</sub>, <em>v <sub>f </sub></em>− <em>u</em><sub>2</sub>, versus the evaluation points. Use solid, dashed, dotted and dotted-dashed lines, respectively, and appropriate legend and labels. Calculate and output max |<em>v <sub>f </sub></em>− <em>v</em><sub>1</sub>|, max |<em>v <sub>f </sub></em>− <em>v</em><sub>2</sub>|, max |<em>v <sub>f </sub></em>− <em>u</em><sub>1</sub>|, and max |<em>v <sub>f </sub></em>− <em>u</em><sub>2</sub>|,. Place the plots side-by-side with appro-</li>

</ul>

<em>eval pts                      eval pts                      eval pts                                eval pts</em>

priate captions/subcaptions. Comment on the results.

<ol start="4">

 <li>[<em>10 points</em>] Consider using three types of interpolation for the function <em>f </em>(<em>x</em>) = exp(−<em>x</em>), namely, polynomial, linear spline and cubic spline interpolation, as in script http://www.cs.toronto.edu/˜ccc/Courses/336/scriptint.m</li>

</ol>

Add the appropriate extra lines to the script to compute the cubic spline interpolant at the points indicated. Then run the script and collect the output. (If you get a warning from polyfit, you are not necessarily doing anything wrong.) Comment on the results, in particular, how the error of each interpolant behaves as the number of data points increases, and whether this behaviour agrees with what expected from theory.

Do not change the format according to which the errors and other quantities are output. You need to explain what the other quantities represent.

General note: Plotting quantity <em>y </em>versus quantity <em>x</em>, means that <em>x </em>is in the <em>x</em>-axis and <em>y </em>is on the <em>y</em>-axis, i.e. what follows “versus” is in the horizontal axis.