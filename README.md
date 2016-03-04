# laravel-web.config

Para instalar laravel en Windows los siguientes pasos.

  1) dar permisos todos a las siguientes carpetas:
    .vendor
    .storage
    .bootstrap/cache
    
  2) el web.config dejarlo de la siguiente manera
  
  <?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <defaultDocument>
            <files>
                <clear />
                <add value="Default.htm" />
                <add value="Default.asp" />
                <add value="index.htm" />
                <add value="index.html" />
                <add value="iisstart.htm" />
                <add value="index.php" />
                <add value="default.aspx" />
            </files>
        </defaultDocument>
        <handlers accessPolicy="Read, Execute, Script">
        </handlers>
        <rewrite>
            <rules>
                <rule name="Imported Rule 3" stopProcessing="true">
                    <match url="^(.*)$" ignoreCase="false" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" ignoreCase="false" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" ignoreCase="false" negate="true" />                     
                    </conditions>
                    <action type="Rewrite" url="public/index.php/{R:1}" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
