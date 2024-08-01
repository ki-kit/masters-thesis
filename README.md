# masters-thesis

This is a series of codes used for my thesis in numerical relativity. The main goal was to generate gravitational waveforms from binary neutron star mergers and then analyse them. Colab was chosen due to its cloud-based nature, which mitigates the risk of data loss
associated with virtual machine failures on local systems, due to e.g. Windows update
breaking the virtual machine that is running a Linux distribution.


We will be using the [PyCBC](http://github.com/ligo-cbc/pycbc) library, which is used to study gravitational-wave data, find astrophysical sources due to compact binary mergers, and study their parameters.





In PyCBC there are plenty of waveform approximants readily available. The list is too long to write out here but it can be accessed by using the python commands presented on [this PyCBC link](https://pycbc.org/pycbc/latest/html/waveform.html).

We started by generating an already built-in time-domain waveform approximant by using the _get__td__waveform_ function, which requires parameters such as the masses of the binary system (in solar masses), sampling time (in seconds), starting GW frequency (in hertz), and the approximant's name - _SEOBNRv4_opt_. The output of this function are the plus and cross polarisations of the gravitational-wave signal as viewed from the line of sight at a given source inclination (assumed face-on if not provided).




We then implemented a custom waveform generator by merging the Colab waveform generator from previous section with PyCBC’s custom WF generator as instructed on [this PyCBC link](https://pycbc.org/pycbc/latest/html/waveform.html#adding-a-custom-waveform), resulting in a slightly longer code. This approach was chosen because it provides a way to add a custom WF into the already vast PyCBC WF approximants database.





Integrating the CoRe database required using the _watpy_ package for gravitational wave analysis. The CoRe database was accessed via Colab using specific commands, with the _geopandas_ package for data handling, which was beneficial, since we only had to include the respective github code for the dataset which we wanted to use, thus decreasing the download time. We have also previously verified in bash how the strains of the plus and the cross polarisations look like and we also printed them eparately to verify the correct implementation of the CoRe database. It is trivial to convert between the time domain and the frequency domain in PyCBC with one simple command hp.to_frequencyseries().




