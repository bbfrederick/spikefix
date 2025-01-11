# spikefix
Simple scripts for finding and removing spikes from fMRI datasets

Spikefix consists of two scripts, spikecheck and spikepatch.  They depend on a working installation of FSL to do most of the heavy lifting.

Spikecheck
==========
spikecheck finds the spikes.  Type it without arguments, and it will tell you what it expects for input.  Basically, it scans a 4D Nifti file, and finds volumes that have more than some number (default 150) of voxels that differ from the mean of the preceding and following images by more than some percentage (default is 3.0).  If the volume meets that criterion, the volume is labelled as a spike volume.  Various informational files are generated saying where the spikes are and how bad they are.

Spikepatch
=========
spikepatch removes spikes based on the output of spikecheck by replacing volumes with the mean of the preceding and following images.  If there is more than one spiked volume in a row, it interpolates over the gap.
