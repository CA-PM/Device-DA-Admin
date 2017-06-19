# Device-DA-Admin
Sample CA PC app to display DA device information and trigger some actions

This sample app displays DA device information like type, polled item count, life cycle status and date, contact status, poll status along with the last poll date of availability in a table view:
	- for all devices (within the query limit) in the given group context and across the given timerange
	- single or multiple (using CTRL key) table rows can be selected by click, or by buttons "select all" / "select none"
	- following actions can be triggered on the selected devices via button
		- change polling status (ON > OFF and OFF > ON)
		- rediscover
		- update all metric families
		- delete device (with pop up window to confirm)
	- the action type will be displayed in the action column
	- the table does not refresh automatically
	- the CSV button exports the table content to csv file.
	
	The app  
	- uses CA PM OpenAPI to query devices with max availability timestamp
	- uses DA REST calls to retrieve other parameters like device type, contact and poll status and other webservices for administrative actions
	- uses DataTables javascript object, see https://datatables.net/examples/basic_init/zero_configuration.html 
	- has to live in CA PC app or browser view (running in a browser directly will cause problem due to cross-site scripting)
	- uses CA PC redirector URL that opens the device context page in new browser tab (new 3.1 functionality)
	- provides access only to users with administrator role. Users other than admin need to be enabled for DA REST access in CA PC (see https://communities.ca.com/docs/DOC-231174750-ca-pc-apps-and-user-authorization)
	
	Prerequisites:
	- CA PM 3.1
	
	CA PC App View parameters:
	URL: /pc/apps/user/DeviceDAAdmin/DeviceDAAdmin.html?id={ItemIdDA}&startTime={TimeStartUTC}&endTime={TimeEndUTC}&userrole={UserRoleName}&limit=100
	which consists of
		id={ItemIdDA}				dashboard context (group ID)
		startTime={TimeStartUTC}	dashboard context (start time)
		endTime={TimeEndUTC}		dashboard context (end time)
		userrole={UserRoleName}		user context. the app will only initialize if the role is Administrator
		limit=100					query limit: the number of rows retrieved
	Height: 600
	
	NOTE: this sample app is not designed for massive updates. The DA REST calls are individual per device
	
	last update:
	v1.0	June 16, 2017	Lutz Holzbecher, CA

Installation
	1. store DeviceDAAdmin.zip on your workstation
	2. under CA PC Administration -> App Deployment, select the zip archive and install it.
	3. in dashboard editor select single column layout and create an App View (under External Links) and select "Device DA Admin" in the drop down. Save your work.
