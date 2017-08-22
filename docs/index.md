"Lead Safe" is an API available to Chicago-area hospital and health networks to provide estimates on a child's potential exposure to elevated lead levels from household paint. Health network providers can provide information on the patient's demographics, address, and history on their past visits and blood-lead levels, the Lead Safe API will provide an estimate on the chance of elevated, unsafe blood-lead levels for children under 4 years-old.

The API uses a predictive model developed by the University of Chicago[^1] that uses historical blood-lead level testing conducted by the State of Illinois. Data submitted through this API and subsequent testing conducted will improve the accuracy of the model, allowing for a more effective use of blood tests to prevent elevated lead levels.

## Obtaining Access

### Eligibility

To access the API, fill out [this form](#) to be contacted by the Chicago Department of Public Health. The city will need to verify your eligiblity as an area health provider.

### Accessing API

In order to integrate with Lead Safe, the health provider will need to make a REST call against the API. To do so, they will be provided an API token which will provide some authentication. The city will also need to "whitelist" the IP address(es) of the health providers servers.


## API

### Parameters

| Field          | Format   | Constraints                                                | Notes/Questions                                                                                                                                                                                                             |
|----------------|----------|------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| timestamp      | TimeDate | yyyy-mm-dd hh:mm:ss.sss-hh.mm                              | Current Timestamp. RFC 3339 (ISO 8601 derivative).                                                                                                                                                                          |
| clinic_id      | Text     |                                                            | Two Characted Organization ID (NN- NearNorth  EF- ErieFamily)                                                                                                                                                               |
| location_id    | Text     |                                                            | Specific Location Abbreviation in Centricity                                                                                                                                                                                |
| alliance_id    | Text     | AlphaNumeric                                               | Uses CPS PatientProfile.patientID                                                                                                                                                                                           |
| address1       | Text     | Address number, street direction, street name, street type | Patientprofile.address1                                                                                                                                                                                                     |
| address2       | Text     | Additional address information, e.g. apartment number      | patientprofile.address2                                                                                                                                                                                                     |
| city           | Text     |                                                            | patientprofile.city                                                                                                                                                                                                         |
| state          | Text     |                                                            | patientprofile.state                                                                                                                                                                                                        |
| zip            | Text     | 5 digit zip code                                           | patientprofile.Zip                                                                                                                                                                                                          |
| date_of_birth  | Date     | yyyy-mm-dd                                                 |                                                                                                                                                                                                                             |
| gender         | Text     | M/F/U                                                      |                                                                                                                                                                                                                             |
| race           | Text     | Code Values from Centricity                                | Standard ONC Race definitionsCode     description1002-5  American Indian or Alaska Native2028-9  Asian  2054-5  Black or African American 2076-8  Native Hawaiian or Other Pacific Islander 2106-3  White UNK       Unknown |
| ethnicity      | Text     | Code Values from Centricity                                | Standard ONC Ethnicity definitionsCode     description2135-2  Hispanic or Latino  2186-5  Non Hispanic or Latino UNK      Unknown                                                                                           |
| Visit Array    |          |                                                            |                                                                                                                                                                                                                             |
| visit.visit_id | Numeric  | 16 Digit GE ID                                             | Unique GE ID for specific visit  (DocumentID)                                                                                                                                                                               |
| visit.date     | Date     | yyyy-mm-dd                                                 |                                                                                                                                                                                                                             |
| visit.location | Text     |                                                            | Text Abbreviation for facility of visit location                                                                                                                                                                            |
| visit.provider | Text     |                                                            | Full provider name, last name, or just NPI                                                                                                                                                                                  |
| Lab Array      |          |                                                            |                                                                                                                                                                                                                             |
| lab.lab_id     | Numeric  | 16 Digit GE ID                                             | Unique GE ID for specific lab result (ObsID)                                                                                                                                                                                |
| lab.type       | Text     | BLL                                                        | Static BLL unless we identify additional labs to include                                                                                                                                                                    |
| lab.date       | Date     | yyyy-mm-dd                                                 |                                                                                                                                                                                                                             |
| lab.route      | Text     | V                                                          | *Always "V"  Veinous for Alliance sites                                                                                                                                                                                     |
| lab.result     | Text     |                                                            | Several values are possible; integer, non-integer numeric, ranges indicated by alphanumeric text.  We'll use previous examples to essentially construct a dictionary.                                                       |

#### Example Call

```shell
POST 
```

### Response Parameters

| Field            | Format       | Constraints                                                                     | Notes/Questions                                                                                  |
|------------------|--------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| version          | Text         | "0.2.1"                                                                         | Follows Semantic Versioning 2.0.0 http://semver.org/spec/v2.0.0.html                             |
| timestamp        | TimeDate     | yyyy-mm-ddThh:mm:ss.sss-hh:mm                                                   | Current Timestamp. RFC 3339 (ISO 8601 derivative).                                               |
| visit_date       | Date         | yyyy-mm-dd                                                                      | Effective date of score                                                                          |
| alliance_id      | Text         | AlphaNumeric                                                                    | Return value provided by Feed                                                                    |
| risk_score       | AlphaNumeric | 9.99                                                                            | Currently expecting numeric, future may be phrased by stating an odds ratio with the risk score. |
| risk_score_notes | Text         | Additional notes (referral, remediation funds, etc to be returned to provider ) |                                                                                                  |

#### Sample Response

```json
{
    "risk_score": "0.309", 
    "risk_score_notes": "Risk Score Notes", 
    "visit_date": "2017-07-25", 
    "version": "0.0.1", 
    "alliance_id": 6425, 
    "timestamp": "2017-08-11 19:20:29"}
}
```

## Interpreting Risk Levels

Elevated lead levels has severe impacts on a child's mental and physical development. When the API identifies elevated blood-lead levels, doctors are highly encouraged to conduct further blood tests

!!! note "Follow-up after the blood test"
	If elevated lead levels are confirmed by subsequent blood testing, the family has multiple options when deciding how to mitigate potential sources of lead poisoning:

		* The City of Chicago has [limited grant funding](https://www.cityofchicago.org/city/en/depts/cdph/provdrs/inspections_and_permitting/svcs/apply_for_financialassistanceforleadabatement.html) to assist low-income homeowners and landlords of affordable housing to eliminate lead hazards.
		* Local non-profits, such as 
		* Families who rent their home from a landlord can also contact the City of Chicago for inspectors to inspect their homes for potential sources of lead poisoning. Families may dial 311 for further assistance.

## Terms and Conditions

Thou shalt not...


## Acknowledgements

The "Lead Safe" API was developed by the [Chicago Department of Public Health](https://www.cityofchicago.org/city/en/depts/cdph.html), [University of Chicago's Center for Data Science and Public Policy](http://dsapp.uchicago.edu/), and the [Chicago Department of Innovation and Technology](https://www.cityofchicago.org/city/en/depts/doit.html). This project was made possible by a grant from the [Robert Wood Johnson Foundation](http://www.rwjf.org/). 

[^1]: Potash _et al._ (2015) [Predictive Modeling for Public Health](ttps://dssg.uchicago.edu/wp-content/uploads/2016/01/p2039-potash.pdf). _Proceedings of the 21th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining_ pp. 2039-2047.