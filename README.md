# Signals-and-Systems-with-Real-World-Applications

##### A common framework: vector space
- vector spaces are very general objects
- vector spaces are defined by their properity
- once you know the properties are satisfied, you can use all  the tools for the space     
##### We need something to measure and compare: inner product(aka dot product 对应点相乘，求和)    
- measure the similarity between vectors
- inner product is zero ---> vectors are orthogonal(maximally different)

##### Signal spaces
![image](https://user-images.githubusercontent.com/51925070/192094072-ec289fb9-6a70-42a9-a37e-88fe8e40b853.png)    
CN is the space of length of complex numbers in vector notation.    
*：共轭
![image](https://user-images.githubusercontent.com/51925070/192094230-8e91950d-6f5b-427f-9510-55991441a797.png)    

##### Hilbert Space
When a vector space equipped with an inner product is also complete, we call the vector space a Hilbert space.(不完整案例，有理数序列求和收敛于无理数，这样的向量空间是不完整的) 

##### Basis
![image](https://user-images.githubusercontent.com/51925070/192094324-0912a05d-efbf-48e9-ae92-283d9e4fad7f.png)    
Notation: {w^k} indicates a family of vectors, k is the cardinal number of the vector in the family.
![image](https://user-images.githubusercontent.com/51925070/192094583-519ad6a6-7552-413c-b2ad-9152fbca84ce.png)    
The inner product between any two vectors in the basis is equal to the delta of the difference between the indices.So, in other word, if the vectors are not the same vector, the inner product will be equal to zero.基组之间相互正交。    
![image](https://user-images.githubusercontent.com/51925070/192094880-4a9466f7-19ec-4f23-91a3-21fac5c5f583.png)

###### Change of basis
![image](https://user-images.githubusercontent.com/51925070/192094929-e4643bd6-850f-432a-ba4b-ed348a9bb6c5.png)    
![image](https://user-images.githubusercontent.com/51925070/192094939-4f47b06a-cf81-4c1f-9747-04fa4a129b60.png)    
  What is remarkable however, is that the factors used in this linear combination do not depend on the vectors that we are manipulating. These are just inner products between vectors in the original basis and the new basis. As a matter of fact, we can write this sum here as matrix vector multiplication. 
- In other words, given a starting basis and an orthogonal arrival basis. You can compute this change of basis matrix once and for all. And everytime you have to change the reference system for a vector(a signal), 只需要做一次矩阵向量乘法。We will see very soon that this is really what't behind the DFT 算法.

##### Fourier Analysis
Fourier bases for C^N, N是维度
- So we need N different vectors, each one of which will have length N.
- k will be the index that indicates different vector
- small n, to indicate the index of the element within each vector

##### Linear time-invariant filters
___冲击响应是一个LTI系统的特征___    
Time invariance
y[n] = H{x[n]} <==> H{x[n-n0]} = y[n-n0]    
![image](https://user-images.githubusercontent.com/51925070/191734954-7bb23571-e9f5-46b7-bde5-d7cb533bc383.png)
Another requirement that is not mandatory, but makes a lot of sensem, is that the system be causal.(the system can only have access to input and output values from teh past)
![image](https://user-images.githubusercontent.com/51925070/191735668-0d67ce55-3bcb-49e9-b9e4-be9de4566ff1.png)

##### Convolution
![image](https://user-images.githubusercontent.com/51925070/191736639-53c73780-5f29-409b-8542-4e27f93fbe3b.png)
In general, we can always write x[n](a generic discrete time sequence as the sum of time delayed deltas scaled by the values of the sequenceitself.)
___The convolution which represents the output of a filter given its impulse response and an arbitary input sequence x[n] 用卷积计算LTI系统的输出___    
It is actually an algorithmic formula to compute the output of the filter.
![image](https://user-images.githubusercontent.com/51925070/191738763-d1fd565c-36aa-42ef-b42a-c3500c873b76.png)
___inner product: 加权求和___
![image](https://user-images.githubusercontent.com/51925070/191740011-be2dbced-4821-4483-bc74-d4fc2d6440fb.png)
The convolution is also associative, which means that if you have a cascaded system, you can lump their effevt into a single filter, whose impulse response is the convolution of the individual impulse response.

#### The moving average filter


### MATLAB for Signal Processing Review
#### Spectral Analysis Workflow
- Import signals
- Preprocess signals
- Analyze spectrum
- Filter signals
- Deploy / Calculate features
##### Preprocessing
- Normalizing
- Resampling
- Aligning
##### Analyze spectrum
To view the frequency content of a signal, you can calculate the power spectrum with the pspectrum function.    
- pspectrum(mysig)    
If you don't use any output arguments, pspectrum creates a plot.    
***
To zoom in on the meaningful seismic activity, you can set the frequency limits while calculating the power spectrum.
- pspectrum(mysig,"FrequencyLimits",[a b])
*** 


