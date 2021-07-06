# Jupyter Unit Testing Demo

This demonstrates automated unit testing for Jupyter notebooks, using `ipnyb` for cross-notebook importing, and `pytest` with the `nbmake` plugin for test running.

The example notebook calculates summary data for when devices begin charging (i.e. how low was the battery when someone started charging it), including the mean, min, max, and standard deviation across multiple devices.

# Installation

1. Ensure you have the prerequisites installed
    1. Python 3
    2. Jupyter Lab >= 3.0 (`pip install jupyterlab`)
    3. ipnyb (`pip install ipnyb`)
    4. nbmake (`pip install nbmake`)
    5. pandas (`pip install pandas`)
2. Clone this repository
3. Open Jupyter Lab (`jupyter lab`) to view, edit, and manually run tests
4. Run `pytest --nbmake` to run the test suite

## Losant Setup

The repository comes with a sample data input file ("battery-state-reports-last-30-days"). To link to your own data using the Losant template application this demo used:

1. Create a Losant sandbox account (or log into an existing Losant account)
2. Create a copy of the "Asset Tracker" application template
3. Enable the device state workflow
5. Create an empty Data Table, "battery charging stats" (no are columns necessary)
4. Add a notebook
    1. Upload the "battery-state.ipynb" notebook file. 
        1. Note: Losant does not curently support the 'id' property in Jupyter 3 cells. Check that these have not been added automatically if you have trouble uploading.
    2. Add an input source
        1. type: device data
        2. time range: last 30 days
        3. attributes: 'battery'
        4. file name template: "battery-state-reports-last-30-days.csv"
    3. Add an output destination
        1. type: data table 
        2. data table: "battery charging stats"
        3. option: enable "Create columns from CSV if they do not exist in data table"
        4. name: 'summary.csv'
5. Download the data and place it in the same directory as the repository
    1. Either: request a data export, and download the file via the link in the email you receive
    2. Or: execute the notebook, and when it completes download the file via the link in the Execution Log
