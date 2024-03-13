# Multitenant-Notification-API-Workflow


## Case 1: Create a multi-tenant incidents notification profileREQUEST: POST /api/sase/v2.0/resource/custom/query/remotenetworks/rn_list
ENDPOINT: "https://api.sase.paloaltonetworks.com/mt/notifications/v1/profiles"REQUEST HEADERS:
	User-Agent: python-requests/2.28.2 (PRISMA SASE SDK v6.1.2b1)
	Accept-Encoding: gzip, deflate
	Accept: application/json
	Connection: keep-alive
	authorization: Bearer exxxxxxxxxxxxxxxxxxxxxx
	X-PANW-Region: americas        <<<<<<<<<<<<<<<<<<<<<< PANW Region 
	prisma-tenant: xxxxxxxxx       <<<<<<<<<<<<<<<<<<<<<< TSG ID of the tenant
	Content-Type: application/json
	Content-Length: 348
REQUEST BODY:


data = {
    "profileName": "Tunnel-state-notification-profile",
    "tenantList":
    [
        "13xxxxxxxx",
        "16xxxxxxxx"
    ],
    "description": "Profile for notifications on tunnel state down,flap",
    "excludeTenantList": [],   <<<<<<<<<<<<<<<<<   List of TSG IDs to be excluded.
     "notifChannels":
    [
        {
            "name": "NOC-US-admin",
            "type": "WEBHOOK",
            "webhookChannelDetails":
            {
                "urls":
                [
                    "https://webhook.site/ce5d0687-0175-42b0-9d3a-c4423bb97799",
                    
                ],
                "authType": "NO_AUTH",
            }
        },
        {
            "emailChannelDetails":
            {
                "emails":
                [
                    {
                        "emailId": "xxxxxxx@gmail.com",
                        "name": "NOC-US-admin"
                    }
                ]
            },
            "name": "NOC-admin-US",
            "type": "EMAIL"
        }
    ],
    "notifTypeDetails": [
            
                {
                "notifCategoryList": [
                    {
                        "bestPractice": False,
                        "name": "RN",
                        "subCategoryList": [
                            {
                                "bestPractice": False,
                                "name": "INC_RN_ECMP_TUNNEL_DOWN"
                            },
                            {
                                "bestPractice": False,
                                "name": "INC_RN_SECONDARY_WAN_TUNNEL_RTT_EXCEEDED_BASELINE"
                            },
                            {
                                "bestPractice": False,
                                "name": "INC_RN_ECMP_BGP_DOWN"
                            }
                        ]
                    }
                ],
                "type": "INCIDENTS"
            }
        ],
    "opState": "ENABLED",
}


RESPONSE DATA:
{
    "data": {
        "description": "Profile for notifications on tunnel state down,flap",
        "excludeTenantList": [],
        "id": "0dxxxxxxxxxxxxxxxxxxx6",
        "notifChannels": [
            {
                "name": "NOC-US-admin",
                "type": "WEBHOOK",
                "webhookChannelDetails": {
                    "authType": "NO_AUTH",
                    "urls": [
                        "https://webhook.site/ce5d0687-xxxxxxxxxxxxx9"
                    ]
                }
            },
            {
                "emailChannelDetails": {
                    "emails": [
                        {
                            "emailId": "xxxxxx@gmail.com",
                            "name": "NOC-US-admin"
                        }
                    ]
                },
                "name": "Email Channel",
                "type": "EMAIL"
            }
        ],
        "notifTypeDetails": [
            {
                "notifCategoryList": [
                    {
                        "bestPractice": false,
                        "name": "RN",
                        "subCategoryList": [
                            {
                                "bestPractice": false,
                                "name": "INC_RN_SECONDARY_WAN_TUNNEL_RTT_EXCEEDED_BASELINE"
                            },
                            {
                                "bestPractice": false,
                                "name": "INC_RN_ECMP_TUNNEL_DOWN"
                            },
                            {
                                "bestPractice": false,
                                "name": "INC_RN_ECMP_BGP_DOWN"
                            }
                        ]
                    }
                ],
                "type": "INCIDENTS"
            }
        ],
        "opState": "DISABLED",
        "profileName": "Tunnel-state-notification-profile",
        "tenantList": [
            "13xxxxxxxx",
            "16xxxxxxxx"
        ]
    },
    "requestId": "ecbcxxxxxxx"
}
