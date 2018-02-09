"Lead Safe" is an API available to Chicago-area hospital and health networks to estimate the likelihood that a child will be exposed to lead-based paint hazards. Health network providers can provide information on the patient's demographics, address, and history on their past visits and blood-lead levels, the Lead Safe API will provide an estimate of the risk of elevated, unsafe blood-lead levels for children under 4 years-old.

The API uses a predictive model developed by the University of Chicago[^1] that uses historical blood-lead level testing conducted by the State of Illinois. Data submitted through this API and subsequent testing conducted will improve the accuracy of the model, allowing for a more effective use of blood tests to prevent elevated lead levels.

## Obtaining Access

### Eligibility

To access the API, fill out [this form](/apply/) to be contacted by the Chicago Department of Public Health. The city will need to verify your eligibility as an area health provider.

### Accessing API

In order to integrate with Lead Safe, the health provider will need to make a REST call against the API. To do so, they will be provided an API token which will provide some authentication. The city will also need to "whitelist" the IP address(es) of the health providers servers.

## Acknowledgements

The "Lead Safe" API was developed by the [Chicago Department of Public Health](https://www.cityofchicago.org/city/en/depts/cdph.html), University of Chicago's [Center for Data Science and Public Policy](http://dsapp.uchicago.edu/), and the [Chicago Department of Innovation and Technology](https://www.cityofchicago.org/city/en/depts/doit.html). This project was made possible by a grant from the [Robert Wood Johnson Foundation](http://www.rwjf.org/). 

[^1]: Potash _et al._ (2015) [Predictive Modeling for Public Health](https://dssg.uchicago.edu/wp-content/uploads/2016/01/p2039-potash.pdf). _Proceedings of the 21th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining_ pp. 2039-2047.
