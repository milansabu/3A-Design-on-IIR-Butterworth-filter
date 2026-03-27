# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

# To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc ; 
close ; 

wp = input('Enter the pass band frequency (Radians )= ' ); 
ws = input('Enter the stop band frequency (Radians )= ' ); 
alphap = input( 'Enter the pass band attenuation (dB)=' ); 
alphas = input('Enter the stop band attenuation(dB)=');
T = input('Enter the Value of sampling Time=')

omegap = (2/T)*tan(wp/2);
disp(omegap,'omegap=');
omegas = (2/T)*tan(ws/2);
disp(omegas,'omegas=');

N = log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap));
disp(N,'N=');
N = ceil(N);
disp(N,'Round off value of N');

omegac = omegap/(((10^(0.1*alphap))-1)^(1/(2*N)));
disp(omegac,'omegac=');

disp('Normalised Analog LPF Transfer function H(S)=');
hs_Normalised = analpf(N,'butt',[0,0],1);
disp(hs_Normalised);

disp('Analog LPF Transfer function H(S)=');
hs=analpf(N,'butt',[0,0],omegac);
disp(hs);

z = poly(0,'z');
Hz = horner(hs,(2/T)*((z-1)/(z+1)))
disp('Digital LPF Transfer function H(Z)=');
disp(Hz);

HW = frmag(Hz,512);
w = 0:%pi/511:%pi;
plot(w/%pi,abs(HW));
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude');
title('Frequency Response of Butterworth IIR LPF')
```


 # MANUAL CALCULATION:
<img width="901" height="1600" alt="image" src="https://github.com/user-attachments/assets/e63ec650-df4b-41cc-83a5-1094595ac1f1" />

<img width="901" height="1600" alt="image" src="https://github.com/user-attachments/assets/bd0af192-37b7-40c7-a0f1-95a646849715" />

<img width="901" height="1600" alt="image" src="https://github.com/user-attachments/assets/c8f4050b-9948-40a8-99a7-1cb72a9d134f" />

# OUTPUT:
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/4e349c8c-8a33-4cba-92fc-931375ecb34a" />

# RESULT: 

Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.

