---------------------------------------------------------------------------------------------------------------------
Notice: This code is for academic (non-commercial) use only. 
-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
* How to compile and run the code
----------------------------------------
The folders "2DLimitedParralleRecon" and "2DLimitedFanbeamRecon" contain the parallel-beam reconstruction codes and fan-beam reconstruction codes, respectively.

Take the configuration of "2DLimitedParralleRecon" codes as an example (solution configuration is release and the solution platform is 64)£º

 1.  Create a new project in Visual Studio.

 2.  Copy the ".cpp" files, ".h" files, ".cu" files, ".cuh" files to the new project folder.

 3.  Copy the three folders named 'cufft', 'Eigen' and 'fftw' in the ..\x64\Release directory to the project folder.

 4.  Add the following five paths to the project in the 
     Properties -> Configuration Properties -> VC + + directory -> include directory:

     ..\cufft
     ..\Eigen\Eigen
     ..\fftw
     C:\ProgramData\NVIDIA Corporation\CUDA Samples\v8.0\common\inc
     C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\include

 5.  Add the following two paths to your project in 
     Properties -> Configuration Properties -> VC++ Directory -> Library Directory:

     ..\cufft
     ..\fftw
     C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\lib\x64

 6.  Copy the dynamic libraries like "cudart32_80.dll", "cudart64_80.dll", "libfftw3-     3.dll", "libfftw3f-3.dll" and  "libfftw3l-3.dll" to your project folder.

 7.  Add "cudart.lib", "libfftw3-3.lib", "libfftw3f-     3.lib", " libfftw3l-3.lib ", "cublas.lib", "cufft.lib" and "cufftw.lib"       in      Properties -> Configuration Properties -> Connectors -> Input -> Additional      Dependencies.

-------------------------------

When one needs to reproduce the results of some experiments, the reference data, projection data 
and the "script" file: "main.cpp"  in the corresponding folder shall be copyed to the project folder. 
Take the experiment AEDS(l_0,l_1) with noise in Section 3.1.3 as an example: 
 
Firstly, open the folder ..\SimulatedData\InverseCrimeTest\Noisy\AEDS(L0,L1) and then copy the "main.cpp" to your project folder.
Secondly, open the folder ..\SimulatedData\InverseCrimeTest\Noisy\reference data and then copy the reference data "FullAngleAnalytic_512_512" to your project folder.
Thirdly, open the folder ..\SimulatedData\InverseCrimeTest\Noisy\projection data and then copy the projection data "Pro-1024-201noise1.5(5)" to your project folder.
Lastly, regenerate (it is essential) and run to reproduce the results of that experiment.

----------------------------------------------
 *Meanings of used parameters
----------------------------------------------

"ImageSize" :                  the size of the reconstructed image.
"nNumDetec" :                  the number of detector units.
"fStaAng" :                    the starting scan angle.
"fAngRan":                     the scanning angular range.
"fInterAng":                   the scanning angular interval.
"fDetecSize":                  the detector unit width.
"nRMENum":                     the maximum iteration number.
"nInitialInterNum":            the iteration number of initial guess.
"fSOd":                        the distance from the x-ray source to the detector.
"ODd":                         the distance from the rotation center to the detector.

"lambda1", "lambda2", "Lambda", "mu", "nMedianRadiusNum" and "RelaxationPara"  correspond to
 \lambda_1, \lambda_2, \lambda_{l0}, \mu, r and \omega, respectively, which are specified in the paper. 

-----------------------------------------------------
