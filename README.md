# HDRImaging
We explore a computational photography technique called High Dynamic Resolution (HDR) Imaging.

## What is HDR
Dynamic range refers to the ability to distinguish between bright sections and dark sections in a scene. Our eyes have excellent (high) dynamic range, about 100000:1 in so called 'stops'. However commercial cameras have limitations due to pixel sizes in terms of their ability to store photon generated charge. This can be mitigated by  by taking images of the same static scene at various exposures and then merging the images, a technique called High Dynamic Range Imaging.

## HDR Imaging
HDR imaging starts by taking (in a short time to limit changing lighting conditions) several images of the scene at various exposures. 

Next the images can then be digitally processed. First the images need to be aligned, since some position shift is likely. Using tripods and other techniques may mitigate this effect but still, it is better to align anyway.

Next the HDRI process is performed using the Debevec algorithms to calculate the radiance map. Debevec et.al. give a radiance equation

\begin{equation}
\sum_{i=1}^{N}\sum_{j=1}^{P} \left \{ w(z_{ij} [g(z_{ij})-\ln E_{i} - \ln\Delta t_{j} ])\right \}^{2} + \lambda \sum_{Z=Z_{min+1}}^{Z=Z_{max-1}}[w(z)g''(z)]^{2} = 0 
\end{equation}

The least squares solver then looks like

$ [A]_{NXP+255,256+N} \{x\}_{256+N,1} = \{b\}_{NXP}$

More 'visually'


Then to produce a more aesthetically pleasing image, Tone mapping is applied. The calculated HDR values cannot be used on devices which has limited dynamic range like our screens. Tone mapping reverses the HDRI process while preserving the features in the HDR images and present aesthetically  pleasing colors.
