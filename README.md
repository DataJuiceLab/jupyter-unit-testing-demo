# Jupyter Unit Testing Demo

This demonstrates automated unit testing for Jupyter notebooks, using `ipnyb` for cross-notebook importing, and `pytest` with the `nbmake` plugin for test running.

The example notebook calculates summary data for when devices begin charging (i.e. how low was the battery when someone started charging it), including the mean, min, max, and standard deviation across multiple devices.

# Installation

1. Ensure you have the prerequisites installed
    a. Python 3
    b. Jupyter Lab >= 3.0 (`pip install jupyterlab`)
    c. ipnyb (`pip install ipnyb`)
    d. nbmake (`pip install nbmake`)
    e. pandas (`pip install pandas`)
2. Clone this repository
3. Open Jupyter Lab (`jupyter lab`) to view, edit, and manually run tests
4. Run `pytest --nbmake` to run the test suite

The repository comes with a sample data input file ("battery-state-reports-last-30-days"). To link to your own data using the Losant template application this demo used:

1. Create a Losant sandbox account (or log into an existing Losant account)
2. Create a copy of the "Asset Tracker" application template
3. Enable the device state workflow
5. Create an empty Data Table, "battery charging stats" (no are columns necessary)
4. Add a notebook
    a. Upload the "battery-state.ipynb" notebook file
    b. Add an input source
        i. type: device data
        ii. time range: last 30 days
        iii. attributes: 'battery'
        iv. file name template: "battery-state-reports-last-30-days.csv"
    c. Add an output destination
        i. type: data table 
        ii. data table: "battery charging stats"
        iii. option: enable "Create columns from CSV if they do not exist in data table"
        iv. name: 'summary.csv'
5. Download the data and place it in the same directory as the repository
    a. Either: request a data export, and download the file via the link in the email you receive
    b. Or: execute the notebook, and when it completes download the file via the link in the Execution Log