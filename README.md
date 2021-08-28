# mysite
"UserData": {
					"Fn::Base64": {
						"Fn::Join": [ "", [
							"#!/bin/bash -ex\n",
							"yum install -y aws-cfn-bootstrap\n",
							"/opt/aws/bin/cfn-init -v ",
							" --stack ", {"Ref": "AWS::StackName"},
							" --resource WebServerInstance ",
							" --configsets config01 ",
							" --region ", {"Ref": "AWS::Region"}, "\n"
						]]
					}	
          
          
          "Install": {
						"packages": {
							"yum": {
								"httpd": []
					  		}
						},
						"sources": {
							"/var/wwww/html": "https://github.com/pbseo72/mysite/tarball/main"
						},
						"services": {
							"sysvinit": {
								"httpd": {
									"enabled": "true",
									"ensureRunning": "true"
