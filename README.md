Download Link: https://assignmentchef.com/product/solved-comp4901l-computer-vision-fall-2019-homework-assignment-4-physics-based-vision
<br>
<h1>1           Overview</h1>

The purpose of this homework is to go over the topics of radiometry, reflectance, photometric stereo, and color. Given the short nature of this homework, and unlike previous assignments, it consists of a few smaller and independent problems, rather than a sequence of related problems.

<h2>1.1         Lambertian albedo  (10 points)</h2>

For Lambertian surfaces, the BRDF is a constant function of the input and output directions. For such a material, we often describe the reflectance in terms of its albedo, which is given the symbol <em>ρ</em>. For a Lambertian surface, the BRDF and albedo are related by <em>f<sub>r</sub></em>(<strong>v</strong>ˆ<em><sub>i</sub>,</em><strong>v</strong>ˆ<em><sub>o</sub></em>) = <em>ρ/π</em>. Using conservation of energy, prove that 0 ≤ <em>ρ </em>≤ 1.

<h2>1.2         Foreshortening         (10 points)</h2>

A small Lambertian source <em>dA </em>is centered at <em>P </em>and emits radiance <em>L</em>. The orientation of this patch is the same as that of a plane containing two points, <em>X</em><sub>1 </sub>and <em>X</em><sub>2</sub>. The point <em>X</em><sub>1 </sub>is the point on this plane that is closest to <em>P</em>, and the distance from <em>P </em>to <em>X</em><sub>1 </sub>is <em>D </em>as shown.

<ol>

 <li>Calculate the solid angle subtended by <em>dA </em>at points <em>X</em><sub>1 </sub>and <em>X</em><sub>2</sub>.</li>

 <li>Calculate the irradiance <em>E </em>incident on the plane at points <em>X</em><sub>1 </sub>and <em>X</em><sub>2</sub>, and calculate the ratio <em>E</em>(<em>X</em><sub>1</sub>)<em>/E</em>(<em>X</em><sub>2</sub>).</li>

</ol>

<h2>1.3         Simple rendering      (10 points)</h2>

Obtain the file bunny.mat from the data folder of this assignment and load it into Matlab. There is a single variable in this file; the variable N is an <em>h </em>× <em>w </em>× 3 array of surface normals. N(i,j,1), N(i,j,2), and N(i,j,3) are the <em>x</em>, <em>y</em>, and <em>z </em>components of the surface normal at the <em>ij</em>−<em><sup>th </sup></em>surface point, as observed by an orthographic camera with view direction (0<em>,</em>0<em>,</em>1).

<ul>

 <li>Use quiver to display the <em>x</em>–<em>y </em>components of the normal field and print the result.</li>

 <li>Compute and display the radiance emitted from each point assuming Lambertian reflectance and constant albedo (equal to one), with a distant point light source in direction ˆ<strong>s </strong>= (0<em>,</em>0<em>,</em>1), by typing imshow(N(:,:,3)). Explain why this works.</li>

 <li>Compute, display and print the emitted radiance for three different light source directions which are rotated i) 45<sup>◦ </sup>up, ii) 45<sup>◦ </sup>right, and iii) 75<sup>◦ </sup>right from the frontal direction ˆ<strong>s </strong>= (0<em>,</em>0<em>,</em>1). Can you spot errors in the field of surface normals? What are the illumination effects being ignored in this calculation of scene radiance?</li>

</ul>

<strong>In your write-up</strong>: Please include figures for the normal visualizations and the three renderings of the bunny, as well as answers to the associated questions.

<h2>1.4         Photometric stereo  (20 points)</h2>

The data folder of this assignment contains a set of seven photometric stereo images along with a MAT file containing the light source vectors. You can load the images into Matlab and convert them to double, grayscale format.

<ol>

 <li>Estimate the surface normal and grayscale albedo for each pixel. Submit your Matlab code as well as the results (using imshow for the albedo values and quiver for the surface normals.)</li>

</ol>

Figure 1: A few bunny renderings.

<ol start="2">

 <li>Note the poor estimates of the albedo (and surface normal) in the area surrounding the nostrils. What is the source of this error? Describe one method for finding a better estimate of this information from these seven images.</li>

 <li>Use the recovered surface information to predict what the person would look like (in grayscale) if illuminated from direction ˆ<strong>s </strong>= (0<em>.</em>58<em>,</em>−0<em>.</em>58<em>,</em>−0<em>.</em>58) and from direction ˆ<em>s </em>= (−0<em>.</em>58<em>,</em>−0<em>.</em>58<em>,</em>−0<em>.</em>58). Submit your results and your code.</li>

 <li>The function integrate frankot.m in the matlab folder can be used to recover a surface <em>z</em>(<em>x,y</em>) from your surface normals <strong>n</strong>ˆ(<em>x,y</em>), and the surface can be displayed in Matlab. Display and submit two views of the recovered shape.</li>

