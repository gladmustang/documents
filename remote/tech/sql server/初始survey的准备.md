insert into faast.core_survey (cs_su_guid, cs_survey, cs_name)

values (

'1',

' { "title":"Claims Testing Results",

                "pages": [

                    {

                        "name":"Page1",

                        "questions":

                            [

                                {

                                    "type":"text",

                                    "hasOther":"false",

                                    "hasComment":"false",

                                    "isRequired":"false",

                                    "name":"questiion1",

                                    "title":"Type of Supporting Document Examined For Date of Loss",

                                    "visible":"true"

                                },

                                {

                                    "type":"text",

                                    "hasOther":"false",

                                    "hasComment":"false",

                                    "isRequired":"false",

                                    "name":"questiion2",

                                    "title":"Supporting Document Reference Number:",

                                    "visible":"true"

                                },

                                {

                                    "type":"text",

                                    "hasOther":"false",

                                    "hasComment":"false",

                                    "isRequired":"false",

                                    "name":"questiion3",

                                    "title":"Date of Loss Per Supporting Documentation:",

                                    "visible":"true"

                                },

                                {

                                    "type": "dropdown",

                                    "choices": [

                                        {

                                            "value": "item1",

                                            "text": "text1"

                                        },

                                        {

                                            "value": "item2",

                                            "text": "text2"

                                        },

                                        {

                                            "value": "item3",

                                            "text": "text3"

                                        }

                                    ],

                                    "name": "question4",

                                    "title": "Date of Loss Per Supporting Documentation Agrees to Date of Loss per Detailed Listing:"

                                }

                            ]   

                    }

                ]

}',

'Claims Testing Results'

)