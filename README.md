# Device-DA-Admin
This sample app displays DA device information like type, polled item count, life cycle status and date, contact status, 
poll status along with the last poll date of availability in a table view:
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

Please review the PDF document within the package for more information and installation hints.
