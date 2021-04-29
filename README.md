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
  ### When you use the sign_in_app library, 
  
  
  
  
  
  ## Get Today's Visitors
 
 ```python
visitors=api.get_today()
for visitor in visitors:
	print(visitor.__dict__)
  ```
  

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
