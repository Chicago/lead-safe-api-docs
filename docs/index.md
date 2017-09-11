"Lead Safe" is an API available to Chicago-area hospital and health networks to provide estimates on a child's potential exposure to elevated lead levels from household paint. Health network providers can provide information on the patient's demographics, address, and history on their past visits and blood-lead levels, the Lead Safe API will provide an estimate on the chance of elevated, unsafe blood-lead levels for children under 4 years-old.

The API uses a predictive model developed by the University of Chicago[^1] that uses historical blood-lead level testing conducted by the State of Illinois. Data submitted through this API and subsequent testing conducted will improve the accuracy of the model, allowing for a more effective use of blood tests to prevent elevated lead levels.

## Obtaining Access

### Eligibility

To access the API, fill out [this form](#) to be contacted by the Chicago Department of Public Health. The city will need to verify your eligiblity as an area health provider.

### Accessing API

In order to integrate with Lead Safe, the health provider will need to make a REST call against the API. To do so, they will be provided an API token which will provide some authentication. The city will also need to "whitelist" the IP address(es) of the health providers servers.

## API

### Submitting Prediction
 
Submit a patient record and retrieved the estimated probability of having elevated blood-lead levels.

```bash
POST {json file} <url>/insert/
```

| Field           | Format   | Constraints                                                | Notes/Questions                                                                                                   |
|-----------------|----------|------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| timestamp       | TimeDate | yyyy-mm-dd hh:mm:ss.sss-hh:mm                              | Current Timestamp. RFC 3339 (ISO 8601 derivative).                                                                |
| visit_date      | Date     | yyyy-mm-dd                                                 | Effective date of score                                                                                           |
| network_id      | Text     |                                                            | The parent entity of the submitting organization                                                                  |
| clinic_id       | Text     |                                                            | Two Characted Organization ID (NN- NearNorth  EF- ErieFamily)                                                     |
| location_id     | Text     |                                                            | Specific Location Abbreviation in Centricity                                                                      |
| patient_id      | Text     | AlphaNumeric                                               | A id to identify individual patients, should be unique with secondary key.                                        |
| address1        | Text     | Address number, street direction, street name, street type | Patientprofile.address1                                                                                           |
| address2        | Text     | Additional address information, e.g. apartment number      | patientprofile.address2                                                                                           |
| city            | Text     |                                                            | patientprofile.city                                                                                               |
| state           | Text     |                                                            | patientprofile.state                                                                                              |
| zip             | Text     | 5 digit zip code                                           | patientprofile.Zip                                                                                                |
| date_of_birth   | Date     | yyyy-mm-dd                                                 |                                                                                                                   |
| gender          | Text     | M/F/U                                                      |                                                                                                                   |
| race            | Text     | Code Values from Centricity                                | Standard ONC Race definitions <br> <br> **Code / description** <br> 1002-5 / American Indian or Alaska Native <br> 2028-9 / Asian <br> 2054-5 / Black or African American <br> 2076-8 / Native Hawaiian or Other Pacific Islander <br> 2106-3 / White <br> UNK / Unknown |
| ethnicity       | Text     | Code Values from Centricity                                | Standard ONC Ethnicity definitions <br> <br> **Code / description** <br> 2135-2 / Hispanic or Latino <br> 2186-5 / Non Hispanic or Latino <br> UNK / Unknown |
| Visit Array     |          |                                                            |                                                                                                                   |
| visit.visit_id  | Numeric  | 16 Digit GE ID                                             | Unique GE ID for specific visit  (DocumentID)                                                                     |
| visit.date      | Date     | yyyy-mm-dd hh:mm:ss.sss-hh:mm                              | RFC 3339 (ISO 8601 derivative).                                                                                   |
| visit.location  | Text     |                                                            | Text Abbreviation for facility of visit location                                                                  |
| visit.provider  | Text     |                                                            | Full provider name, last name, or just NPI                                                                        |
| Lab Array       |          |                                                            |                                                                                                                   |
| lab.lab_id      | Numeric  | 16 Digit GE ID                                             | Unique GE ID for specific lab result (ObsID)                                                                      |
| lab.type        | Text     | BLL                                                        | Static BLL unless we identify additional labs to include                                                          |
| lab.date        | Date     | yyyy-mm-dd                                                 |                                                                                                                   |
| lab.sample_type | Text     | "V" or "C"                                                 | "V" Veinous or "C" for Capillary                                                                                  |
| lab.result      | Text     |                                                            | Several values are possible; integer, non-integer numeric, ranges indicated by alphanumeric text.  We'll use previous examples to essentially construct a dictionary. |

```json
{
  "timestamp": "2017-08-22 12:00:00.000-00:00", 
  "clinic_id": "EF",
  "location_id": "examp_loc",
  "patient_id": 9000, 
  "address1": "333 S State St", 
  "address2": "Ste 420", 
  "city": "Chicago", 
  "state": "IL", 
  "zip": "60653", 
  "date_of_birth": "2013-07-24", 
  "gender": "F", 
  "race": "2054-5", 
  "ethnicity": "2186-5",
  "visit": [
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"},
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"}, 
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"}, 
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"}, 
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"}, 
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"}, 
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"}, 
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"}, 
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"}, 
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"}, 
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"}, 
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"}, 
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"}, 
    {"date": "2017-07-25 15:02:54.171-0:00", "visit_id": 1234567891011121, "location": "333 S State St", "provider": "John Doe"}
  ],
  "lab": [
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 5.0, "result": "None Detected ug/dL", "date": "2016-07-29", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 5.0, "result": "1", "date": "2015-08-21", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 5.0, "result": "1", "date": "2015-02-27", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 5.0, "result": "1", "date": "2014-06-06", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 1.0, "result": "3", "date": "2014-09-29", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 1.0, "result": "4.1", "date": "2014-01-09", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 1.0, "result": "4.1", "date": "2013-06-28", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 1.0, "result": "6.3", "date": "2013-03-13", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 1.0, "result": "9.7", "date": "2012-10-02", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 1.0, "result": "16.3", "date": "2012-06-19", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 1.0, "result": "3", "date": "2016-09-16", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 1.0, "result": "3", "date": "2015-12-15", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 1.0, "result": "3", "date": "2015-06-09", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 1.0, "result": "13.6", "date": "2012-03-20", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 1.0, "result": "15", "date": "2012-02-21", "type": "BLL"}, 
    {"lab_id": 1234567891011121, "route": "V", "healthcenterid": 1.0, "result": "5", "date": "2011-08-19", "type": "BLL"}] 
}
```

### Response

#### Body

| Field            | Format       | Constraints                                                                     | Notes/Questions                                                                                  |
|------------------|--------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| version          | Text         | "0.2.1"                                                                         | Follows Semantic Versioning 2.0.0 http://semver.org/spec/v2.0.0.html                             |
| timestamp        | TimeDate     | yyyy-mm-ddThh:mm:ss.sss-hh:mm                                                   | Current Timestamp. RFC 3339 (ISO 8601 derivative).                                               |
| visit_date       | Date         | yyyy-mm-dd                                                                      | Effective date of score                                                                          |
| patient_id       | Text         | AlphaNumeric                                                                    | Return value provided by Feed                                                                    |
| risk_score       | AlphaNumeric | 9.99                                                                            | Currently expecting numeric, future may be phrased by stating an odds ratio with the risk score. |
| risk_score_notes | Text         | Additional notes (referral, remediation funds, etc to be returned to provider ) |                                                                                                  |

```json
{
    "version": "0.3.0", 
    "timestamp": "2017-08-11 19:20:29.000-00:00", 
    "visit_date": "2017-07-25", 
    "patient_id": 6425, 
    "risk_score": "0.309", 
    "risk_score_notes": "Risk Score Notes"
}
```

#### Header

| Field            | Format       | Constraints      |                                                                                             |
|------------------|--------------|------------------|---------------------------------------------------------------------------------------------|
| Date             | Integer      | N/A              | ID of the record submitted.                                                                 |
| Server           | Text         | "Apache"         | The type of the server providing the results                                                |
| Content-Location | URL          |                  | Pernament location to retrieve the results                                                  |
| ETag             |              |                  |                                                                                             |
| Content-Length   | Integer      | 225              |                                                                                             |
| Content-Type     | Text         | application/json | Informs user that the content will be a JSON file                                           |
| Set-Cookie       | Text         |                  |                                                                                             |

```
HTTP/1.1 200 OK
Date: Tue, 22 Aug 2017 22:49:39 GMT
Server: Apache
Content-Location: https://webapps1int.cityofchicago.org/ords/cdph_lead_api/test_result/get/406
ETag: "zi/wQ5GvoQFjvb4ej24v8f5PbHog14ZsjDSGJABXUxKxV3SxyOwBKrNJv7we9B5hnSs9WgeoA2h54/yVmIjcnA=="
Content-Length: 225
Content-Type: application/json
Set-Cookie: BIGipServerwebapps1int.cityofchicago.org-443.app~webapps1int.cityofchicago.org-443_pool=339105802.47873.0000; Secure; HttpOnly; path=/; Httponly; Secure
```


### Retrieving Previous Predictions

When submitting a record for a prediction, a unique URL is given to the submission (not the individual) where the results can be retrieved in the future. 

```bash
GET <url>/get/{id}
```

The response will be the [same as the original prediction](#body).

!!! note ""
    The prediction is only assigned when it is POST to the server. The score will only reflect the prediction given the data originally submitted and based on known information at that time. Retrieving old records will not update the prediction. To get a new prediction, submit a new record


### Checking Status on All Submissions

Check the status on all submissions and whether results are available.

```bash
GET <url>/get/
```

##### Response

| Field       | Format       | Constraints    | 
|-------------|--------------|----------------|--------------------------------------------------------------------------------------------------|
| id          | Integer      | N/A            | ID of the record submitted.                                                                      |
| processed   | Text         | "Y" or "N"     | Whether the results are available. Results may be an error or blank if the record was incorrect. |

```json
{"items":[
  {"id":133,"processed":"Y"},
  {"id":121,"processed":"Y"},
  {"id":120,"processed":"Y"},
  {"id":122,"processed":"Y"},
  {"id":123,"processed":"Y"}
  ]
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