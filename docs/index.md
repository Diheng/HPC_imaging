# Imaging (fMRI) data processing with High Performance Computing (HPC) cluster at the University of Arizona

Diheng Zhang ([diheng.zhang@gmail.com](mailto:diheng.zhang@gmail.com))

This is intended to be a documentation for starting fMRI data processing on HPC at UA. It mainly serves two purposes: 1. document the way I implement data (pre)processing for my doctoral dissertation and in the same time, 2. provide an example of one way to do that. This documentation is not intended to be exhaustive, however, external documentations will be provided at the beginning of each step for a deeper dive if needed.

## Starter resources

If you have no other previous experience with MRI data (pre-)processing, here are some external resources that can help you start:

- Dr. Saren H. Seeley's documentation on BIDS, fMRIPrep, MRIQC (local processing): [Read here](https://rpubs.com/sarenseeley/463941)
- [BIDS starter kit](https://bids-standard.github.io/bids-starter-kit/)
- fMRIPrep offical site: [Here](https://fmriprep.org/en/stable/)

Join Neuroimaging Workshops group (on D2L) for more imaging data processing workshops and tutorials. Usually meet on Mondays. Email Dianne Patterson ([dkp@arizona.edu](mailto:dkp@arizona.edu)) to be added to the D2L site.

![D2L_site](img/D2L.png)

## Starting with HPC@UA

### External resources
- Dr. Dianne Patterson's documentation on neural imaging on HPC@UA: [Neuroimaging-core documentation](https://neuroimaging-core-docs.readthedocs.io/en/latest/pages/hpc.html)

### Setting up your account on HPC

### Transfering data to HPC

- Globus:
Globus is the preferred way to transfer data from your local machine to HPC. Here is a 7 min video showing how to do that: [HPC 1b: Data Transfer](https://arizona.openclass.ai/resource/lesson-619ed67e898b4fb790c4e52a)  
  
You might also find this section of the Neuroimaging-core webpage helpful: [Neuroimaging-core/Transferring Files](https://neuroimaging-core-docs.readthedocs.io/en/latest/pages/hpc.html#transferring-files)