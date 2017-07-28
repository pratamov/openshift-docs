<h1>Java Web Application</h1>

## Introduction
<p style="text-align:justify">
	This use case shows how to deploy Java web application in OpenShift. This section covers how to setting WebHook, autoscaler and also setting SSL router. 
</p>
<p style="text-align:justify">
	Most of the cases, OpenShift uses Git as repository to obtain the source in application. OpenShift capable to automatically update the deployed applications immediately after the Git repository updated. User have to set the WebHook to enable the feature.
</p>
<p style="text-align:justify">
	OpenShift provides autoscaling feature to let the applications obtain resource depend on it's load. OpenShift adjust the memory and CPU based on the application's load. 
</p>
<p style="text-align:justify">
	When user deploy web application in OpenShift it is going to obtain a URL to expose the interface. The URL is HTTP by default. User can create SSL router when they wish.
</p>
## Process

<div class="mxgraph" style="max-width:100%;border:1px solid transparent;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;resize&quot;:true,&quot;toolbar&quot;:&quot;zoom&quot;,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile userAgent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36\&quot; version=\&quot;6.9.7\&quot; editor=\&quot;www.draw.io\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;178d4bf7-2678-c851-30b0-abed46fd7ce3\&quot; name=\&quot;Page-1\&quot;&gt;5VrRkqI4FP0aH3uKJID42O1079RW79bUWFuz8xglIjuRUCG0Ol+/CQQxBmxbRdqefuiCaxKSe8/JPRcyQOPl+g+O08VfLCR0AJ1wPUCfBxAGQyj/K8OmNLhOUBoiHoelCdSGSfyLaKOjrXkcksxoKBijIk5N44wlCZkJw4Y5Zyuz2ZxR86kpjohlmMwwta3f41As9LI8p7Z/IXG0qJ4MHP3LEleNtSFb4JCtdkzocYDGnDFRXi3XY0KV7yq/lP2eWn7dToyTRBzTAQbBbBgMZz6YTR3XI3d6hExsqsWSUK5d3zIuFixiCaaPtfWBszwJiRrRkXcLsaTyEsjL/4gQGx0+nAsmTfUIz4ylul35TPWg1mVU82I5n+lW/tQd+XiOfOSOMCSomrvAPCKipQ3cOlmCk7AlEXwj+3BCsYhfzOdjDZNo2672pLzQzmx2bNvkXjDN9VMmcqLCdjelEsbKratFLMgkxcV6V5JIpnNxlpbYnsdr5XztxRfCBVkf9qO9ft0BeW7ZRRMTaZiuapRXIF/sALyyneMwC4nohpEIbSRa6+sNidBC4p/4BUvLpFwSdMZyw7a8L7eqVF1KX2BKCWURx8vXYXoBVMJhYKASQBuW0IE2Lt0ucOndDi6bMfcKLt0r4bJtcju4HHOChQLk95iGc6qmcZ+mNJ7JmbDEioPp5WvgcmTgEjo2LsFodCVcBn3gkqxj8a/urq5/qOtP3uUQ6x6BWP9MxBZd7znHm50GKYsTke2M/FUZ6uCDkbkpIVNpyYtyxDqY26mdFt+RRY8fJLNiLtEszFByksW/8LRooMKkFyZbew8D77NSEjSOEmmYycgQLg2KFZJk9F7/sIzDsMALxVNCH/DsZ1QgZ8wo48Vz0bz4O8QrLcb1TAZbCbyLiGZQtxLwzvnkBkO9Ib8t3HU8qyZsPs+IsCh4ZtSAf8Pp4hjyAa+vfAGGFiP+Zh+dEKBls6sZ4bju3s70nvnhWjH8SnFSFOVc/c9FzpUCyNNQSQH0ZGf9BVtO86wXJQqDJiUK7IwfdJHxwUVTvnQB32xzubqpk/mb5UDRqxIEF9yR/GvsSCfqAd+Ahut2rAd8izkTGaU4iZReJtMvjP20uXJlhQyA6RTkNyhkv+GNQicKefvSrReJDAYdSWTgHUOKUR+k8HxwXVJAO5/8Bip559VxiyjwjDBUpfb7lARw1E1aK3PSNrFdX04fRVQ4PJOop79wdSzufHw9DVv2RT20lNNwT0674DzyVKRE5rB37t4QHdWjnhXkx6RwGXT++fZcpGaZmaEzmTz3r7aHpucb3q9Bx7XVQydqG8Je1MOB7etS29LoGttSm0BARoh9sBe6clK6Vx29twsR8zmev/dddK89CsCh9pcXLsB+vVfLecVF6Hxjudo9+9b07p5r3IYaGPgNrOxE0yP3vYmFzmtgeEwRjOAl+Pr2Ihga2Bi+kWbDrmkG7ap5zJJ5HJVvme5lXDOpSwra9V07O2b28xt5dq2vS+iGDoa0JK/XMty5n5FO960Nyt+gaEWH4S+LVt9F5nGUd122ohs6sHIaQ87OKaczxK5aPn5pWgLqUGkKkJk+K7qcW5rCvdK0gnbH733s73m7uRnv5Oa+C9MqFVfVQXXIo5fPQAhafnuKkzhb2PvR9mxhdZgrZLnE5GO/Zw7NbwRBQ5V/oUOH8rY+WltCtj6fjB7/Bw==&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>

## Prerequisite
<p style="text-align:justify">
	Java web application source code in OpenShift have to [Mavenized](https://maven.apache.org/what-is-maven.html). The project have to specify <b>openshift</b> profile in the <b>pom.xml</b> as follows
</p>

		...
		<profiles>
		....
			<profile>
				<id>openshift</id>
				<build>
					<plugins>
						<plugin>
							<artifactId>maven-war-plugin</artifactId>
							<configuration>
								<failOnMissingWebXml>false</failOnMissingWebXml>
								<outputDirectory>deployments</outputDirectory>
								<warName>ROOT</warName>
							</configuration>
						</plugin>
					</plugins>
				</build>
			</profile>
		</profiles>
	</project>


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
			<td>Create WildFly Application</td>
			<td>
				WildFly is an application server to implements Java application. WildFly available as default image in OpenShift catalog. See <a href="../../guide/newapp/#create-new-application-from-catalog">this guide to create application.</a>
			</td>
		</tr>
		<tr>
			<td>Setting WebHook</td>
			<td>
				Take a look <a href="../../guide/config/#configure-git-webhook">this guide</a> to set the WebHook.
			</td>
		</tr>
		<tr>
			<td>Setting SSL Router</td>
			<td>
				SSL Router require SSL certificate. User can <a href="../../guide/tutorial/#create-self-signed-ssl-in-linux">generate self-signed SSL</a>. <a href="../../guide/config/#setting-application-router-https">This guide</a> shows how to set SSL application router given SSL certificate.
			</td>
		</tr>
		<tr>
			<td>Configure Autoscaling</td>
			<td>
				See <a href="../../guide/config/#configure-autoscaling">this guide</a> to configure autoscaling in the application.
			</td>
		</tr>
	</tbody>
</table>

## References

* [Create New Application From Catalog](../../guide/newapp/#create-new-application-from-catalog)
* [Configure Git Webhook](../../guide/config/#configure-git-webhook)
* [Create Self Signed SSL in Linux](../../guide/tutorial/#create-self-signed-ssl-in-linux)
* [Setting Application Router HTTPS](../../guide/config/#setting-application-router-https)
* [Configure Autoscaling](../../guide/config/#configure-autoscaling)