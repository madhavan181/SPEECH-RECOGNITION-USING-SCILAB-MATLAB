# EXP 5 : SPEECH RECOGNITION USING SCILAB

## AIM: 

To perform and verify speech recognition using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM : 

//  SPEECH RECOGNITION USING SCILAB
```
clc;
clear;
close;

disp("Loading audio files...");

// Read reference and test voice files (your uploaded files)
[y1, fs1] = wavread("C:\Users\acer\Downloads\DTSP\sample-12s.wav");   // Reference
[y2, fs2] = wavread("C:\Users\acer\Downloads\DTSP\sample-15s.wav");   // Test

// Check sampling rate
if fs1 <> fs2 then
    error("Sampling rates must match!");
end

// Convert stereo to mono (if needed)
if size(y1,2) == 2 then
    y1 = mean(y1, 2);
end
if size(y2,2) == 2 then
    y2 = mean(y2, 2);
end

// Force both signals to same length
n = min(length(y1), length(y2));
y1 = y1(1:n);
y2 = y2(1:n);

// Compute Euclidean distance
dist = sqrt(sum((y1 - y2).^2));

disp("Euclidean distance (reference vs test): " + string(dist));

// Decision threshold
if dist < 0.5 then
    disp("Matching with reference (same word)");
else
    disp("Not matching with reference (different word)");
end

// ----------------------
// PLOTS
// ----------------------

// Plot both signals separately
figure(0);
subplot(2,1,1);
plot(y1);
title("REFERENCE VOICE SIGNAL (sample-12s.wav)");
xlabel("Samples");
ylabel("Amplitude");

subplot(2,1,2);
plot(y2);
title("TEST VOICE SIGNAL (sample-15s.wav)");
xlabel("Samples");
ylabel("Amplitude");

// Combined plot
figure(1);
plot(y1, 'b');
plot(y2, 'r');
title("Reference (Blue) vs Test (Red) Signal");
xlabel("Samples");
ylabel("Amplitude");
legend(["Reference", "Test"]);

disp("Waveforms plotted successfully.");
```
## OUTPUT:

<img width="1158" height="607" alt="image" src="https://github.com/user-attachments/assets/a1dcaa5b-1243-48dc-8107-074425b1a98c" />

<img width="1134" height="616" alt="image" src="https://github.com/user-attachments/assets/0b458aae-c491-4882-a6a3-ee68c71cd2ac" />

## RESULT: 
Thus the speech recognition using SCILAB was performed and verified.
