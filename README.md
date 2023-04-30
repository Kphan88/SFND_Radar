# SFND_Radar

1. Implementation steps for the 2D CFAR process.

A for-loop iterates the RDM, doing the following operations:

- Calculate the sum of noise level of training cells by subtracting the non-training cell noise from the all cells' noise level
- average the summed noise level of all training cells 
- offset the threshold
- compare the signal under cell under test (CUT) against the threshold
- if CUT signal level is larger than the threshold, the CFAR value is set to 1, otherwise the value is 0


2. Selection of Training, Guard cells and offset.
- I chose to use 10 training cells and 2 guard cells in both range and doppler dimensions. Offset to the threshold was set to 5dB.
I chose these hyper parameters based on repeated experimentation.

T_range = 7; % training cells for range
T_doppler = 7; % training cells for doppler

G_range = 2; % guard cells for range
G_doppler = 2; % guard cells for doppler
offset = 5;

3. Steps taken to suppress the non-thresholded cells at the edges
I initialize the final signal with zeoros and fill out the cells that can be computed by sliding window.
