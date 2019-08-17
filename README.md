This program finds the input for a given SOAP api from wsdl recursively and sets the input data as it matches. This way we dont create new methods to call each apis.




# SymcResellerSoapAPI
Dependency:

pip install requests
pip install suds
Usage:
```python
#for unit testing the functions
import os
from resellerAPIs import resellerSoapAPIs as r
wsdl = 'file:///' +  os.path.abspath("./query.jws.xml")
#wsdl = 'https://api.ws.symantec.com/webtrust/query.jws?WSDL'
# parameters to the below function call need not be in the same sequence
h = r.TestApi(wsdl,
    'GetOrderByPartnerOrderID',
    UserName='username',
    password='password',
    partnercode='partnercode',
    PartnerOrderID='parterorderid',
    ReturnProductDetail=True,
    ReturnContacts=True,
    criterion = [1,2])
h.process_soap_request()
h.validate_and_capture_response_data(
    returncount=0,
    successcode=0)
h.print_relevant_data()
```
