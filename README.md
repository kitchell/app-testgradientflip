[![Abcdspec-compliant](https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg)](https://github.com/brain-life/abcd-spec)
[![Run on Brainlife.io](https://img.shields.io/badge/Brainlife-bl.app.1-blue.svg)](https://doi.org/10.25663/bl.app.1)

# app-testgradientflip
This application will provide a recommendation on which axis you should flip the bvecs of your data, if it is necessary. It will perform fiber tracking using 4 different gradient flip options (no flip, x flip, y flip, and z flip) and report the most likely flip needed for your data. The flip recommendation is made based on the flip direction with the highest number of long fibers.

### Author
- Lindsey Kitchell (kitchell@indiana.edu)

### Contributors
- Soichi Hayashi (hayashis@iu.edu)
- Steven O'Reilly (stevengeeky@gmail.com )

### Funding 
[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-1636893](https://img.shields.io/badge/NSF_BCS-1636893-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1636893)

## Running the App 

### On Brainlife.io

You can submit this App online at [https://doi.org/10.25663/bl.app.18](https://doi.org/10.25663/bl.app.18) via the "Execute" tab.

### Running Locally (on your machine)

1. git clone this repo.
2. Inside the cloned directory, create `config.json` with something like the following content with paths to your input files.

```json
{
    "dwi": "../5b96c398161e01002a31fb5a/5967bffa9b45c212bbec8956/dwi.nii.gz",
    "bvecs": "../5b96c398161e01002a31fb5a/5967bffa9b45c212bbec8956/dwi.bvecs",
    "bvals": "../5b96c398161e01002a31fb5a/5967bffa9b45c212bbec8956/dwi.bvals",
    "t1": "../5b96c398161e01002a31fb5a/5967bffa9b45c212bbec8957/t1.nii.gz",
    "phaseEncodeDir": "2",
    "rotateBvecsWithCanXform": true,
    "rotateBvecsWithRx": true,
    "eddyCorrect": "1"
}
```

If you have singularity installed on your local machine:

3. Launch the App by executing `main`

```bash
./main
```

Otherwise:

3. Execute the main.m file in matlab. 

### Sample Datasets

If you don't have your own input file, you can download sample datasets from Brainlife.io, or you can use [Brainlife CLI](https://github.com/brain-life/cli).


## Output

The main output of this App is a file called `output.mat`. This file contains following object.


#### Product.json

The secondary output of this app is `product.json`. This file allows web interfaces, DB and API calls on the results of the processing. 

### Dependencies

This App only requires [singularity](https://www.sylabs.io/singularity/) to run. If you don't have singularity, you will need to install following dependencies.  

  - VISTASOFT: https://github.com/vistalab/vistasoft/
  - MATLAB: https://www.mathworks.com/products/matlab.html
  - JSONlab: https://www.mathworks.com/matlabcentral/fileexchange/33381-jsonlab-a-toolbox-to-encode-decode-json-files
