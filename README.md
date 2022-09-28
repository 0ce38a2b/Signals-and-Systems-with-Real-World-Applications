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
![image](https://user-images.githubusercontent.com/51925070/192440517-595e1c3e-11a9-4a25-9be5-da992e3ef597.png)
![image](https://user-images.githubusercontent.com/51925070/192441204-da95e6c1-8151-45d1-bd4d-0e59e907e2fc.png)    
Fourier bases for C^N, N是维度
- So we need N different vectors, each one of which will have length N.
- k will be the index that indicates different vector
- small n, to indicate the index of the element within each vector
- 实则每一个向量k, 都是一个离散的正弦信号，频率不同
![image](https://user-images.githubusercontent.com/51925070/192443407-22f52cab-9188-44a3-bef8-8344f0e739a1.png)
![image](https://user-images.githubusercontent.com/51925070/192443603-025b2bbe-180f-415c-b803-1286428ecda8.png)

##### DFT
![image](https://user-images.githubusercontent.com/51925070/192448276-9f31c831-a95b-4550-b795-0fc575b74580.png)

![image](https://user-images.githubusercontent.com/51925070/192448450-0cb25bb4-9525-4184-86c8-e26d67dc35dc.png)        
  Given an arbitrary element of C^N(call it x), we want to express x in this new Fourier basis.So the analysis formula will give us new coefficients for the vector in the new basis.And each coefficient, Xk will be simply the inner product of x with each vector of the new basis.(x 是原信号，wk 是傅里叶基向量，Xk 既是傅里叶系数)    
 If we want to go back to original representation for x, we simply have to sum a scaled version of all the basis functions. Please note here that since the basis is not orthonormal, and we choose to normalize in the synthesis formula by dividing N.
 ![image](https://user-images.githubusercontent.com/51925070/192451142-0b025bc1-1982-4db8-9239-381fd0824d8d.png)    
 If we recall Parseval's theorem, we know that the energy of a signal will not change if we change the underlying basis, so ener













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
![image](https://user-images.githubusercontent.com/51925070/192130195-1ed552c6-2dd7-43b3-a74a-f72fbad69566.png)     
And it is very easy to see that if we put the delta function in here, this is the average relationship that we saw before.    
![image](https://user-images.githubusercontent.com/51925070/192130303-092e0e55-bdfd-430a-a488-0510312f8033.png)
![image](https://user-images.githubusercontent.com/51925070/192130309-bfb02f02-88ef-4d7e-af4c-4c9f02577520.png)
![image](https://user-images.githubusercontent.com/51925070/192130332-ea3439c7-70e3-460c-9a30-8a90cfcb7cf6.png)
![image](https://user-images.githubusercontent.com/51925070/192130334-f29a34f6-aa82-49ce-aa93-efd37859b85e.png)
![image](https://user-images.githubusercontent.com/51925070/192130378-38594fe1-8aaf-4c13-bdd1-ac629dd84ce3.png)
![image](https://user-images.githubusercontent.com/51925070/192130394-8084608a-8088-4a26-a7d4-0547e340a834.png)    
We can rearrange the index of the signal like so:    
![image](https://user-images.githubusercontent.com/51925070/192130412-4afa91e4-06e8-4741-8778-5bdaee1c086d.png)    
And this "k+1" that affects only the summation index can be propagated to the summation range.     
![image](https://user-images.githubusercontent.com/51925070/192130450-2cec000c-e490-4590-9a7f-f1b85f609c06.png)
![image](https://user-images.githubusercontent.com/51925070/192130479-bc4f31ad-3b14-494f-9e70-18f1ac2693b1.png)
![image](https://user-images.githubusercontent.com/51925070/192130544-1816f180-20ae-4b36-b1fa-c4830b388559.png)    
We obtain the relationship that we were looking for between the moving average over capital M points, and the moving average over M-1 delayed by 1.
![image](https://user-images.githubusercontent.com/51925070/192130591-98b81116-c994-4b3e-a8c7-1b26cef2e677.png)    



###### Leaky integrator
![image](https://user-images.githubusercontent.com/51925070/192130826-7679edf9-19f7-4580-8ad9-83cdeae91dae.png)
![image](https://user-images.githubusercontent.com/51925070/192130926-fa89eef0-8936-4a1f-9179-3eede53aa90d.png)
![image](https://user-images.githubusercontent.com/51925070/192130936-34e583fc-a7eb-416b-b3dd-fd6a21d39735.png)
![image](https://user-images.githubusercontent.com/51925070/192130981-be0471ee-157b-4d3f-8fc8-10803fa8a1ec.png)
![image](https://user-images.githubusercontent.com/51925070/192131004-5d6f65bd-1e40-44a0-aa2a-b419d96a2cec.png)


##### Filter classification in the time domain
According to the shape of their impluse response, we can already label a filter as belonging to one of the following categories.    
![image](https://user-images.githubusercontent.com/51925070/192688869-fdd5b8eb-f8b8-450e-b069-cdcaa29ca292.png)
![image](https://user-images.githubusercontent.com/51925070/192688912-70bd05b3-ba1e-486b-bf63-f59a7d6b7e85.png)
![image](https://user-images.githubusercontent.com/51925070/192688956-f317dac7-f841-4be9-b69f-f0de50cf2b5b.png)
![image](https://user-images.githubusercontent.com/51925070/192689223-0d282059-03ce-47a6-9061-9efadab7b3bf.png)

##### Filter stability
![image](https://user-images.githubusercontent.com/51925070/192689883-52d2a64e-792c-477f-a74f-45e5e229f60f.png)
![image](https://user-images.githubusercontent.com/51925070/192689943-6b4811aa-f818-4f81-852a-22f75e03ffb3.png)
![image](https://user-images.githubusercontent.com/51925070/192690041-c99dec4a-f9df-4b17-a780-39d2dea37072.png)
![image](https://user-images.githubusercontent.com/51925070/192690149-5e1f5eee-a4b3-48e4-91df-5b5ede7f827e.png)


##### The convolution theorem
What happens if you take a linear time invarient filter H, and we use as the input, a complex exponential of known frequency w0.
![image](https://user-images.githubusercontent.com/51925070/192707256-d6aa1143-e9e9-4a8a-94b1-479eab5399af.png)    
![image](https://user-images.githubusercontent.com/51925070/192690354-e2c51fb4-b5e2-4b99-b342-02d7862601bd.png)
An Eigen sequence is a aequence that when input to a linear time invariant filter, returns the sequence itself times a scaling factor which happens to be the value of the DTFT of the impulse response at the frequency of the input.

![image](https://user-images.githubusercontent.com/51925070/192690791-99c9b456-1ac4-4633-b211-705c9b9df469.png)    
- LTI system cannot change the frequency of a sinusoidal input.
- the DTFT of impulse response fully determines the frequency characteristic of a filter at a given frequency.
- 
![image](https://user-images.githubusercontent.com/51925070/192690928-e9d12958-a326-4147-bc08-d8e03918fdf1.png)
![image](https://user-images.githubusercontent.com/51925070/192691152-60465cc7-1acf-4ebd-be56-5757be4fb42b.png)    
The Fourier transform of impulse response is called the frequency response. We can split the significance of the product in the frequency domian, by separating the effects of the magnitude and those of the phase.    
So, the magnitude of the frequency response will determine whether certain frequencues of the input signal are going to be amplified or attenuated.    
The effect of the phase are a little bit more difficult to qualify right now, but the phase will determine whether the signal will conserve its shape in the time domain, or its shape will be altered.



###### Filter classification in the frequency domain
![image](https://user-images.githubusercontent.com/51925070/192693740-80abadf0-2ea3-435d-ad35-27dc5febed9e.png)    
Filter types according to phase response
- Linear phase
- Nonlinear phase

##### The ideal lowpass filter
















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