</ol>

Figure 2: Two views of the recovered face shape.

<strong>In your write-up</strong>: Include figures for the recovered normals and albedo, the re-rendered face images, and the final reconstructed surface, as well as answers to all associated questions.

<h2>1.5         Dichromatic reflectance     (30 points)</h2>

A reasonable reflectance model for dielectric (non-conducting) surfaces is the so-called dichromatic model, according to which the spectral BRDF is written as a linear combination of a Lambertian diffuse component <em>f<sub>d </sub></em>and a wavelength-independent specular component <em>f<sub>s</sub></em>:

<em>f</em>(<em>λ,ω</em>ˆ<em><sub>i</sub>,ω</em>ˆ<em><sub>o</sub></em>) = <em>f<sub>d</sub></em>(<em>λ</em>) + <em>f<sub>s</sub></em>(<em>ω</em>ˆ<em><sub>i</sub>,ω</em>ˆ<em><sub>o</sub></em>)

When we image a scene consisting of such surfaces under a directional light source with spectral power distribution <em>I</em>(<em>λ</em>) and direction <sup>ˆ</sup><em>l </em>= (<em>l<sub>x</sub>,l<sub>y</sub>,l<sub>z</sub></em>), the RGB values recorded at pixel <em>~u </em>= (<em>u,v</em>) can be expressed as

<em>C</em><em><sup>~</sup></em>(<em>~u</em>) = h<em>~n</em>(<em>~u</em>)<em>,</em><sup>ˆ</sup><em>l</em>i<em>d</em><em><sup>~</sup></em>(<em>~u</em>) + <em>g<sub>s</sub></em>(<em>~u</em>)<em>~s,</em>

where h·<em>,</em>·i, is the inner product operation, ˆ<em>n</em>(<em>~u</em>) is the surface normal at the scene point imaged by pixel <em>~u</em>, and <em>g<sub>s</sub></em>(<em>~u</em>) is a function that depends non-linearly on ˆ<em>n</em>(<em>~u</em>) (as well as view and lighting directions) through the specular component of the BRDF.

<ol>

 <li>Assuming that the spectral sensitivities of a camera’s three filters are (<em>c<sub>R</sub></em>(<em>λ</em>)<em>,c<sub>G</sub></em>(<em>λ</em>)<em>,c<sub>B</sub></em>(<em>λ</em>)) and that the BRDF at the surface point imaged at pixel <em>~u </em>is <em>f</em>(<em>λ,ω</em>ˆ<em><sub>i</sub></em>(<em>~u</em>)<em>,ω</em>ˆ<em><sub>o</sub></em>(<em>~u</em>)) = <em>f<sub>d</sub></em>(<em>λ,~u</em>) + <em>f<sub>s</sub></em>(<em>ω</em>ˆ<em><sub>i</sub></em>(<em>~u</em>)<em>,ω</em>ˆ<em><sub>o</sub></em>(<em>~u</em>)), write expressions for the elements of the <em>diffuse color vectors d</em><em><sup>~</sup></em>(<em>~u</em>) <em>and the source color vector ~s.</em></li>

 <li>Suppose you are given two unit-length three-vectors ˆ<em>r</em><sub>1 </sub>and ˆ<em>r</em><sub>2 </sub>that are orthogonal to <em>~s</em>. Show that the two-channel image<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> given by the per-pixel inner products (h<em>r</em>ˆ<sub>1</sub><em>,C</em><sup>ˆ</sup>(<em>u</em>ˆ)i<em>,</em>h<em>r</em>ˆ<sub>2</sub><em>,C</em><sup>ˆ</sup>(<em>u</em>ˆ)i):

  <ul>

   <li>does not depend on the specular components of the BRDFs, <em>f<sub>s</sub></em>(<em>ω</em>ˆ<em><sub>i</sub></em>(<em>~u</em>)<em>,ω</em>ˆ<em><sub>o</sub></em>(<em>~u</em>)).</li>

   <li>depends linearly on the surface normals, ˆ<em>n</em>(<em>~u</em>).</li>

  </ul></li>

 <li>Show that the two properties from part (b) are also satisfied by the single-channel (grayscale) image <em>J</em>(<em>~u</em>) = ||<em>J~</em>(<em>~u</em>)||.</li>

 <li>Write a function imout=makeLambertian(im,s) that takes an RGB image im and a source color vector s and computes the grayscale image <em>J</em>(<em>~u</em>) from part (c). Run this function on the image png from the data folder using s=[0.6257 0.5678 0.5349] and submit the results. Explain in three sentences or less why imout might be more useful than im to a computer vision system. Note that a simple way to numerically obtain a set of <em>N </em>− 1 unit-length vectors that are orthogonal to <em>N</em>-vector is to use the null command in Matlab.</li>

