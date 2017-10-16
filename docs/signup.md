<form method="POST" action="http://formspree.io/developers@cityofchicago.org">
  <p>Please select from one of the eligible health networks:</p>
  <select name="health-network">
  <option value="Advocate Christ Medical Center">Advocate Christ Medical Center, 4440 West 95th Street</option>
  <option value="Advocate Illinois Masonic Medical Center">Advocate Illinois Masonic Medical Center, 836 West Wellington</option>
  <option value="Advocate Trinity Hospital">Advocate Trinity Hospital, 2320 East 93rd Street</option>
  <option value="Ann &amp; Robert H. Lurie Children's Hospital of Chicago">Ann &amp; Robert H. Lurie Children's Hospital of Chicago, 225 E. Chicago Avenue</option>
  <option value="Holy Cross Hospital">Holy Cross Hospital, 2701 West 68th Street</option>
  <option value="Jackson Park Hosp. Foundation">Jackson Park Hosp. Foundation, 7531 Stony Island Avenue</option>
  <option value="John H. Stroger Hospital of Cook County">John H. Stroger Hospital of Cook County, 1901 West Harrison Street</option>
  <option value="LaRabida Children's Hospital">LaRabida Children's Hospital, 6501 S. Promontory Drive</option>
  <option value="Little Company of Mary Hospital and Health Care Centers">Little Company of Mary Hospital and Health Care Centers, 2800 West 95th Street</option>
  <option value="Loretto Hospital">Loretto Hospital, 645 South Central Avenue</option>
  <option value="Louis A. Weiss Memorial Hospital">Louis A. Weiss Memorial Hospital, 4646 North Marine Drive</option>
  <option value="Mercy Hospital &amp; Medical Center">Mercy Hospital &amp; Medical Center, 2525 South Michigan Avenue</option>
  <option value="Methodist Hospital of Chicago">Methodist Hospital of Chicago, 5025 North Paulina Street</option>
  <option value="Mount Sinai Hospital Medical Center">Mount Sinai Hospital Medical Center, 2750 W. 15th Street</option>
  <option value="Northwestern Memorial Hospital">Northwestern Memorial Hospital, 211 East Ontario</option>
  <option value="Norwegian American Hospital">Norwegian American Hospital, 1044 North Francisco Avenue</option>
  <option value="Presence Our Lady of the Resurrection Medical Center">Presence Our Lady of the Resurrection Medical Center, 5645 West Addison Street</option>
  <option value="Presence Resurrection Medical Center">Presence Resurrection Medical Center, 7435 West Talcott Avenue</option>
  <option value="Presence Saint Francis Hospital">Presence Saint Francis Hospital, 355 Ridge Avenue</option>
  <option value="Presence Saint Joseph Hospital Chicago">Presence Saint Joseph Hospital Chicago, 2900 North Lake Shore Drive</option>
  <option value="Presence Saint Mary Of Nazareth Hospital">Presence Saint Mary Of Nazareth Hospital, 2233 West Divison Street</option>
  <option value="Presence St. Elizabeth's Hospital">Presence St. Elizabeth's Hospital, 1431 North Claremont</option>
  <option value="Provident Hospital of Cook County">Provident Hospital of Cook County, 500 East 51st Street</option>
  <option value="Roseland Community Hospital">Roseland Community Hospital, 45 West 111th Street</option>
  <option value="Rush University Medical Center">Rush University Medical Center, 1653 West Congress Parkway</option>
  <option value="Shriners Hospitals for Children - Chicago">Shriners Hospitals for Children - Chicago, 2211 North Oak Park</option>
  <option value="South Shore Hospital, Corp.">South Shore Hospital, Corp., 8012 South Crandon Ave.</option>
  <option value="St. Anthony Hospital">St. Anthony Hospital, 2875 West 19th Street</option>
  <option value="St. Bernard Hospital">St. Bernard Hospital, 326 West 64th Street</option>
  <option value="Swedish Covenant Hospital">Swedish Covenant Hospital, 5145 North California Avenue</option>
  <option value="Thorek Memorial Hospital">Thorek Memorial Hospital, 850 West Irving Park Road</option>
  <option value="University of Chicago Medical Center">University of Chicago Medical Center, 5841 South Maryland</option>
  <option value="University of Illinois Medical Center at Chicago">University of Illinois Medical Center at Chicago, 740 West Taylor Avenue</option>
</select>
  <p>Please provide information on the lead clinical contact:</p>
  <input type="text" name="clinical-point-of-contact" placeholder="Clinical Point of Contact">
  <input type="text" name="clinical-title" placeholder="Clinical Title">
  <input type="text" name="national-provider-identifer" placeholder="National Provider Identifier">
  <input type="text" name="illinois-physician-license" placeholder="Illinois Physician License">
  <input type="text" name="clinical-address" placeholder="Clinical contact address">
  <input type="tel" name="clinical-telephone" placeholder="Clinical telephone number">
  <input type="_replyto" name="clinical-email" placeholder="Clinical email address">
  <p>Please provide contact information for the technical advisor:</p>
  <input type="text" name="technical-point-of-contact" placeholder="Technical Point of Contact">
  <input type="text" name="technical-title" placeholder="Technical Title">
  <input type="text" name="technical-address" placeholder="Technical contact address">
  <input type="tel" name="technical-telephone" placeholder="Technical telephone number">
  <input type="email" name="technical-email" placeholder="Technical email address">
  <input type="checkbox" name="eligibility-criteria" value="certifies-eligibility">I have read the <a href="#">eligibility criteria</a> and certify that this institution meets the minimum standards.
  <br />
  <p>I have read the <a href="#">Terms of Service:</a></p>
  <input type="radio" name="terms-of-service" value="accepts-terms-of-service">I accept the Terms of Service<br />
  <input type="radio" name="terms-of-service" value="rejects-terms-of-service">I do not accept the Terms of Service<br />
  <textarea name="message" placeholder="Leave any other note"></textarea>
  <button type="submit">Send</button>
  <input type="hidden" name="_subject" value="Test submission: Lead Safe API Request" />
</form>