### POC using Apigee ###


### Weather Console ###

Creating console for Weather on Apigee Togo

**Create Console**

* Configure Console Name & URL

![](images/api-console-name.png)

* Set Credentials

![](images/api-console-credentials.png)

* Create WADL File

```
<application xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xmlns:xsd="http://www.w3.org/2001/XMLSchema"
             xmlns:apigee="http://api.apigee.com/wadl/2010/07/"
             xmlns="http://wadl.dev.java.net/2009/02"
             xsi:schemaLocation="http://wadl.dev.java.net/2009/02 http://apigee.com/schemas/wadl-schema.xsd http://api.apigee.com/wadl/2010/07/ http://apigee.com/schemas/apigee-wadl-extensions.xsd">
    <resources base="http://portalcity-prod.apigee.net">
        <resource path="/woeid/v1/search">
            <param name="q" required="true" type="xsd:string" style="query" default="Singapore">
                <doc>Location</doc>
            </param>
            <method id="search" name="GET" apigee:displayName="woeid search">
                <apigee:tags>
                    <apigee:tag primary="true">Weather</apigee:tag>
                </apigee:tags>
                <apigee:authentication required="true"/>
                <doc apigee:url="http://portalcity-prod.apigee.net/doc/weoid/search">
                    WOEID code search of a location
                </doc>
            </method>
        </resource>
        <resource path="/weather/v1/forecast">
            <param name="w" required="true" type="xsd:string" style="query" default="23424948">
                <doc>woeid</doc>
            </param>
            <param name="u" required="true" type="xsd:string" style="template" default="c">
                <doc>units</doc>
                <option value="c" />
                <option value="f" />
            </param>
            <method id="forecast" name="GET" apigee:displayName="weather forecast">
                <apigee:tags>
                   <apigee:tag primary="true">Weather</apigee:tag>
                </apigee:tags>
                <apigee:authentication required="true"/>
                <doc apigee:url="http://portalcity-prod.apigee.net/doc/weather/forecast">
                    Weather forecast for the location
                </doc>
            </method>
        </resource>
    </resources>
</application>
```

* Upload WADL file

![](images/api-console-wadl-upload.png)

* Open Console (click on `Preview WADL in console`)

![](images/api-console-preview.png)

* Get Embed Code


```
<iframe src="https://apigee.com/madhav.maharjan/embed/console/portalcity" width="100%" height="600" scrolling="no"></iframe>
```
