<h1>PHP Application - WordPress</h1>

## Introduction
<p style="text-align:justify">
	This use case consists of PHP application and MySQL database. It shows how to connect application and database in OpenShift. It also show how to build PHP application in OpenShift using private Git project.
</p>
## Process

<div class="mxgraph" style="max-width:100%;border:1px solid transparent;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;resize&quot;:true,&quot;toolbar&quot;:&quot;zoom&quot;,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile userAgent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36\&quot; version=\&quot;6.9.7\&quot; editor=\&quot;www.draw.io\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;74e2e168-ea6b-b213-b513-2b3c1d86103e\&quot; name=\&quot;Page-1\&quot;&gt;3ZlLb6MwEMc/DcdWGEOAY5um7WF3FSlatT064IB3HYyM8+qnXxPM0yGNmle7OURmMsbj8c9/PMSAw/n6iaM0/slCTA3LDNcGfDAsy3Mt+Z0bNoXBNr3CEHESFiZQGybkHSujqawLEuKs5SgYo4KkbWPAkgQHomVDnLNV223GaHvUFEVYM0wCRHXrCwlFrKblmLX9GZMoLkcGpvpljkpnZchiFLJVwwRHBhxyxkTRmq+HmOa5K/NS9Hvs+bUKjONEHNLBwZ4P4GDmO4GPBq53o1YmE5tysjiUc1eXjIuYRSxBdFRb7zlbJCHO72jKq1jMqWwC2fyDhdio5UMLwaSpvsMPxlLlV4yZD9Q7DWXK2IIHyssNBw4AbhC4vm2bll/GLhCPsOjxgVWSJZyYzbHgG9mHY4oEWbbHRwqTqPKrMykbKpm7E9sX3BLRhRplIgMVeroplRjnaV3FROBJirbzXcmN1E4uytKC7RlZ58lXWVxiLvB6fx71+asOlusUXdTGhArTVU15CXncALy0HZMwnUT3lCjKBPDNa26/dcrLN+V2YUyhjqk2edCzTufnFGqcvjAejjnOMmmeFBOzzKHUdG19pJqleVNmBFGKKYs4mn9M8gnABV4bXGDp5FY0N9GF/jnQ9b+PimrBH4KneyE6+4Jr0DnkGImcyAck0BRlOpXtxJ6fxeqYUoroQGcReDtYtM8io943ZtE+gMVLPdH7gtvF4vh5LL/v0pSSQEbBkqtDCf02lJZ7TSjLHfItoXQPgNK/FpSuDiVLZiRa8LZGygf4tjb6Cmx2BdO2r8mmr2XwkSQki3Viq5N6ee4J2WJK8egrneCdHQehix3hAbzGNsdrIl4b7bcDSoATSQMo30bs0wb7SG1QXceMyNCqhXc6m8gadFa0iEn1qhf1jnO0abiluUPWPw60O+PAzhuGjr/t7vWXjSKCmrAqJ5+ETn8u/2Iah3KHiTZessIh72i6dciRUImQ3s694Tzk+5WSKJGGQDKBuTTkO1U+4Omd+mFOwnDLMEVTTO9R8Dfa0jxklPHtuHC2/ezb6+qllYrEqF4VNVns2Wm9qnBj3tqOp06CR4IGvXYPNptlWBhdnThyFa2rSofZkI6GWnwB8QDOWdQDdNXD7tziROoBYPvxdHY1sHQ1eMPZ/y4H1sdy4NqwtRJlOfNZkM4rB+XeaCzj74wkUV5rcbIsqq4nIvPxqK0tj9l8usiucpQF/oFHWe8stf9Jy6xaAlsCuNXDC5dgwLnUOatf4E6Kt6Ph3SzbcrAtczJ5zgNJQqPxHnaCA471fxEuXcINDni7sKvs+EQFJy/r/8eK5Nd/MsLRPw==&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>

## Prerequisite
<p style="text-align:justify">
	Prepare WordPress source code. Update the database configuration in `wp-config.php` file using environment variable. User can define variables for `DB_NAME`, `DB_USER` and `DB_PASSWORD` environment variables with arbitrary string. Set `DB_HOST` variable depend on the database service name using format `[DATABASE_SERVICE_NAME]_SERVICE_HOST`. For instance if user create database with service name `MYSQL`, DB_HOST have to set environment variable as `MYSQL_SERVICE_HOST`.
</p>
*example*

	define('DB_NAME', getenv('DB_NAME'));

	/** MySQL database username */
	define('DB_USER', getenv('DB_USER'));

	/** MySQL database password */
	define('DB_PASSWORD', getenv('DB_PASSWORD'));

	/** MySQL hostname */
	define('DB_HOST', getenv('MYSQL_SERVICE_HOST'));
	
<p style="text-align:justify">
	The WordPress source code have to publish in Git repository which reachable from OpenShift and vice versa.
</p>

## Process Detail

<table>
	<thead>
		<tr>
			<th>Process</th>
			<th>Description</th>
		<tr>
	</thead>
	<tbody>
		<tr>
			<td>Configure Git SSH and Source Secret</td>
			<td>
				This process require <a href="../../guide/tutorial/#create-ssh-keys-in-linux">generate SSH keys</a>. Then
				<a href="../../guide/tutorial/#add-public-key-in-gitlab-repository">set the SSH in Git Repository</a> using the public key. Finally <a href="../../guide/config/#setting-source-secrets">create Source Secrets</a> using private key.
			</td>
		</tr>
		<tr>
			<td>Create PHP Application</td>
			<td>
				If the WordPress Source Code using private Git Repository, <a href="../../guide/newapp/#create-new-application-with-private-git-repository">specify Source Secret</a>. Otherwise just <a href="../../guide/newapp/#create-new-application-from-catalog">create the application.</a>
			</td>
		</tr>
		<tr>
			<td>Create Database</td>
			<td>
				Take a look to <a href="../../guide/newapp/#create-new-database">this guide</a> to create database in OpenShift. 
			</td>
		</tr>
		<tr>
			<td>Configure Database Connection</td>
			<td>
				<a href="../../guide/config/#setting-environment-variables">Set the required environment variables</a> in the PHP application. This case needs DB_NAME, DB_USER and DB_PASSWORD environment to set using name, username and password respectively of the database.
			</td>
		</tr>
	</tbody>
</table>

## References

* [Create SSH Keys in Linux](../../guide/tutorial/#create-ssh-keys-in-linux)
* [Add Public Key in GitLab Repository](../../guide/tutorial/#add-public-key-in-gitlab-repository)
* [Setting Source Secrets](../../guide/config/#setting-source-secrets)
* [Create New Application With Private Git Repository](../../guide/newapp/#create-new-application-with-private-git-repository)
* [Create New Application From Catalog](../../guide/newapp/#create-new-application-from-catalog)
* [Create New Database](../../guide/newapp/#create-new-database)
* [Setting Environment Variables](../../guide/config/#setting-environment-variables)