</ol>

<h2>1.6         Color metamers (Extra Credit)      (20 points)</h2>

Two distinct spectral distributions are <em>metameric </em>if they induce the same responses in the cones of a human retina. Said another way, <em>metamers </em>are distinct spectral distributions that map to the same tristimulus vector (in CIE XYZ or any other linear color space). If you own a grocery store that sells bananas, it is in your interest to choose your light source so that overripe bananas look that same as those in their prime. That is, you want the light reflected from ripe and overripe bananas to be metameric.

Let <em>f</em><em><sup>~ </sup></em>and <em>~g </em>be <em>N </em>×1 vectors that come from discretizing the spectral reflectance functions <em>f</em>(<em>λ</em>) and <em>g</em>(<em>λ</em>) of ripe and overripe bananas, respectively. (For example, if we sampled from 400nm to 700nm in increments of 10nm, we’d have <em>N </em>= 31.) Let <em>R </em>be the 3 × <em>N </em>matrix whose rows are obtained by discretizing the CIE XYZ color matching functions.

Figure 3: Left: Original color image. Right: Image converted to grayscale with specularities removed.

<ol>

 <li>Show that the tristimulus vector ) for a ripe banana) under illuminant spectrum <em>l</em>(<em>λ</em>) can be written as <em>C<sub>f </sub></em>= <em>L<sub>f</sub>l </em>where <em>L<sub>f </sub></em>is a 3×<em>N </em>matrix and <em>l </em>is the discretization of <em>l</em>(<em>λ</em>).</li>

 <li>Given <em>f</em><em><sup>~ </sup></em>and <em>~g</em>, a good way to choose <em><sup>~</sup>l </em>is to minimize the distance, in a least-squares sense, of the two resulting tristimulus vectors. Write an expression for the Euclidean distance between the two tristimulus vectors in terms of <em>L<sub>f</sub></em>, its counterpart <em>L<sub>g </sub></em>, and <em><sup>~</sup>l</em>.</li>

 <li>Write a Matlab function T=metamericLight(f,g) that finds the temperature T in the closed interval <em>T </em>∈ [2500<em>K,</em>10<em>,</em>000<em>K</em>], with precision ±50<em>K</em>, of the blackbody radiator that minimizes the distance derived in part (b). The spectral power distribution for a blackbody radiator (see FP Sect. 6.1.2) with temperature <em>T </em>is</li>

</ol>

where <em>a </em>= 1<em>.</em>4388 × 10<sup>−2</sup>(<em>m </em>· <em>K</em>).

<ol start="4">

 <li>The file mat from the data folder contains two spectral reflectance functions, ripe and overripe, which are sampled in 10nm increments from 400nm to 700nm and correspond roughly to the data from Day 5 and Day 7 of Figure 4. Use your function to find the optimal metamer-inducing blackbody temperature for these materials, and plot the distance as a function of temperature, and the spectral power distribution of the best illuminant. You will need to use the file ciexyz64 1.csv from the data folder, which contains tabulated data for the CIE XYZ color matching functions. In Matlab, you can read data from a CSV file using the csvread command. Remember to normalize the spectral power distributions of blackbody radiators in a way that is meaningful for the minimization criterion of part (b).</li>

</ol>

Figure 4: Relative spectral reflectance curves for different colors of bananas during ripening. Day five is the first day of shelf life. (Taken without permission from Morita et al., “Evaluation of Change in Quality of Ripening Bananas Using Light Reflectance Technique,” in <em>Memoirs of the</em>

<em>Faculty of Agriculture, Kagoshima University</em>, 1992.)

<a href="#_ftnref1" name="_ftn1">[1]</a> This image can have pixels with negative values, and these negative values are just as useful as the positive ones.