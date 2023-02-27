Converts 1D data into 2D image according to relation/correlation between features.

Here, let a features set of N features (81 for our case) needs to be transformed into images. Let there are M number of dataset ie M number of N feature set. If the transformed image is $x_i$  where i is index of an image, then dimension of image is $N_r \times N_c$, where $N_r \times N_c = N$, which is total number of features. So, we need no of features which can be formed by muliplying two natural numbers. The $Nr$ and $N_c$ is given by the user. For our case:
$$ N = 81\ :N_r = 9\ and\ N_c = 9 $$

The rank matrix is calculated which is of dimension $N \times N$, which is distance between each features. So, the top right and bottom left triangle of the rank matrax is symetrical. The rank value of the features is given by the row index or column index as row index and column index is equal. 

For optimization of ranks, the ideal rank matrix is taken, which is of dimesion $N \times N$. And the intensity of a pixel is given by distance between  i and j where i is row index and j is column index. So, ideally the diagonal is zero and the intensity increased with moving towards the corners such that corners is of highest intensity (pitch black).

For optimization, the rank matrx is compared with ideal rank matrix and swaping of colmuns(rank) is performed if needed. The loss is calculated as:
$$ loss(R, Q) = \sum_{i=1}^N \sum_{j=1}^i |r_{i,j} - q_{i,j}| $$
$$ where, r = rank\ matrix\ and\ q\ = ideal\ rank\ matrix$$

According to loss the swap is performed i.e. swap of columns causing lowest loss. 

### Algorithm
The algorithm takes four input parametes which are:
$S_{max}$ = maximum number of interation 
$S_{cov}$ = number of iteration for checking algorithm covergance
$t_{con}$ = small positive thereshold to determine whether the algorithm converges
$t_{swap}$ = threshold on the error reduction rate for feature swap

- Step 1:
	Calculate initial loss. Let s be 0 ie iteration index. Let $K_0$ be {1 .. N} which indicates ordering of features at the beginning before optimization
- Step 2:
	Identify the feature that has not been swaped for longest time which is determined by logging count and taking list features of least count and if list consit more than one feature, select feature randomly. Selected feature be 'k'. After selection of feature, find a feature swap that results in largest error reduction.
	$$ l^* = index(max(loss(R, Q) - loss(R_{k\Leftrightarrow l}, Q))) $$
	$$ where, R_{k\Leftrightarrow l} = matrix\ after\ swaping\ k^{th} element\ and\ l^{th} element$$
	After finding the iteration is updated i.e. $s = s + 1$. The $l^*$ is the index selected for swaping
- Step 3:
	If the swap reduces the error by or more than error reduction threshold $t_{swap}$ then swap is performed else not.
	$$ t_{swap} < loss(R, Q) - loss(R_{k\Leftrightarrow l^*}, Q)$$
	If upper expression is true then swap is performed i.e. the rank matrix is updated $R = R_{k\Leftrightarrow l^*}$, the latest loss gets updated $e_s = loss(R_{k\Leftrightarrow l^*}, Q)$ and append the loss to the list of losses so that the convergence can be calculated, and the log of swaped feature count gets updated.
- Step 4:
	Check where to terminate the program stating the optimum solution of go on. Two condition is checked. If one of the condtion is satisfied the program is terminated.
	$$ s = S_{max} $$
	$$ or $$
	$$ t_{con} > \frac{e_{s-s_{con}} - e_s}{e_{s-s_{con}}}$$
	If none of the above condition is satisfied the algorithm continues from step 2.
	If one of the above condition is satisfied the program terminates giveing the optimum solution which is rank matrix R. The index of the rank matrix R is the optimum index for converting 1D data into 2D image.

> TODO Add images