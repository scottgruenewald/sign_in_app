# sign_in_app
Unofficial Python API for the [Sign In App API](https://backend.signinapp.com/client-api/docs/1.0/overview).


 
 ## Create API object
```python
def create_api_obj():
	from sign_in_app.sign_in_app import sign_in_app
	
	#These options match up with the terminology of the Sign In App.
	#Once you've created your client, it should be straight forward.
	
	base_url="your_base_url"
	client_key="your_client_key"
	connection_name="your_connection_name"
	secret_key="your_secret_key"
	
	#Instructs which sites to look at. You will need to specify this.
	site_ids=[]

	#Instructs which user groups to look at. You will need to specify this.
	group_ids=[]

	#Create api object.
	api=sign_in_app(
		site_ids=site_ids,
		base_url=base_url,
		connection_name=connection_name,
		client_key=client_key,
		secret_key=secret_key,
		group_ids=group_ids
		)
	
	"""
	get_today iterates through the sites to retrieve all the visitors assigned to the group_ids specified above.
	A list of sign_in_app.user objects of all the users from the sites is retrieved.
	All datetime objects from the API come in UTC. The sign_in_app library will add localized datetimes to the user objects.
	"""
	visitors=api.get_today()

	print(visitors)
  ```
  
  
  ## Visitor Objects
  ### Once you've created an api object, you can call functions with it to return lists of visitor objects.
  ### The visitor object has these attributes available:
  
  ```python
  {
  #These are parent objects for the visitor object.
  'site': <sign_in_app.site object at 0x01EC62C8>, 
  'sign_in_app': <sign_in_app.sign_in_app object at 0x01EA0C10>, 
  
  #This is the data the API returns.
  'id': some_integer, #This is the id for the visit.
  'group_id': some_integer, 
  'returning_visitor_id': some_integer, #This is basically the user's ID.
  'name': 'Someone's Full Name', 
  'photo_url': None, 
  'badge_url': None, 
  'status': 'signed_in', 
  'in_datetime': '2021-04-29T13:39:57Z', 
  'out_datetime': None, 
  'expected_datetime': None, 
  'additional_fields': {"Question 1":"Answer", "Question 2", "Answer"}, 
  'role': None, 
  'email': 'somebody@domain.com', 
  'mobile': None, 
  'c3YQ5d9wQi': 'User's Department', 
  'fQHRUCmOKz': 'User's Job Title', 
  'rejected_sign_in': False, 
  
  #Custom fields added for convenience. Any suggestions, please get in contact.
  
  #In and Out times converted to your local timezone. You can specify this timezone if needed.
  'in_datetime_local': datetime.datetime(2021, 4, 29, 9, 39, 57, tzinfo=datetime.timezone(datetime.timedelta(days=-1, seconds=72000), 'Eastern Daylight Time')), 
  'out_datetime_local': None,  
  }
  
  ```
   
 ## Get Today's Visitors

 ```python
visitors=api.get_today()
for visitor in visitors:
	print(visitor.__dict__)
  ```
