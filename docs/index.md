# Imaging (fMRI) data processing with High Performance Computing (HPC) cluster at the University of Arizona

Created and maintained by: Diheng Zhang ([diheng.zhang@gmail.com](mailto:diheng.zhang@gmail.com))

Docs created at: Oct 11th, 2022

Docs updated at: 2022-10-14 12:19:22 

Contributors:
- Andrea Coppola, M.A.
- Dianne Patterson, Ph.D.
- Teodora Stoica, Ph.D.

This is intended to be a documentation for starting fMRI data processing on HPC at UA. It mainly serves two purposes: 1. document the way I implement data (pre)processing for my doctoral dissertation and in the same time, 2. provide an example of one way to do that. This documentation is not intended to be exhaustive, however, external documentations will be provided at the beginning of each step for a deeper dive if needed.

## Starter resources

If you have no other previous experience with MRI data (pre-)processing, here are some external resources that can help you start:

- Dr. Saren H. Seeley's documentation on BIDS, fMRIPrep, MRIQC (local processing): [Read here](https://rpubs.com/sarenseeley/463941)
- [BIDS starter kit](https://bids-standard.github.io/bids-starter-kit/)
- fMRIPrep offical site: [Here](https://fmriprep.org/en/stable/)

Join Neuroimaging Workshops group (on D2L) for more imaging data processing workshops and tutorials. Usually meet on Mondays. Email Dianne Patterson ([dkp@arizona.edu](mailto:dkp@arizona.edu)) to be added to the D2L site.

![D2L_site](img/D2L.png)


## Converting your DICOM files to BIDS format

fMRIPrep is a *BIDS* app, meaning that it takes BIDS format data folders as input. BIDS stands for Brain Imaging Data Structure. It is recommended as a uniform structure to facilitate consistent collaboration between labs. See [BIDS starter kit](https://bids-standard.github.io/bids-starter-kit/) for more information.

For data security purposes, it is recommended you convert your dataset with a secure local lab machine.

Or, you can convert and deface your DICOM file to BIDS format with an online platform [ezbids](https://brainlife.io/ezbids/) by Brainlife. ezbids is a HIPAA compliant online platform that require you upload your raw DICOM folder. Documentation of ezbids see [here](https://github.com/brainlife/ezbids).

After you convert your DICOM files to BIDS format, we suggest that you use the [BIDS validator](https://bids-standard.github.io/bids-validator/) to check if the convertion is successful before you transfor your BIDS data to HPC.

## Starting with HPC@UA

### External resources
- Dr. Dianne Patterson's documentation on neural imaging on HPC@UA: [Neuroimaging-core documentation](https://neuroimaging-core-docs.readthedocs.io/en/latest/pages/hpc.html)

### Setting up your account on HPC

Here is the page for requesting an accout for HPC@UA: [HPC Account Creation](https://public.confluence.arizona.edu/display/UAHPC/Account+Creation)

If you are a PI, you will be registering a PI account, which will give you authority to sponsor individual or group access to HPC. For most of the graduate students, you will most likely requesting a sponsoered HPC account, which will be created upon approved from your sponsor (most likely your PI).

### Transferring data to HPC

*Note on data security:* HPC storages in general is not HIPAA compliant. It is recommended to convert your raw DICOM files to BIDS format, and then deface all imaging data before you transfer the data to HPC for further pre-processing.

- Globus:
Globus is the preferred way to transfer data from your local machine to HPC. Here is a 7 min video showing how to do that: [HPC 1b: Data Transfer](https://arizona.openclass.ai/resource/lesson-619ed67e898b4fb790c4e52a)  
  
You might also find this section of the Neuroimaging-core webpage helpful: [Neuroimaging-core/Transferring Files](https://neuroimaging-core-docs.readthedocs.io/en/latest/pages/hpc.html#transferring-files)

Step 1 - Register/Log in to [Globus](https://www.globus.org/): You can log in with your UA SSO credential. Just click "Log in" on the right upper corner and follow the instruction.

Step - 2 - Install Globus Connect Personal on your computer as an Endpoint: if your data is deidentified, you can use your personal laptop or any lab computer for this task. 

*Note for psychofizzer:* If you are a member for John Allen's Psychophysiology lab, just so you know that as of Oct 21, 2022, we don't have Globus Connect Personal installed on any of our term server. I have tried installing it but results in error.

Step - 2 (Alternative) - Use Google Drive for Globus: if you want to skip the Globus Connect Personal route, Globus also works with Google Drive. As an UA student your Google Drive account (same as your UA email address) comes with unlimited storage (but soon will be 15 GB). If your data is under 15 GB in total and has been deidentified, I recommend using Google Drive for Globus file transfer. I also recommend compressing your deidentified BIDS data into a single zip file before you move it to Google Drive for Globus, so that it saves you time and increase reliability of transferring. Documentation see [here](https://docs.globus.org/how-to/gcsv5.3/access-google-drive/). To connect your Google Drive to your Globus account, go to Collection tab and search "UA Google Drive" and go from there.
    
### Storage options:

- HIPAA Box: This is recommanded if you want to do all your preprocessing on HPC. If you have access to a secure local machine for DICOM to BIDS convertion and defacing process (see below for more detail), you can skip this. [Link to request](https://uarizona.service-now.com/), See Home > Service Catalog > Teaching and Learning > Academic Technology > Box > Box Health Account Request.

Note: Each faculty at UA can request a 50 GB HIPAA Box account for free.