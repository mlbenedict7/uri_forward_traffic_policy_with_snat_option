# uri_forward_traffic_policy_with_snat_option
AS3 declaration format for selecting SNAT option
I'm creating a URI Policy in AS3 and trying to use the SNAT option flags.  Can't find any documentation on how this should be laid out.  
Example declaration...
    "snat_test_policy": {
				"class": "Endpoint_Policy",
				"strategy": "first-match",
				"rules": [{
						"name": "snat_test_tcp_80",
						"conditions": [{
							"type": "httpUri",
							"path": {
								"operand": "starts-with",
								"values": [
									"/anything-api"
								]
							}
						}],
						"actions": [{
							"type": "forward",
							"event": "request",
							"snat": {
                  "enable": "true"
                      },
							"select": {
								"pool": {
									"use": "dummy_app_http_80_pool"
								    }
							    }
						    }]
					}]
                }
