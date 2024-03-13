# Multitenant-Notification-API-Workflow

## Case 1: Create a multi-tenant incidents notification profile
REQUEST: POST "https://api.sase.paloaltonetworks.com/mt/notifications/v1/profiles"
REQUEST HEADERS:
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

## Case 2: Create a Multi tenant Upgrades/Announcements notification profile
REQUEST: POST https://api.sase.paloaltonetworks.com/mt/notifications/v1/profiles
REQUEST HEADERS:
	User-Agent: python-requests/2.31.0 (PRISMA SASE SDK v6.3.1b1)
	Accept-Encoding: gzip, deflate, br
	Accept: application/json
	Connection: keep-alive
	authorization: Bearer exxxxxxxxxxx
	Content-Type: application/json
	Content-Length: 747
REQUEST BODY:
{
    "profileName": "upgrades-announcements-profile",
    "tenantList": [
        "13xxxxxxxx",
        "16xxxxxxxx"
    ],
    "description": "Profile for Upgrades/Announcements",
    "excludeTenantList": [],
    "notifChannels": [
        {
            "name": "NOC-US-admin",
            "type": "WEBHOOK",
            "webhookChannelDetails": {
                "urls": [
                    "https://webhook.site/xxxxxxxxx"
                ],
                "authType": "NO_AUTH"
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
            "name": "NOC-admin-US",
            "type": "EMAIL"
        }
    ],
    "notifTypeDetails": [
        {
            "notifCategoryList": [
                {
                    "bestPractice": false,
                    "name": "Dataplane",
                    "subCategoryList": [
                        {
                            "bestPractice": true,
                            "name": "In Progress"
                        },
                        {
                            "bestPractice": true,
                            "name": "Error"
                        }
                    ]
                }
            ],
            "type": "UPGRADES"
        }
    ],
    "opState": "ENABLED"
}

RESPONSE: 201 Created
RESPONSE DATA:
{
    "data": {
        "description": "Profile for Upgrades/Announcements",
        "excludeTenantList": [],
        "id": "7axxxx",
        "notifChannels": [
            {
                "name": "NOC-US-admin",
                "type": "WEBHOOK",
                "webhookChannelDetails": {
                    "authType": "NO_AUTH",
                    "urls": [
                        "https://webhook.site/ce5xxxxx"
                    ]
                }
            },
            {
                "emailChannelDetails": {
                    "emails": [
                        {
                            "emailId": "xxxxx@gmail.com",
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
                        "name": "Dataplane",
                        "subCategoryList": [
                            {
                                "bestPractice": true,
                                "name": "In Progress"
                            },
                            {
                                "bestPractice": true,
                                "name": "Error"
                            }
                        ]
                    }
                ],
                "type": "UPGRADES"
            }
        ],
        "opState": "ENABLED",
        "profileName": "upgrades-announcements-profile",
        "tenantList": [
            "13xx",
            "16xx"
        ]
    },
    "requestId": "fd0xxxxxxx"
}

##Case 3: List all notification profiles to fetch the ID of a specific profile to edit
REQUEST: GET /mt/notifications/v1/profiles
REQUEST HEADERS:
	User-Agent: python-requests/2.31.0 (PRISMA SASE SDK v6.3.1b1)
	Accept-Encoding: gzip, deflate, br
	Accept: application/json
	Connection: keep-alive
	authorization: Bearer eyJ0eXAiOiJxxxxx
	Cookie: JSESSIONID=yUvVSWMqkiGpSIU58Xh0IA_6jvcjWxv5OtVoh_p8
REQUEST BODY:
{}

RESPONSE: 200 OK

RESPONSE DATA:
{
    "data": [
        {
            "description": "Profile for notifications on tunnel state down,flap",
            "excludeTenantList": [],
            "failureTenant": [],
            "id": "0dxxxx",     <<<<<<<<<<<<<<<< id used to edit/change the state of a profile
            "notifChannels": [
                {
                    "name": "NOC-US-admin",
                    "type": "WEBHOOK",
                    "webhookChannelDetails": {
                        "authType": "NO_AUTH",
                        "urls": [
                            "https://webhook.site/cexxxx"
                        ]
                    }
                },
                {
                    "emailChannelDetails": {
                        "emails": [
                            {
                                "emailId": "xxx@gmail.com",
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
            "opState": "ENABLED",
            "profileName": "Tunnel-state-notification-profile",
            "status": "SUCCESS",
            "successTenant": [
                "16xxxx",
                "1xxxx"
            ],
            "tenantList": [
                "13xxxx",
                "16xxxx"
            ]
        },
        {
            "description": "Profile for Upgrades/Announcements",
            "excludeTenantList": [],
            "id": "7axxxx",               <<<<<<<<<<<<<<<< id used to edit/change the state of a profile
            "notifChannels": [
                {
                    "name": "NOC-US-admin",
                    "type": "WEBHOOK",
                    "webhookChannelDetails": {
                        "authType": "NO_AUTH",
                        "urls": [
                            "https://webhook.site/cxxxxx"
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
                            "name": "Dataplane",
                            "subCategoryList": [
                                {
                                    "bestPractice": true,
                                    "name": "Error"
                                },
                                {
                                    "bestPractice": true,
                                    "name": "In Progress"
                                }
                            ]
                        }
                    ],
                    "type": "UPGRADES"
                }
            ],
            "opState": "ENABLED",
            "profileName": "upgrades-announcements-profile",
            "status": "SUCCESS",
            "tenantList": [
                "13xxxx",
                "16xxxx"
            ]
        }
    ],
    "requestId": "7exxxxx"
}

##Case 4: Update a specific profile using the ID from the list, updating a new email to teh email channel
******NOTE: Fetch the entire payload of existing profile and add/edit using that. The entire profile is overwritten with the "PUT" payload.
REQUEST: PUT /mt/notifications/v1/profiles/7a972b3f-73e4-45bb-a63d-e46f850d940a
REQUEST HEADERS:
	User-Agent: python-requests/2.31.0 (PRISMA SASE SDK v6.3.1b1)
	Accept-Encoding: gzip, deflate, br
	Accept: application/json
	Connection: keep-alive
	authorization: Bearer eyxxxxxxxxx
	Content-Type: application/json
	Content-Length: 716
REQUEST BODY:
{
    "profileName": "upgrades-announcements-profile",
    "tenantList": [
        "13xxxxx",
        "16xxxxx"
    ],
    "description": "Profile for Upgrades/Announcements",
    "excludeTenantList": [],
    "id": "7a972b3f-73e4-45bb-a63d-e46f850d940a",
    "notifChannels": [
        {
            "emailChannelDetails": {
                "emails": [
                    {
                        "emailId": "xxxxx@gmail.com",
                        "name": "NOC-US-admin2"
                    },
                    {
                        "emailId": "xxxxx@gmail.com",
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
            "type": "ANNOUNCEMENTS"
        },
        {
            "notifCategoryList": [
                {
                    "bestPractice": false,
                    "name": "Dataplane",
                    "subCategoryList": [
                        {
                            "bestPractice": true,
                            "name": "In Progress"
                        },
                        {
                            "bestPractice": true,
                            "name": "Error"
                        }
                    ]
                }
            ],
            "type": "UPGRADES"
        }
    ],
    "opState": "ENABLED"
}

RESPONSE: 200 OK

RESPONSE DATA:
{
    "data": {
        "description": "Profile for Upgrades/Announcements",
        "excludeTenantList": [],
        "id": "7axxxxx",
        "notifChannels": [
            {
                "emailChannelDetails": {
                    "emails": [
                        {
                            "emailId": "xxxxxxx@gmail.com",
                            "name": "NOC-US-admin"
                        },
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
                "type": "ANNOUNCEMENTS"
            },
            {
                "notifCategoryList": [
                    {
                        "bestPractice": false,
                        "name": "Dataplane",
                        "subCategoryList": [
                            {
                                "bestPractice": true,
                                "name": "Error"
                            },
                            {
                                "bestPractice": true,
                                "name": "In Progress"
                            }
                        ]
                    }
                ],
                "type": "UPGRADES"
            }
        ],
        "opState": "ENABLED",
        "profileName": "upgrades-announcements-profile",
        "tenantList": [
            "13xxxx,
            "16xxxx"
        ]
    },
    "requestId": "00exxxxxx"
}

##Case 5: List all notification types (Can be used to decide which types/subtypes to choose while creating/editing notification profile)
REQUEST: GET /mt/notifications/v1/types
REQUEST HEADERS:
	User-Agent: python-requests/2.31.0 (PRISMA SASE SDK v6.3.1b1)
	Accept-Encoding: gzip, deflate, br
	Accept: application/json
	Connection: keep-alive
	authorization: Bearer eyJ0eXxxxxxx
REQUEST BODY:
{}

RESPONSE: 200 OK
RESPONSE HEADERS:

RESPONSE DATA:
{
    "data": [
        {
            "notifCategoryList": [
                {
                    "bestPractice": false,
                    "name": "Dataplane",
                    "subCategoryList": [
                        {
                            "bestPractice": false,
                            "name": "Postponed"
                        },
                        {
                            "bestPractice": true,
                            "name": "In Progress"
                        },
                        {
                            "bestPractice": true,
                            "name": "Error"
                        },
                        {
                            "bestPractice": true,
                            "name": "Scheduled"
                        },
                        {
                            "bestPractice": true,
                            "name": "Cancelled"
                        },
                        {
                            "bestPractice": true,
                            "name": "Completed"
                        },
                        {
                            "bestPractice": false,
                            "name": "Other"
                        },
                        {
                            "bestPractice": false,
                            "name": "Rolled back"
                        },
                        {
                            "bestPractice": false,
                            "name": "Retry"
                        }
                    ]
                }
            ],
            "type": "UPGRADES"
        },
        {
            "notifCategoryList": [
                {
                    "bestPractice": false,
                    "name": "RN",
                    "subCategoryList": [
                        {
                            "bestPractice": true,
                            "name": "INC_RN_ECMP_BGP_DOWN"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_RN_SECONDARY_WAN_BGP_DOWN"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_RN_PRIMARY_WAN_BGP_FLAP"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_RN_SPN_LONG_DURATION_CAPACITY_EXCEEDED_THRESHOLD"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_RN_ECMP_TUNNEL_RTT_EXCEEDED_BASELINE"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_RN_PRIMARY_WAN_TUNNEL_DOWN"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_RN_PRIMARY_WAN_TUNNEL_RTT_EXCEEDED_BASELINE"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_RN_PRIMARY_WAN_BGP_DOWN"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_RN_SECONDARY_WAN_TUNNEL_RTT_EXCEEDED_BASELINE"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_RN_PRIMARY_WAN_TUNNEL_FLAP"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_RN_SITE_LONG_DURATION_EXCEEDED_CAPACITY"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_RN_SITE_LONG_DURATION_CAPACITY_EXCEEDED_THRESHOLD"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_RN_SECONDARY_WAN_BGP_FLAP"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_RN_SPN_LONG_DURATION_EXCEEDED_CAPACITY"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_RN_SITE_DOWN"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_RN_ECMP_BGP_FLAP"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_RN_SECONDARY_WAN_TUNNEL_FLAP"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_RN_ECMP_TUNNEL_DOWN"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_RN_ECMP_TUNNEL_FLAP"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_RN_SITE_CAPACITY_PREDICTION"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_RN_SECONDARY_WAN_TUNNEL_DOWN"
                        }
                    ]
                },
                {
                    "bestPractice": false,
                    "name": "Authentication",
                    "subCategoryList": [
                        {
                            "bestPractice": false,
                            "name": "INC_RN_AUTH_SERVER_UNREACHABLE_ALL_PA_LOCATIONS"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_CIE_AGENT_DISCONNECT"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_MU_AUTH_SERVER_UNREACHABLE_PER_PA_LOCATION"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_PORTAL_CLIENTLESS_VPN_AUTH_TIMEOUT_FAILURES_COUNT_EXCEEDED_ABOVE_BASELINE_PER_PA_LOCATION"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_RN_AUTH_SERVER_UNREACHABLE_PER_PA_LOCATION"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_GLOBALPROTECT_GW_USER_AUTH_TIMEOUT_FAILURES_COUNT_EXCEEDED_ABOVE_BASELINE_ALL_PA_LOCATIONS"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_CIE_DIRECTORY_DISCONNECT"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_GLOBALPROTECT_PORTAL_AUTH_TIMEOUT_FAILURES_COUNT_EXCEEDED_ABOVE_BASELINE_ALL_PA_LOCATIONS"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_MU_AUTH_SERVER_UNREACHABLE_ALL_PA_LOCATIONS"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_PORTAL_CLIENTLESS_VPN_AUTH_TIMEOUT_FAILURES_COUNT_EXCEEDED_ABOVE_BASELINE_ALL_PA_LOCATIONS"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_GLOBALPROTECT_GW_USER_AUTH_TIMEOUT_FAILURES_COUNT_EXCEEDED_ABOVE_BASELINE_PER_PA_LOCATION"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_GLOBALPROTECT_PORTAL_AUTH_TIMEOUT_FAILURES_COUNT_EXCEEDED_ABOVE_BASELINE_PER_PA_LOCATION"
                        }
                    ]
                },
                {
                    "bestPractice": false,
                    "name": "SC",
                    "subCategoryList": [
                        {
                            "bestPractice": false,
                            "name": "INC_SC_PRIMARY_WAN_BGP_FLAP"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_SC_SECONDARY_WAN_TUNNEL_DOWN"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_SC_SITE_DOWN"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_SC_SECONDARY_WAN_TUNNEL_RTT_EXCEEDED_BASELINE"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_SC_PRIMARY_WAN_TUNNEL_FLAP"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_SC_SITE_LONG_DURATION_EXCEEDED_CAPACITY"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_SC_PRIMARY_WAN_BGP_DOWN"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_SC_PRIMARY_WAN_TUNNEL_DOWN"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_SC_SECONDARY_WAN_BGP_DOWN"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_SC_SITE_CAPACITY_PREDICTION"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_SC_SITE_LONG_DURATION_CAPACITY_EXCEEDED_THRESHOLD"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_SC_PRIMARY_WAN_TUNNEL_RTT_EXCEEDED_BASELINE"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_SC_SECONDARY_WAN_TUNNEL_FLAP"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_SC_SECONDARY_WAN_BGP_FLAP"
                        }
                    ]
                },
                {
                    "bestPractice": false,
                    "name": "Security",
                    "subCategoryList": [
                        {
                            "bestPractice": false,
                            "name": "INC_GENERALIZED_BLOCK_SECURITY_RULE_COVERED_BY_LOWER_ORDER_ALLOW_RULE"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_SHADOWED_ALLOW_SECURITY_RULE_COVERED_BY_HIGHER_ORDER_BLOCK_RULE"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_REDUNDANT_BLOCK_SECURITY_RULE_COVERED_BY_HIGHER_ORDER_BLOCK_RULE"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_REDUNDANT_BLOCK_SECURITY_RULE_COVERED_BY_LOWER_ORDER_BLOCK_RULE"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_REDUNDANT_ALLOW_SECURITY_RULE_COVERED_BY_HIGHER_ORDER_ALLOW_RULE"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_GENERALIZED_ALLOW_SECURITY_RULE_COVERED_BY_LOWER_ORDER_BLOCK_RULE"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_SHADOWED_BLOCK_SECURITY_RULE_COVERED_BY_HIGHER_ORDER_ALLOW_RULE"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_REDUNDANT_ALLOW_SECURITY_RULE_COVERED_BY_LOWER_ORDER_ALLOW_RULE"
                        }
                    ]
                },
                {
                    "bestPractice": false,
                    "name": "Prisma Access Infrastructure",
                    "subCategoryList": [
                        {
                            "bestPractice": true,
                            "name": "INC_PA_SERVICE_DEGRADATION_PA_LOCATION"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_PA_SERVICE_DEGRADATION_RN_SITE_CONNECTIVITY"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_PA_SERVICE_DEGRADATION_SC_CONNECTIVITY"
                        }
                    ]
                },
                {
                    "bestPractice": false,
                    "name": "ZTNA",
                    "subCategoryList": [
                        {
                            "bestPractice": false,
                            "name": "INC_ZTNA_CONNECTOR_TUNNEL_DOWN"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_ZTNA_CONNECTOR_APP_STATUS_DOWN_PARTIAL"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_ZTNA_CONNECTOR_APP_STATUS_DOWN"
                        }
                    ]
                },
                {
                    "bestPractice": false,
                    "name": "MU",
                    "subCategoryList": [
                        {
                            "bestPractice": false,
                            "name": "INC_MU_IP_POOL_BLOCK_UTILIZATION_EXCEEDED_THRESHOLD"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_MU_IP_POOL_BLOCK_UTILIZATION_EXCEEDED_CAPACITY"
                        }
                    ]
                },
                {
                    "bestPractice": false,
                    "name": "DNS",
                    "subCategoryList": [
                        {
                            "bestPractice": false,
                            "name": "INC_RN_DNS_SERVER_UNREACHABLE_ALL_PA_LOCATIONS"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_MU_DNS_SERVER_UNREACHABLE_PER_PA_LOCATION"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_MU_DNS_SERVER_UNREACHABLE_ALL_PA_LOCATIONS"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_RN_DNS_SERVER_UNREACHABLE_PER_PA_LOCATION"
                        }
                    ]
                },
                {
                    "bestPractice": false,
                    "name": "GP",
                    "subCategoryList": [
                        {
                            "bestPractice": false,
                            "name": "INC_GP_CLIENT_VERSION_UNSUPPORTED"
                        }
                    ]
                },
                {
                    "bestPractice": false,
                    "name": "Application Experience",
                    "subCategoryList": [
                        {
                            "bestPractice": true,
                            "name": "INC_RN_APP_EXPERIENCE_DEGRADED_PERFORMANCE_PER_PA_LOCATION"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_RN_APP_EXPERIENCE_DEGRADED_PERFORMANCE_ALL_PA_LOCATIONS"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_MU_APP_EXPERIENCE_DEGRADED_PERFORMANCE_PER_PA_LOCATION"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_MU_APP_EXPERIENCE_DEGRADED_PERFORMANCE_ALL_PA_LOCATIONS"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_MU_APP_EXPERIENCE_UNREACHABLE_ALL_PA_LOCATIONS"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_RN_APP_EXPERIENCE_UNREACHABLE_PER_PA_LOCATION"
                        },
                        {
                            "bestPractice": true,
                            "name": "INC_MU_APP_EXPERIENCE_UNREACHABLE_PER_PA_LOCATION"
                        },
                        {
                            "bestPractice": false,
                            "name": "INC_RN_APP_EXPERIENCE_UNREACHABLE_ALL_PA_LOCATIONS"
                        }
                    ]
                }
            ],
            "type": "INCIDENTS"
        },
        {
            "type": "ANNOUNCEMENTS"
        }
    ],
    "requestId": "27xxxxx"
}

#Case 6:  Test the webhook connectivity via API
REQUEST: POST /mt/notifications/v1/profiles/webhook/test
REQUEST HEADERS:
	User-Agent: python-requests/2.31.0 (PRISMA SASE SDK v6.3.1b1)
	Accept-Encoding: gzip, deflate, br
	Accept: application/json
	Connection: keep-alive
	authorization: Bearer eyJ0xxxxxx
	Content-Type: application/json
	Cookie: JSESSIONID=A4sdK0FCOQy22GqIHLRxTDQ6NXXKxN19WggyDuUj
	Content-Length: 94
REQUEST BODY:
{
    "urls": [
        "https://webhook.site/808605a4-f565-4cxxxxxxx"
    ],
    "authType": "NO_AUTH"
}

RESPONSE: 201 Created

RESPONSE DATA:
{
    "data": "Webhook Connectivity Check Success",
    "requestId": "00028xxxxxxx"
}

#Case 7: Fetch all upgrade/announcement notifications in read/unread state in ascending order of impacted tenants
REQUEST: POST /mt/notifications/v1/list
REQUEST HEADERS:
	User-Agent: python-requests/2.31.0 (PRISMA SASE SDK v6.3.1b1)
	Accept-Encoding: gzip, deflate, br
	Accept: application/json
	Connection: keep-alive
	authorization: Bearer eyJ0eXAxxxxxxx
	Content-Type: application/json
	Content-Length: 231
REQUEST BODY:
{
    "filters": [
        {
            "field": "readState",
            "values": [
                "READ",
                "UNREAD"
            ]
        },
        {
            "field": "notifType",
            "values": [
                "UPGRADES",
                "ANNOUNCEMENTS"
            ]
        }
    ],
    "sortByList": [
        {
            "field": "impactedTenantCount",
            "sortBy": "ASC"
        }
    ],
    "page": {
        "num": 0,
        "size": 10
    }
}

RESPONSE: 200 OK

RESPONSE DATA:
{
    "data": {
        "notificationCounts": {
            "readCount": 0,
            "unreadCount": 0
        },
        "notificationList": [],
        "totalCount": 0
    },
    "requestId": "c6a0a5xxxxx"
}

#Case 8: Fetch all the notification incidents from the MSP notifications
REQUEST: POST /mt/monitor/v1/agg/incidents/list
REQUEST HEADERS:
	User-Agent: python-requests/2.31.0 (PRISMA SASE SDK v6.3.1b1)
	Accept-Encoding: gzip, deflate, br
	Accept: application/json
	Connection: keep-alive
	authorization: Bearer eyJ0eXxxxxx
	Content-Type: application/json
	Content-Length: 588
REQUEST BODY:
{
    "properties": [
        {
            "property": "incident_id"
        },
        {
            "property": "title"
        },
        {
            "property": "sub_tenant_id"
        },
        {
            "property": "severity"
        },
        {
            "property": "category"
        },
        {
            "property": "sub_category"
        },
        {
            "property": "status"
        },
        {
            "property": "created_time"
        },
        {
            "property": "updated_time"
        },
        {
            "property": "clear_reason"
        },
        {
            "property": "code"
        }
    ],
    "filter": {
        "operator": "AND",
        "rules": [
            {
                "property": "updated_time",
                "operator": "last_n_days",
                "values": [
                    7
                ]
            },
            {
                "property": "domain",
                "operator": "in",
                "values": [
                    "External",
                    "external"
                ]
            },
            {
                "property": "severity",
                "operator": "in",
                "values": [
                    "Critical",
                    "Warning"
                ]
            }
        ]
    }
}

RESPONSE: 200 OK

RESPONSE DATA:
{
    "header": {
        "createdAt": "2024-03-13T17:48:35Z",
        "dataCount": 21,
        "requestId": "c5166644-1bxxxxx",
        "clientRequestId": "81f68xxxxxx",
        "queryInput": {
            "time_range": "last 7 day(s)",
            "event_time": {
                "from": "2024-03-06T00:00:00Z",
                "to": "2024-03-13T17:47:59Z",
                "from_epoch": 1709683200000,
                "to_epoch": 1710352079000
            }
        },
        "status": {
            "subCode": 200
        }
    },
    "data": [
        {
            "incident_id": "9a1e2xxxxxx6",
            "title": "DNS server 10.10.5.11 is unreachable for location US Central for MU",
            "sub_tenant_id": "13xxxxx",
            "severity": "Critical",
            "category": "DNS",
            "status": "Raised",
            "created_time": 1710338542649,
            "updated_time": 1710339049223,
            "code": "INC_MU_DNS_SERVER_UNREACHABLE_PER_PA_LOCATION",
            "tsg_id": "122xxxx"
        },
        {
            "incident_id": "63363848-fxxxxx",
            "title": "DNS server 10.10.5.11 is unreachable for location US Central for MU",
            "sub_tenant_id": "13xxxxx",
            "severity": "Critical",
            "category": "DNS",
            "status": "Cleared",
            "created_time": 1710296229885,
            "updated_time": 1710312129713,
            "clear_reason": "Auto",
            "code": "INC_MU_DNS_SERVER_UNREACHABLE_PER_PA_LOCATION",
            "tsg_id": "1228584868"
        },
        {
            "incident_id": "67d9efe0-bcxxxxxxx",
            "title": "DNS server 10.10.5.11 is unreachable for location US Central for MU",
            "sub_tenant_id": "135xxxxxx",
            "severity": "Critical",
            "category": "DNS",
            "status": "Cleared",
            "created_time": 1710199922885,
            "updated_time": 1710203827848,
            "clear_reason": "Auto",
            "code": "INC_MU_DNS_SERVER_UNREACHABLE_PER_PA_LOCATION",
            "tsg_id": "1228xxxx"
        },
       
        {
            "incident_id": "b1cexxxxxxx",
            "title": "Auth server https://dev-04352742.okta.com/app/panw_captiveportal/exk89qkd8hdPLNyZT5d7/sso/saml is unreachable for location US Central for MU",
            "sub_tenant_id": "13xxxxx",
            "severity": "Critical",
            "category": "Authentication",
            "status": "Cleared",
            "created_time": 1709833968709,
            "updated_time": 1709836337488,
            "clear_reason": "Auto",
            "code": "INC_MU_AUTH_SERVER_UNREACHABLE_PER_PA_LOCATION",
            "tsg_id": "12xxxx"
        },
       
    ]
}
