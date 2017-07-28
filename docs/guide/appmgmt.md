## Upload File into Running Pod

**1.	Select Project `oc project [PROJECT_NAME]`**

	$ oc project sop
	Now using project "sop" on server "https://lb.osh.telkom.co.id:8443".

**2. Get the pod name of deployed application `oc get pods`**

	$ oc get pods
	NAME            READY     STATUS    RESTARTS   AGE
	mysql-1-shblb   1/1       Running   0          1m

**3.	Upload file to selected pod `oc rsync [SOURCE_DIR] [POD_NAME]:[DESTINATION_DIR]`**

	$ oc rsync /home/source mysql-1-shblb:/tmp/destination
	Forwarding from 127.0.0.1:58021 -> 45705
	Forwarding from [::1]:58021 -> 45705
	Handling connection for 58021
	sending incremental file list
	created directory tmp/destination
	source/
	source/database.sql

	sent 450,501 bytes  received 76 bytes  180,230.80 bytes/sec
	total size is 450,274  speedup is 1.00

## Download File from Running Pod

**1. Select Project `oc project [PROJECT_NAME]`**

	$ oc project sop
	Now using project "sop" on server "https://lb.osh.telkom.co.id:8443".

**2. Get the pod name of deployed application `oc get pods`**

	$ oc get pods
	NAME            READY     STATUS    RESTARTS   AGE
	mysql-1-shblb   1/1       Running   0          1m

**3. Upload file to selected pod `oc rsync [POD_NAME]:[SOURCE_DIR] [DESTINATION_DIR]`**

	$ oc rsync mysql-1-shblb:/tmp/destination /home
	Forwarding from 127.0.0.1:58479 -> 50222
	Forwarding from [::1]:58479 -> 50222
	Handling connection for 58479
	receiving incremental file list
	destination/
	destination/source/
	destination/source/database.sql
	sent 53 bytes  received 450,498 bytes  180,220.40 bytes/sec
	total size is 450,274  speedup is 1.00