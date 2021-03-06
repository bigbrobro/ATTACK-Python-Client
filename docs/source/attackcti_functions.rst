Library Functions
=================

get_enterprise
##############

get_enterprise(self, stix_format=True)
**************************************

Extracts all the available STIX objects in the Enterprise ATT&CK matrix categorized in the following way:

+--------------------+---------------------+
| ATT&CK Format      | STIX Format         |
+====================+=====================+
| technique          | attack-pattern      |
+--------------------+---------------------+
| mitigation         | course-of-action    |
+--------------------+---------------------+
| group              | intrusion-set       |
+--------------------+---------------------+
| malware            | malware             |
+--------------------+---------------------+
| tool               | tool                |
+--------------------+---------------------+
| relationship       | relationship        |
+--------------------+---------------------+
| tactic             | x-mitre-tactic      |
+--------------------+---------------------+
| matrix             | x-mitre-tactic      |
+--------------------+---------------------+
| identity           | identity            |
+--------------------+---------------------+
| marking-definition | markinng-definition |
+--------------------+---------------------+

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: Dictionary

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> enterprise = lift.get_enterprise()
>>> type(enterprise)
<class 'dict'>
>>>
>>> enterprise.keys()
dict_keys(['techniques', 'mitigations', 'groups', 'malware', 'tools', 'relationships', 'tactics', 'matrix', 'identity', 'marking-definition'])
>>>
>>> type(enterprise['techniques'])
<class 'list'>
>>> type(enterprise['techniques'][0])
<class 'stix2.v20.sdo.AttackPattern'>
>>>
>>> print(enterprise['techniques'][0])
{
    "type": "attack-pattern",
    "id": "attack-pattern--cf7b3a06-8b42-4c33-bbe9-012120027925",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2019-04-25T20:53:07.719Z",
    "modified": "2019-04-29T21:13:49.686Z",
    "name": "Compile After Delivery",
    "description": "Adversaries may attempt to make payloads difficult to discover and analyze by delivering files to victims as uncompiled code. Similar to [Obfuscated Files or Information](https://attack.mitre.org/techniques/T1027), text-based source code files may subvert analysis and scrutiny from protections targeting executables/binaries. These payloads will need to be compiled before execution; typically via native utilities such as csc.exe or GCC/MinGW.(Citation: ClearSky MuddyWater Nov 2018)\n\nSource code payloads may also be encrypted, encoded, and/or embedded within other files, such as those delivered as a [Spearphishing Attachment](https://attack.mitre.org/techniques/T1193). Payloads may also be delivered in formats unrecognizable and inherently benign to the native OS (ex: EXEs on macOS/Linux) before later being (re)compiled into a proper executable binary with a bundled compiler and execution framework.(Citation: TrendMicro WindowsAppMac)\n",
    "kill_chain_phases": [
        {
            "kill_chain_name": "mitre-attack",
            "phase_name": "defense-evasion"
        }
    ],
    "external_references": [
        {
            "source_name": "mitre-attack",
            "url": "https://attack.mitre.org/techniques/T1500",
            "external_id": "T1500"
        },
        {
            "source_name": "ClearSky MuddyWater Nov 2018",
            "description": "ClearSky Cyber Security. (2018, November). MuddyWater Operations in Lebanon and Oman: Using an Israeli compromised domain for a two-stage campaign. Retrieved November 29, 2018.",
            "url": "https://www.clearskysec.com/wp-content/uploads/2018/11/MuddyWater-Operations-in-Lebanon-and-Oman.pdf"
        },
        {
            "source_name": "TrendMicro WindowsAppMac",
            "description": "Trend Micro. (2019, February 11). Windows App Runs on Mac, Downloads Info Stealer and Adware. Retrieved April 25, 2019.",
            "url": "https://blog.trendmicro.com/trendlabs-security-intelligence/windows-app-runs-on-mac-downloads-info-stealer-and-adware/"
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_contributors": [
        "Ye Yint Min Thu Htut, Offensive Security Team, DBS Bank",
        "Praetorian"
    ],
    "x_mitre_data_sources": [
        "Process command-line parameters",
        "Process monitoring",
        "File monitoring"
    ],
    "x_mitre_defense_bypassed": [
        "Static File Analysis",
        "Binary Analysis",
        "Anti-virus",
        "Host intrusion prevention systems",
        "Signature-based detection"
    ],
    "x_mitre_detection": "Monitor the execution file paths and command-line arguments for common compilers, such as csc.exe and GCC/MinGW, and correlate with other suspicious behavior to reduce false positives from normal user and administrator behavior. The compilation of payloads may also generate file creation and/or file write events. Look for non-native binary formats and cross-platform compiler and execution frameworks like Mono and determine if they have a legitimate purpose on the system.(Citation: TrendMicro WindowsAppMac) Typically these should only be used in specific and limited cases, like for software development.",
    "x_mitre_permissions_required": [
        "User"
    ],
    "x_mitre_platforms": [
        "Linux",
        "macOS",
        "Windows"
    ],
    "x_mitre_system_requirements": [
        "Compiler software (either native to the system or delivered by the adversary)"
    ],
    "x_mitre_version": "1.0"
}

get_enterprise_techniques
#########################

get_enterprise_techniques(self, stix_format=True)
*************************************************

Extracts all the available techniques STIX objects in the Enterprise ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sdo.AttackPattern objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> enterprise_techniques = lift.get_enterprise_techniques()
>>> type(enterprise_techniques)
<class 'list'>
>>>
>>> type(enterprise_techniques[0])
<class 'stix2.v20.sdo.AttackPattern'>
>>>
>>> print(enterprise_techniques[0])
{
    "type": "attack-pattern",
    "id": "attack-pattern--cf7b3a06-8b42-4c33-bbe9-012120027925",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2019-04-25T20:53:07.719Z",
    "modified": "2019-04-29T21:13:49.686Z",
    "name": "Compile After Delivery",
    "description": "Adversaries may attempt to make payloads difficult to discover and analyze by delivering files to victims as uncompiled code. Similar to [Obfuscated Files or Information](https://attack.mitre.org/techniques/T1027), text-based source code files may subvert analysis and scrutiny from protections targeting executables/binaries. These payloads will need to be compiled before execution; typically via native utilities such as csc.exe or GCC/MinGW.(Citation: ClearSky MuddyWater Nov 2018)\n\nSource code payloads may also be encrypted, encoded, and/or embedded within other files, such as those delivered as a [Spearphishing Attachment](https://attack.mitre.org/techniques/T1193). Payloads may also be delivered in formats unrecognizable and inherently benign to the native OS (ex: EXEs on macOS/Linux) before later being (re)compiled into a proper executable binary with a bundled compiler and execution framework.(Citation: TrendMicro WindowsAppMac)\n",
    "kill_chain_phases": [
        {
            "kill_chain_name": "mitre-attack",
            "phase_name": "defense-evasion"
        }
    ],
    "external_references": [
        {
            "source_name": "mitre-attack",
            "url": "https://attack.mitre.org/techniques/T1500",
            "external_id": "T1500"
        },
        {
            "source_name": "ClearSky MuddyWater Nov 2018",
            "description": "ClearSky Cyber Security. (2018, November). MuddyWater Operations in Lebanon and Oman: Using an Israeli compromised domain for a two-stage campaign. Retrieved November 29, 2018.",
            "url": "https://www.clearskysec.com/wp-content/uploads/2018/11/MuddyWater-Operations-in-Lebanon-and-Oman.pdf"
        },
        {
            "source_name": "TrendMicro WindowsAppMac",
            "description": "Trend Micro. (2019, February 11). Windows App Runs on Mac, Downloads Info Stealer and Adware. Retrieved April 25, 2019.",
            "url": "https://blog.trendmicro.com/trendlabs-security-intelligence/windows-app-runs-on-mac-downloads-info-stealer-and-adware/"
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_contributors": [
        "Ye Yint Min Thu Htut, Offensive Security Team, DBS Bank",
        "Praetorian"
    ],
    "x_mitre_data_sources": [
        "Process command-line parameters",
        "Process monitoring",
        "File monitoring"
    ],
    "x_mitre_defense_bypassed": [
        "Static File Analysis",
        "Binary Analysis",
        "Anti-virus",
        "Host intrusion prevention systems",
        "Signature-based detection"
    ],
    "x_mitre_detection": "Monitor the execution file paths and command-line arguments for common compilers, such as csc.exe and GCC/MinGW, and correlate with other suspicious behavior to reduce false positives from normal user and administrator behavior. The compilation of payloads may also generate file creation and/or file write events. Look for non-native binary formats and cross-platform compiler and execution frameworks like Mono and determine if they have a legitimate purpose on the system.(Citation: TrendMicro WindowsAppMac) Typically these should only be used in specific and limited cases, like for software development.",
    "x_mitre_permissions_required": [
        "User"
    ],
    "x_mitre_platforms": [
        "Linux",
        "macOS",
        "Windows"
    ],
    "x_mitre_system_requirements": [
        "Compiler software (either native to the system or delivered by the adversary)"
    ],
    "x_mitre_version": "1.0"
}

get_enterprise_mitigations
##########################

get_enterprise_mitigations(self, stix_format=True)
**************************************************

Extracts all the available mitigations STIX objects in the Enterprise ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sdo.CourseOfAction objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> enterprise_mitigations = lift.get_enterprise_mitigations()
>>> type(enterprise_mitigations)
<class 'list'>
>>> 
>>> type(enterprise_mitigations[0])
<class 'stix2.v20.sdo.CourseOfAction'>
>>> 
>>> print(enterprise_mitigations[0])
{
    "type": "course-of-action",
    "id": "course-of-action--70886857-0f19-4caa-b081-548354a8a994",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2019-04-26T19:30:33.607Z",
    "modified": "2019-04-26T19:41:45.126Z",
    "name": "Firmware Corruption Mitigation",
    "description": "Prevent adversary access to privileged accounts or access necessary to perform this technique. Check the integrity of the existing BIOS and device firmware to determine if it is vulnerable to modification. Patch the BIOS and other firmware as necessary to prevent successful use of known vulnerabilities. ",
    "external_references": [
        {
            "source_name": "mitre-attack",
            "url": "https://attack.mitre.org/techniques/T1495",
            "external_id": "T1495"
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_version": "1.0"
}

get_enterprise_groups
#####################

get_enterprise_groups(self, stix_format=True)
*********************************************

Extracts all the available groups STIX objects in the Enterprise ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sdo.IntrusionSet objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> enterprise_groups = lift.get_enterprise_groups()
>>> type(enterprise_groups)
<class 'list'>
>>> 
>>> type(enterprise_groups[0])
<class 'stix2.v20.sdo.IntrusionSet'>
>>> 
>>> print(enterprise_groups[0])
{
    "type": "intrusion-set",
    "id": "intrusion-set--9538b1a4-4120-4e2d-bf59-3b11fcab05a4",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2019-04-16T15:14:38.533Z",
    "modified": "2019-04-29T18:59:16.079Z",
    "name": "TEMP.Veles",
    "description": "[TEMP.Veles](https://attack.mitre.org/groups/G0088) is a Russia-based threat group that has targeted critical infrastructure. The group has been observed utilizing TRITON, a malware framework designed to manipulate industrial safety systems.(Citation: FireEye TRITON 2019)(Citation: FireEye TEMP.Veles 2018)(Citation: FireEye TEMP.Veles JSON April 2019)",
    "aliases": [
        "TEMP.Veles",
        "XENOTIME"
    ],
    "external_references": [
        {
            "source_name": "mitre-attack",
            "url": "https://attack.mitre.org/groups/G0088",
            "external_id": "G0088"
        },
        {
            "source_name": "TEMP.Veles",
            "description": "(Citation: FireEye TRITON 2019)"
        },
        {
            "source_name": "XENOTIME",
            "description": "The activity group XENOTIME, as defined by Dragos, has overlaps with activity reported upon by FireEye about TEMP.Veles as well as the actors behind TRITON.(Citation: Dragos Xenotime 2018)(Citation: Pylos Xenotime 2019)(Citation: FireEye TRITON 2019)(Citation: FireEye TEMP.Veles 2018 )"
        },
        {
            "source_name": "FireEye TRITON 2019",
            "description": "Miller, S, et al. (2019, April 10). TRITON Actor TTP Profile, Custom Attack Tools, Detections, and ATT&CK Mapping. Retrieved April 16, 2019.",
            "url": "https://www.fireeye.com/blog/threat-research/2019/04/triton-actor-ttp-profile-custom-attack-tools-detections.html"
        },
        {
            "source_name": "FireEye TEMP.Veles 2018",
            "description": "FireEye Intelligence . (2018, October 23). TRITON Attribution: Russian Government-Owned Lab Most Likely Built Custom Intrusion Tools for TRITON Attackers. Retrieved April 16, 2019.",
            "url": "https://www.fireeye.com/blog/threat-research/2018/10/triton-attribution-russian-government-owned-lab-most-likely-built-tools.html "
        },
        {
            "source_name": "FireEye TEMP.Veles JSON April 2019",
            "description": "Miller, S., et al. (2019, April 10). TRITON Appendix C. Retrieved April 29, 2019.",
            "url": "https://www.fireeye.com/content/dam/fireeye-www/blog/files/TRITON_Appendix_C.html"
        },
        {
            "source_name": "Dragos Xenotime 2018",
            "description": "Dragos, Inc.. (n.d.). Xenotime. Retrieved April 16, 2019.",
            "url": "https://dragos.com/resource/xenotime/"
        },
        {
            "source_name": "Pylos Xenotime 2019",
            "description": "Slowik, J.. (2019, April 12). A XENOTIME to Remember: Veles in the Wild. Retrieved April 16, 2019.",
            "url": "https://pylos.co/2019/04/12/a-xenotime-to-remember-veles-in-the-wild/"
        },
        {
            "source_name": "FireEye TEMP.Veles 2018 ",
            "description": "FireEye Intelligence . (2018, October 23). TRITON Attribution: Russian Government-Owned Lab Most Likely Built Custom Intrusion Tools for TRITON Attackers. Retrieved April 16, 2019.",
            "url": "https://www.fireeye.com/blog/threat-research/2018/10/triton-attribution-russian-government-owned-lab-most-likely-built-tools.html "
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_version": "1.0"
}

get_enterprise_malware
######################

get_enterprise_malware(self, stix_format=True)
**********************************************

Extracts all the available malware STIX objects in the Enterprise ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sdo.Malware objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> enterprise_malware = lift.get_enterprise_malware()         
>>> type(enterprise_malware)
<class 'list'>
>>> 
>>> type(enterprise_malware[0])
<class 'stix2.v20.sdo.Malware'>
>>> 
>>> print(enterprise_malware[0])
{
    "type": "malware",
    "id": "malware--d1531eaa-9e17-473e-a680-3298469662c3",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2019-04-23T18:41:36.914Z",
    "modified": "2019-04-29T21:19:34.739Z",
    "name": "CoinTicker",
    "description": "[CoinTicker](https://attack.mitre.org/software/S0369) is a malicious application that poses as a cryptocurrency price ticker and installs components of the open source backdoors EvilOSX and EggShell.(Citation: CoinTicker 2019)",
    "labels": [
        "malware"
    ],
    "external_references": [
        {
            "source_name": "mitre-attack",
            "url": "https://attack.mitre.org/software/S0369",
            "external_id": "S0369"
        },
        {
            "source_name": "CoinTicker 2019",
            "description": "Thomas Reed. (2018, October 29). Mac cryptocurrency ticker app installs backdoors. Retrieved April 23, 2019.",
            "url": "https://blog.malwarebytes.com/threat-analysis/2018/10/mac-cryptocurrency-ticker-app-installs-backdoors/"
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_aliases": [
        "CoinTicker"
    ],
    "x_mitre_contributors": [
        "Richie Cyrus, SpecterOps"
    ],
    "x_mitre_platforms": [
        "macOS"
    ],
    "x_mitre_version": "1.0"
}

get_enterprise_tools
####################

get_enterprise_tools(self, stix_format=True)
********************************************

Extracts all the available tools STIX objects in the Enterprise ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sdo.Tool objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> enterprise_tools = lift.get_enterprise_tools()
>>> type(enterprise_tools)
<class 'list'>
>>>
>>> type(enterprise_tools[0])
<class 'stix2.v20.sdo.Tool'>
>>>
>>> print(enterprise_tools[0])
{
    "type": "tool",
    "id": "tool--4b57c098-f043-4da2-83ef-7588a6d426bc",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2019-04-23T12:31:58.125Z",
    "modified": "2019-04-23T18:29:12.005Z",
    "name": "PoshC2",
    "description": "[PoshC2](https://attack.mitre.org/software/S0378) is an open source remote administration and post-exploitation framework that is publicly available on GitHub. The server-side components of the tool are primarily written in Python, while the implants are written in [PowerShell](https://attack.mitre.org/techniques/T1086). Although [PoshC2](https://attack.mitre.org/software/S0378) is primarily focused on Windows implantation, it does contain a basic Python dropper for Linux/macOS.(Citation: GitHub PoshC2)",
    "labels": [
        "tool"
    ],
    "external_references": [
        {
            "source_name": "mitre-attack",
            "url": "https://attack.mitre.org/software/S0378",
            "external_id": "S0378"
        },
        {
            "source_name": "GitHub PoshC2",
            "description": "Nettitude. (2016, June 8). PoshC2: Powershell C2 Server and Implants. Retrieved April 23, 2019.",
            "url": "https://github.com/nettitude/PoshC2"
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_aliases": [
        "PoshC2"
    ],
    "x_mitre_platforms": [
        "Windows",
        "Linux",
        "macOS"
    ],
    "x_mitre_version": "1.0"
}

get_enterprise_relationships
############################

get_enterprise_relationships(self, stix_format=True)
****************************************************

Extracts all the available relationships STIX objects in the Enterprise ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sro.Relationship objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> enterprise_relationships = lift.get_enterprise_relationships()
>>> type(enterprise_relationships)
<class 'list'>
>>>
>>> type(enterprise_relationships[0])
<class 'stix2.v20.sro.Relationship'>
>>>
>>> print(enterprise_relationships[0])
{
    "type": "relationship",
    "id": "relationship--2a37ddb3-56ef-4c2d-bec7-d6060eb0215a",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2019-04-29T15:54:23.241Z",
    "modified": "2019-04-29T18:16:38.854Z",
    "relationship_type": "uses",
    "source_ref": "intrusion-set--44e43fad-ffcb-4210-abcf-eaaed9735f80",
    "target_ref": "malware--ecc2f65a-b452-4eaf-9689-7e181f17f7a5",
    "external_references": [
        {
            "source_name": "Symantec Chafer Dec 2015",
            "description": "Symantec Security Response. (2015, December 7). Iran-based attackers use back door threats to spy on Middle Eastern targets. Retrieved April 17, 2019.",
            "url": "https://www.symantec.com/connect/blogs/iran-based-attackers-use-back-door-threats-spy-middle-eastern-targets"
        },
        {
            "source_name": "Securelist Remexi Jan 2019",
            "description": "Legezo, D. (2019, January 30). Chafer used Remexi malware to spy on Iran-based foreign diplomatic entities. Retrieved April 17, 2019.",
            "url": "https://securelist.com/chafer-used-remexi-malware/89538/"
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ]
}

get_enterprise_tactics
######################

get_enterprise_tactics(self, stix_format=True)
**********************************************

Extracts all the available tactics STIX objects in the Enterprise ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of dictionaries

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> enterprise_tactics = lift.get_enterprise_tactics()
>>> type(enterprise_tactics)
<class 'list'>
>>>
>>> type(enterprise_tactics[0])
<class 'dict'>
>>>
>>> print(enterprise_tactics[0])
{'external_references': [{'external_id': 'TA0040', 'source_name': 'mitre-attack', 'url': 'https://attack.mitre.org/tactics/TA0040'}], 'object_marking_refs': ['marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168'], 'id': 'x-mitre-tactic--5569339b-94c2-49ee-afb3-2222936582c8', 'name': 'Impact', 'created': '2019-03-14T18:44:44.639Z', 'modified': '2019-04-29T14:23:04.506Z', 'type': 'x-mitre-tactic', 'created_by_ref': 'identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5', 'description': "The Impact tactic represents techniques whose primary objective directly reduces the availability or integrity of a system, service, or network; including manipulation of data to impact a business or operational process. These techniques may represent an adversary's end goal, or provide cover for a breach of confidentiality.", 'x_mitre_shortname': 'impact'}


get_pre
#######

get_pre(self, stix_format=True)
*******************************

Extracts all the available STIX objects in the Pre ATT&CK matrix categorized in the following way:

+--------------------+---------------------+
| ATT&CK Format      | STIX Format         |
+====================+=====================+
| technique          | attack-pattern      |
+--------------------+---------------------+
| group              | intrusion-set       |
+--------------------+---------------------+
| relationship       | relationship        |
+--------------------+---------------------+
| tactic             | x-mitre-tactic      |
+--------------------+---------------------+
| matrix             | x-mitre-tactic      |
+--------------------+---------------------+
| identity           | identity            |
+--------------------+---------------------+
| marking-definition | markinng-definition |
+--------------------+---------------------+

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: Dictionary

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> pre = lift.get_pre()
>>> type(pre)
<class 'dict'>
>>>
>>> pre.keys()
dict_keys(['techniques', 'groups', 'relationships', 'tactics', 'matrix', 'identity', 'marking-definition'])
>>>
>>> type(pre['techniques'])
<class 'list'>
>>> type(pre['techniques'][0])
<class 'stix2.v20.sdo.AttackPattern'>
>>>
>>> print(pre['techniques'][0])
{
    "type": "attack-pattern",
    "id": "attack-pattern--b182f29c-2505-4b32-a000-0440ef189f59",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2018-04-18T17:59:24.739Z",
    "modified": "2018-10-17T00:14:20.652Z",
    "name": "Spearphishing for Information",
    "description": "Spearphishing for information is a specific variant of spearphishing. Spearphishing for information is different from other forms of spearphishing in that it it doesn't leverage malicious code. All forms of spearphishing are elctronically delivered social engineering targeted at a specific individual, company, or industry. Spearphishing for information is an attempt to trick targets into divulging information, frequently credentials, without involving malicious code. Spearphishing for information frequently involves masquerading as a source with a reason to collect information (such as a system administrator or a bank) and providing a user with a website link to visit. The given website often closely resembles a legitimate site in appearance and has a URL containing elements from the real site. From the fake website, information is gathered in web forms and sent to the attacker. Spearphishing for information may also try to obtain information directly through the exchange of emails, instant messengers or other electronic conversation means. (Citation: ATTACKREF GRIZZLY STEPPE JAR)",
    "kill_chain_phases": [
        {
            "kill_chain_name": "mitre-pre-attack",
            "phase_name": "technical-information-gathering"
        }
    ],
    "external_references": [
        {
            "source_name": "mitre-pre-attack",
            "url": "https://attack.mitre.org/techniques/T1397",
            "external_id": "T1397"
        },
        {
            "source_name": "ATTACKREF GRIZZLY STEPPE JAR",
            "description": "Department of Homeland Security and Federal Bureau of Investigation. (2016, December 29). GRIZZLY STEPPE \u2013 Russian Malicious Cyber Activity. Retrieved January 11, 2017."
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_detectable_by_common_defenses": "Partial",
    "x_mitre_detectable_by_common_defenses_explanation": "Depending on the specific method of phishing, the detections can vary. For emails, filtering based on DKIP+SPF or header analysis can help detect when the email sender is spoofed. When it comes to following links, network intrusion detection systems (NIDS), firewalls, removing links, exploding shortened links, proxy monitoring, blocking uncategorized sites, and site reputation based filtering can all provide detection opportunities.",
    "x_mitre_difficulty_for_adversary": "Yes",
    "x_mitre_difficulty_for_adversary_explanation": "Sending emails is trivial, and, over time, an adversary can refine their technique to minimize detection by making their emails seem legitimate in structure and content.",
    "x_mitre_old_attack_id": "PRE-T1174",
    "x_mitre_version": "1.0"
}

get_pre_techniques
##################

get_pre_techniques(self, stix_format=True)
******************************************

Extracts all the available techniques STIX objects in the Pre ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sdo.AttackPattern objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> pre_techniques = lift.get_pre_techniques()
>>> type(pre_techniques)
<class 'list'>
>>>
>>> type(pre_techniques[0])
<class 'stix2.v20.sdo.AttackPattern'>
>>>
>>> print(pre_techniques[0])
{
    "type": "attack-pattern",
    "id": "attack-pattern--b182f29c-2505-4b32-a000-0440ef189f59",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2018-04-18T17:59:24.739Z",
    "modified": "2018-10-17T00:14:20.652Z",
    "name": "Spearphishing for Information",
    "description": "Spearphishing for information is a specific variant of spearphishing. Spearphishing for information is different from other forms of spearphishing in that it it doesn't leverage malicious code. All forms of spearphishing are elctronically delivered social engineering targeted at a specific individual, company, or industry. Spearphishing for information is an attempt to trick targets into divulging information, frequently credentials, without involving malicious code. Spearphishing for information frequently involves masquerading as a source with a reason to collect information (such as a system administrator or a bank) and providing a user with a website link to visit. The given website often closely resembles a legitimate site in appearance and has a URL containing elements from the real site. From the fake website, information is gathered in web forms and sent to the attacker. Spearphishing for information may also try to obtain information directly through the exchange of emails, instant messengers or other electronic conversation means. (Citation: ATTACKREF GRIZZLY STEPPE JAR)",
    "kill_chain_phases": [
        {
            "kill_chain_name": "mitre-pre-attack",
            "phase_name": "technical-information-gathering"
        }
    ],
    "external_references": [
        {
            "source_name": "mitre-pre-attack",
            "url": "https://attack.mitre.org/techniques/T1397",
            "external_id": "T1397"
        },
        {
            "source_name": "ATTACKREF GRIZZLY STEPPE JAR",
            "description": "Department of Homeland Security and Federal Bureau of Investigation. (2016, December 29). GRIZZLY STEPPE \u2013 Russian Malicious Cyber Activity. Retrieved January 11, 2017."
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_detectable_by_common_defenses": "Partial",
    "x_mitre_detectable_by_common_defenses_explanation": "Depending on the specific method of phishing, the detections can vary. For emails, filtering based on DKIP+SPF or header analysis can help detect when the email sender is spoofed. When it comes to following links, network intrusion detection systems (NIDS), firewalls, removing links, exploding shortened links, proxy monitoring, blocking uncategorized sites, and site reputation based filtering can all provide detection opportunities.",
    "x_mitre_difficulty_for_adversary": "Yes",
    "x_mitre_difficulty_for_adversary_explanation": "Sending emails is trivial, and, over time, an adversary can refine their technique to minimize detection by making their emails seem legitimate in structure and content.",
    "x_mitre_old_attack_id": "PRE-T1174",
    "x_mitre_version": "1.0"
}

get_pre_groups
##############

get_pre_groups(self, stix_format=True)
**************************************

Extracts all the available groups STIX objects in the Pre ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sdo.IntrusionSet objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> pre_groups = lift.get_pre_groups()
>>> type(pre_groups)
<class 'list'>
>>>
>>> type(pre_groups[0])
<class 'stix2.v20.sdo.IntrusionSet'>
>>>
>>> print(pre_groups[0])
{
    "type": "intrusion-set",
    "id": "intrusion-set--9538b1a4-4120-4e2d-bf59-3b11fcab05a4",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2019-04-16T15:14:38.533Z",
    "modified": "2019-04-29T18:59:16.079Z",
    "name": "TEMP.Veles",
    "description": "[TEMP.Veles](https://attack.mitre.org/groups/G0088) is a Russia-based threat group that has targeted critical infrastructure. The group has been observed utilizing TRITON, a malware framework designed to manipulate industrial safety systems.(Citation: FireEye TRITON 2019)(Citation: FireEye TEMP.Veles 2018)(Citation: FireEye TEMP.Veles JSON April 2019)",
    "aliases": [
        "TEMP.Veles",
        "XENOTIME"
    ],
    "external_references": [
        {
            "source_name": "mitre-attack",
            "url": "https://attack.mitre.org/groups/G0088",
            "external_id": "G0088"
        },
        {
            "source_name": "TEMP.Veles",
            "description": "(Citation: FireEye TRITON 2019)"
        },
        {
            "source_name": "XENOTIME",
            "description": "The activity group XENOTIME, as defined by Dragos, has overlaps with activity reported upon by FireEye about TEMP.Veles as well as the actors behind TRITON.(Citation: Dragos Xenotime 2018)(Citation: Pylos Xenotime 2019)(Citation: FireEye TRITON 2019)(Citation: FireEye TEMP.Veles 2018 )"
        },
        {
            "source_name": "FireEye TRITON 2019",
            "description": "Miller, S, et al. (2019, April 10). TRITON Actor TTP Profile, Custom Attack Tools, Detections, and ATT&CK Mapping. Retrieved April 16, 2019.",
            "url": "https://www.fireeye.com/blog/threat-research/2019/04/triton-actor-ttp-profile-custom-attack-tools-detections.html"
        },
        {
            "source_name": "FireEye TEMP.Veles 2018",
            "description": "FireEye Intelligence . (2018, October 23). TRITON Attribution: Russian Government-Owned Lab Most Likely Built Custom Intrusion Tools for TRITON Attackers. Retrieved April 16, 2019.",
            "url": "https://www.fireeye.com/blog/threat-research/2018/10/triton-attribution-russian-government-owned-lab-most-likely-built-tools.html "
        },
        {
            "source_name": "FireEye TEMP.Veles JSON April 2019",
            "description": "Miller, S., et al. (2019, April 10). TRITON Appendix C. Retrieved April 29, 2019.",
            "url": "https://www.fireeye.com/content/dam/fireeye-www/blog/files/TRITON_Appendix_C.html"
        },
        {
            "source_name": "Dragos Xenotime 2018",
            "description": "Dragos, Inc.. (n.d.). Xenotime. Retrieved April 16, 2019.",
            "url": "https://dragos.com/resource/xenotime/"
        },
        {
            "source_name": "Pylos Xenotime 2019",
            "description": "Slowik, J.. (2019, April 12). A XENOTIME to Remember: Veles in the Wild. Retrieved April 16, 2019.",
            "url": "https://pylos.co/2019/04/12/a-xenotime-to-remember-veles-in-the-wild/"
        },
        {
            "source_name": "FireEye TEMP.Veles 2018 ",
            "description": "FireEye Intelligence . (2018, October 23). TRITON Attribution: Russian Government-Owned Lab Most Likely Built Custom Intrusion Tools for TRITON Attackers. Retrieved April 16, 2019.",
            "url": "https://www.fireeye.com/blog/threat-research/2018/10/triton-attribution-russian-government-owned-lab-most-likely-built-tools.html "
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_version": "1.0"
}

get_pre_relationships
#####################

get_pre_relationships(self, stix_format=True)
*********************************************

Extracts all the available relationships STIX objects in the Pre ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sro.Relationship objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> pre_relationships = lift.get_pre_relationships()
>>> type(pre_relationships)
<class 'list'>
>>>
>>> type(pre_relationships[0])
<class 'stix2.v20.sro.Relationship'>
>>>
>>> print(pre_relationships[0])
{
    "type": "relationship",
    "id": "relationship--21842707-0f15-43bf-bc42-2bceadf2cfa2",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2019-04-24T19:45:44.212Z",
    "modified": "2019-04-29T18:59:16.596Z",
    "relationship_type": "uses",
    "description": "[TEMP.Veles](https://attack.mitre.org/groups/G0088) has used dynamic DNS.",
    "source_ref": "intrusion-set--9538b1a4-4120-4e2d-bf59-3b11fcab05a4",
    "target_ref": "attack-pattern--20a66013-8dab-4ca3-a67d-766c842c561c",
    "external_references": [
        {
            "source_name": "FireEye TRITON 2019",
            "description": "Miller, S, et al. (2019, April 10). TRITON Actor TTP Profile, Custom Attack Tools, Detections, and ATT&CK Mapping. Retrieved April 16, 2019.",
            "url": "https://www.fireeye.com/blog/threat-research/2019/04/triton-actor-ttp-profile-custom-attack-tools-detections.html"
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ]
}

get_pre_tactics
###############

get_pre_tactics(self, stix_format=True)
***************************************

Extracts all the available tactics STIX objects in the Pre ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of dictionaries

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> pre_tactics = lift.get_pre_tactics()
>>> type(pre_tactics)
<class 'list'>
>>>
>>> type(pre_tactics[0])
<class 'dict'>
>>>
>>> print(pre_tactics[0])
{'external_references': [{'external_id': 'TA0017', 'source_name': 'mitre-attack', 'url': 'https://attack.mitre.org/tactics/TA0017'}], 'object_marking_refs': ['marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168'], 'id': 'x-mitre-tactic--b9f8a273-6167-47cb-89e6-02774d067e24', 'name': 'Organizational Information Gathering', 'created': '2018-10-17T00:14:20.652Z', 'modified': '2018-10-17T00:14:20.652Z', 'type': 'x-mitre-tactic', 'created_by_ref': 'identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5', 'description': 'Organizational information gathering consists of the process of identifying critical organizational elements of intelligence an adversary will need about a target in order to best attack.\xa0 Similar to competitive intelligence, organizational intelligence gathering focuses on understanding the operational tempo of an organization and gathering a deep understanding of the organization and how it operates, in order to best develop a strategy to target it.', 'x_mitre_shortname': 'organizational-information-gathering'}

get_mobile
##########

get_mobile(self, stix_format=True)
**********************************

Extracts all the available STIX objects in the Mobile ATT&CK matrix categorized in the following way:

+--------------------+---------------------+
| ATT&CK Format      | STIX Format         |
+====================+=====================+
| technique          | attack-pattern      |
+--------------------+---------------------+
| mitigation         | course-of-action    |
+--------------------+---------------------+
| group              | intrusion-set       |
+--------------------+---------------------+
| malware            | malware             |
+--------------------+---------------------+
| tool               | tool                |
+--------------------+---------------------+
| relationship       | relationship        |
+--------------------+---------------------+
| tactic             | x-mitre-tactic      |
+--------------------+---------------------+
| matrix             | x-mitre-tactic      |
+--------------------+---------------------+
| identity           | identity            |
+--------------------+---------------------+
| marking-definition | markinng-definition |
+--------------------+---------------------+

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: Dictionary

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> mobile = lift.get_mobile()
>>> type(mobile)
<class 'dict'>
>>>
>>> mobile.keys()
dict_keys(['techniques', 'mitigations', 'groups', 'malware', 'tools', 'relationships', 'tactics', 'matrix', 'identity', 'marking-definition'])
>>>
>>> type(mobile['techniques'])
<class 'list'>
>>> type(mobile['techniques'][0])
<class 'stix2.v20.sdo.AttackPattern'>
>>>
>>> print(mobile['techniques'][0])
{
    "type": "attack-pattern",
    "id": "attack-pattern--c6a146ae-9c63-4606-97ff-e261e76e8380",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2019-02-01T17:29:43.503Z",
    "modified": "2019-02-01T17:29:43.503Z",
    "name": "Web Service",
    "description": "Adversaries may use an existing, legitimate external Web service as a means for relaying commands to a compromised system.\n\nThese commands may also include pointers to command and control (C2) infrastructure. Adversaries may post content, known as a dead drop resolver, on Web services with embedded (and often obfuscated/encoded) domains or IP addresses. Once infected, victims will reach out to and be redirected by these resolvers.\n\nPopular websites and social media acting as a mechanism for C2 may give a significant amount of cover due to the likelihood that hosts within a network are already communicating with them prior to a compromise. Using common services, such as those offered by Google or Twitter, makes it easier for adversaries to hide in expected noise. Web service providers commonly use SSL/TLS encryption, giving adversaries an added level of protection.\n\nUse of Web services may also protect back-end C2 infrastructure from discovery through malware binary analysis while also enabling operational resiliency (since this infrastructure may be dynamically changed).",
    "kill_chain_phases": [
        {
            "kill_chain_name": "mitre-mobile-attack",
            "phase_name": "command-and-control"
        }
    ],
    "external_references": [
        {
            "source_name": "mitre-mobile-attack",
            "url": "https://attack.mitre.org/techniques/T1481",
            "external_id": "T1481"
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_platforms": [
        "Android",
        "iOS"
    ],
    "x_mitre_tactic_type": [
        "Post-Adversary Device Access"
    ],
    "x_mitre_version": "1.0"
}

get_mobile_techniques
#####################

get_mobile_techniques(self, stix_format=True)
*********************************************

Extracts all the available techniques STIX objects in the Mobile ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sdo.AttackPattern objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> mobile_techniques = lift.get_mobile_techniques()
>>> type(mobile_techniques)
<class 'list'>
>>>
>>> type(mobile_techniques[0])
<class 'stix2.v20.sdo.AttackPattern'>
>>>
>>> print(mobile_techniques[0])
{
    "type": "attack-pattern",
    "id": "attack-pattern--c6a146ae-9c63-4606-97ff-e261e76e8380",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2019-02-01T17:29:43.503Z",
    "modified": "2019-02-01T17:29:43.503Z",
    "name": "Web Service",
    "description": "Adversaries may use an existing, legitimate external Web service as a means for relaying commands to a compromised system.\n\nThese commands may also include pointers to command and control (C2) infrastructure. Adversaries may post content, known as a dead drop resolver, on Web services with embedded (and often obfuscated/encoded) domains or IP addresses. Once infected, victims will reach out to and be redirected by these resolvers.\n\nPopular websites and social media acting as a mechanism for C2 may give a significant amount of cover due to the likelihood that hosts within a network are already communicating with them prior to a compromise. Using common services, such as those offered by Google or Twitter, makes it easier for adversaries to hide in expected noise. Web service providers commonly use SSL/TLS encryption, giving adversaries an added level of protection.\n\nUse of Web services may also protect back-end C2 infrastructure from discovery through malware binary analysis while also enabling operational resiliency (since this infrastructure may be dynamically changed).",
    "kill_chain_phases": [
        {
            "kill_chain_name": "mitre-mobile-attack",
            "phase_name": "command-and-control"
        }
    ],
    "external_references": [
        {
            "source_name": "mitre-mobile-attack",
            "url": "https://attack.mitre.org/techniques/T1481",
            "external_id": "T1481"
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_platforms": [
        "Android",
        "iOS"
    ],
    "x_mitre_tactic_type": [
        "Post-Adversary Device Access"
    ],
    "x_mitre_version": "1.0"
}

get_mobile_mitigations
######################

get_mobile_mitigations(self, stix_format=True)
**********************************************

Extracts all the available mitigations STIX objects in the Mobile ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sdo.CourseOfAction objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> mobile_mitigations = lift.get_mobile_mitigations()
>>> type(mobile_mitigations)
<class 'list'>
>>>
>>> type(mobile_mitigations[0])
<class 'stix2.v20.sdo.CourseOfAction'>
>>>
>>> print(mobile_mitigations[0])
{
    "type": "course-of-action",
    "id": "course-of-action--25dc1ce8-eb55-4333-ae30-a7cb4f5894a1",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2017-10-25T14:48:53.732Z",
    "modified": "2018-10-17T00:14:20.652Z",
    "name": "Application Developer Guidance",
    "description": "This mitigation describes any guidance or training given to developers of applications to avoid introducing security weaknesses that an adversary may be able to take advantage of.",
    "external_references": [
        {
            "source_name": "mitre-mobile-attack",
            "url": "https://attack.mitre.org/mitigations/M1013",
            "external_id": "M1013"
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_old_attack_id": "MOB-M1013",
    "x_mitre_version": "1.0"
}

get_mobile_groups
#################

get_mobile_groups(self, stix_format=True)
*****************************************

Extracts all the available groups STIX objects in the Mobile ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sdo.IntrusionSet objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> mobile_groups = lift.get_mobile_groups()
>>> type(mobile_groups)
<class 'list'>
>>>
>>> type(mobile_groups[0])
<class 'stix2.v20.sdo.IntrusionSet'>
>>>
>>> print(mobile_groups[0])
{
    "type": "intrusion-set",
    "id": "intrusion-set--bef4c620-0787-42a8-a96d-b7eb6e85917c",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2017-05-31T21:31:48.664Z",
    "modified": "2019-04-29T18:16:13.040Z",
    "name": "APT28",
    "description": "[APT28](https://attack.mitre.org/groups/G0007) is a threat group that has been attributed to Russia's Main Intelligence Directorate of the Russian General Staff by a July 2018 U.S. Department of Justice indictment. This group reportedly compromised the Hillary Clinton campaign, the Democratic National Committee, and the Democratic Congressional Campaign Committee in 2016 in an attempt to interfere with the U.S. presidential election. [APT28](https://attack.mitre.org/groups/G0007) has been active since at least January 2007.(Citation: DOJ GRU Indictment Jul 2018) (Citation: Ars Technica GRU indictment Jul 2018) (Citation: Crowdstrike DNC June 2016) (Citation: FireEye APT28) (Citation: SecureWorks TG-4127) (Citation: FireEye APT28 January 2017) (Citation: GRIZZLY STEPPE JAR) (Citation: Sofacy DealersChoice) (Citation: Palo Alto Sofacy 06-2018) (Citation: Symantec APT28 Oct 2018)",
    "aliases": [
        "APT28",
        "SNAKEMACKEREL",
        "Swallowtail",
        "Group 74",
        "Sednit",
        "Sofacy",
        "Pawn Storm",
        "Fancy Bear",
        "STRONTIUM",
        "Tsar Team",
        "Threat Group-4127",
        "TG-4127"
    ],
    "external_references": [
        {
            "source_name": "mitre-attack",
            "url": "https://attack.mitre.org/groups/G0007",
            "external_id": "G0007"
        },
        {
            "source_name": "APT28",
            "description": "(Citation: FireEye APT28) (Citation: SecureWorks TG-4127) (Citation: Crowdstrike DNC June 2016) (Citation: Kaspersky Sofacy) (Citation: ESET Sednit Part 3) (Citation: Ars Technica GRU indictment Jul 2018)(Citation: Talos Seduploader Oct 2017)(Citation: Symantec APT28 Oct 2018)(Citation: Securelist Sofacy Feb 2018)"
        },
        {
            "source_name": "SNAKEMACKEREL",
            "description": "(Citation: Accenture SNAKEMACKEREL Nov 2019)"
        },
        {
            "source_name": "Swallowtail",
            "description": "(Citation: Symantec APT28 Oct 2018)"
        },
        {
            "source_name": "Group 74",
            "description": "(Citation: Talos Seduploader Oct 2017)"
        },
        {
            "source_name": "Sednit",
            "description": "This designation has been used in reporting both to refer to the threat group and its associated malware JHUHUGIT. (Citation: FireEye APT28 January 2017) (Citation: SecureWorks TG-4127) (Citation: Kaspersky Sofacy) (Citation: Ars Technica GRU indictment Jul 2018)"
        },
        {
            "source_name": "Sofacy",
            "description": "This designation has been used in reporting both to refer to the threat group and its associated malware. (Citation: FireEye APT28) (Citation: SecureWorks TG-4127) (Citation: Crowdstrike DNC June 2016) (Citation: ESET Sednit Part 3) (Citation: Ars Technica GRU indictment Jul 2018)(Citation: Talos Seduploader Oct 2017)"
        },
        {
            "source_name": "Pawn Storm",
            "description": "(Citation: SecureWorks TG-4127) (Citation: ESET Sednit Part 3)"
        },
        {
            "source_name": "Fancy Bear",
            "description": "(Citation: Crowdstrike DNC June 2016) (Citation: Kaspersky Sofacy) (Citation: ESET Sednit Part 3) (Citation: Ars Technica GRU indictment Jul 2018)(Citation: Talos Seduploader Oct 2017)(Citation: Symantec APT28 Oct 2018)(Citation: Securelist Sofacy Feb 2018)"
        },
        {
            "source_name": "STRONTIUM",
            "description": "(Citation: Kaspersky Sofacy) (Citation: ESET Sednit Part 3)"
        },
        {
            "source_name": "Tsar Team",
            "description": "(Citation: ESET Sednit Part 3)(Citation: Talos Seduploader Oct 2017)(Citation: Talos Seduploader Oct 2017)"
        },
        {
            "source_name": "Threat Group-4127",
            "description": "(Citation: SecureWorks TG-4127)"
        },
        {
            "source_name": "TG-4127",
            "description": "(Citation: SecureWorks TG-4127)"
        },
        {
            "source_name": "DOJ GRU Indictment Jul 2018",
            "description": "Mueller, R. (2018, July 13). Indictment - United States of America vs. VIKTOR BORISOVICH NETYKSHO, et al. Retrieved September 13, 2018.",
            "url": "https://www.justice.gov/file/1080281/download"
        },
        {
            "source_name": "Ars Technica GRU indictment Jul 2018",
            "description": "Gallagher, S. (2018, July 27). How they did it (and will likely try again): GRU hackers vs. US elections. Retrieved September 13, 2018.",
            "url": "https://arstechnica.com/information-technology/2018/07/from-bitly-to-x-agent-how-gru-hackers-targeted-the-2016-presidential-election/"
        },
        {
            "source_name": "Crowdstrike DNC June 2016",
            "description": "Alperovitch, D.. (2016, June 15). Bears in the Midst: Intrusion into the Democratic National Committee. Retrieved August 3, 2016.",
            "url": "https://www.crowdstrike.com/blog/bears-midst-intrusion-democratic-national-committee/"
        },
        {
            "source_name": "FireEye APT28",
            "description": "FireEye. (2015). APT28: A WINDOW INTO RUSSIA\u2019S CYBER ESPIONAGE OPERATIONS?. Retrieved August 19, 2015.",
            "url": "https://www.fireeye.com/content/dam/fireeye-www/global/en/current-threats/pdfs/rpt-apt28.pdf"
        },
        {
            "source_name": "SecureWorks TG-4127",
            "description": "SecureWorks Counter Threat Unit Threat Intelligence. (2016, June 16). Threat Group-4127 Targets Hillary Clinton Presidential Campaign. Retrieved August 3, 2016.",
            "url": "https://www.secureworks.com/research/threat-group-4127-targets-hillary-clinton-presidential-campaign"
        },
        {
            "source_name": "FireEye APT28 January 2017",
            "description": "FireEye iSIGHT Intelligence. (2017, January 11). APT28: At the Center of the Storm. Retrieved January 11, 2017.",
            "url": "https://www2.fireeye.com/rs/848-DID-242/images/APT28-Center-of-Storm-2017.pdf"
        },
        {
            "source_name": "GRIZZLY STEPPE JAR",
            "description": "Department of Homeland Security and Federal Bureau of Investigation. (2016, December 29). GRIZZLY STEPPE \u2013 Russian Malicious Cyber Activity. Retrieved January 11, 2017.",
            "url": "https://www.us-cert.gov/sites/default/files/publications/JAR_16-20296A_GRIZZLY%20STEPPE-2016-1229.pdf"
        },
        {
            "source_name": "Sofacy DealersChoice",
            "description": "Falcone, R. (2018, March 15). Sofacy Uses DealersChoice to Target European Government Agency. Retrieved June 4, 2018.",
            "url": "https://researchcenter.paloaltonetworks.com/2018/03/unit42-sofacy-uses-dealerschoice-target-european-government-agency/"
        },
        {
            "source_name": "Palo Alto Sofacy 06-2018",
            "description": "Lee, B., Falcone, R. (2018, June 06). Sofacy Group\u2019s Parallel Attacks. Retrieved June 18, 2018.",
            "url": "https://researchcenter.paloaltonetworks.com/2018/06/unit42-sofacy-groups-parallel-attacks/"
        },
        {
            "source_name": "Symantec APT28 Oct 2018",
            "description": "Symantec Security Response. (2018, October 04). APT28: New Espionage Operations Target Military and Government Organizations. Retrieved November 14, 2018.",
            "url": "https://www.symantec.com/blogs/election-security/apt28-espionage-military-government"
        },
        {
            "source_name": "Kaspersky Sofacy",
            "description": "Kaspersky Lab's Global Research and Analysis Team. (2015, December 4). Sofacy APT hits high profile targets with updated toolset. Retrieved December 10, 2015.",
            "url": "https://securelist.com/sofacy-apt-hits-high-profile-targets-with-updated-toolset/72924/"
        },
        {
            "source_name": "ESET Sednit Part 3",
            "description": "ESET. (2016, October). En Route with Sednit - Part 3: A Mysterious Downloader. Retrieved November 21, 2016.",
            "url": "http://www.welivesecurity.com/wp-content/uploads/2016/10/eset-sednit-part3.pdf"
        },
        {
            "source_name": "Talos Seduploader Oct 2017",
            "description": "Mercer, W., et al. (2017, October 22). \"Cyber Conflict\" Decoy Document Used in Real Cyber Conflict. Retrieved November 2, 2018.",
            "url": "https://blog.talosintelligence.com/2017/10/cyber-conflict-decoy-document.html"
        },
        {
            "source_name": "Securelist Sofacy Feb 2018",
            "description": "Kaspersky Lab's Global Research & Analysis Team. (2018, February 20). A Slice of 2017 Sofacy Activity. Retrieved November 27, 2018.",
            "url": "https://securelist.com/a-slice-of-2017-sofacy-activity/83930/"
        },
        {
            "source_name": "Accenture SNAKEMACKEREL Nov 2019",
            "description": "Accenture Security. (2019, November 29). SNAKEMACKEREL. Retrieved April 15, 2019.",
            "url": "https://www.accenture.com/t20181129T203820Z__w__/us-en/_acnmedia/PDF-90/Accenture-snakemackerel-delivers-zekapab-malware.pdf#zoom=50"
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_contributors": [
        "Emily Ratliff, IBM",
        "Richard Gold, Digital Shadows"
    ],
    "x_mitre_version": "2.0"
}

get_mobile_malware
##################

get_mobile_malware(self, stix_format=True)
******************************************

Extracts all the available malware STIX objects in the Mobile ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sdo.Malware objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> mobile_malware = lift.get_mobile_malware()
>>> type(mobile_malware)
<class 'list'>
>>>
>>> type(mobile_malware[0])
<class 'stix2.v20.sdo.Malware'>
>>>
>>> print(mobile_malware[0])
{
    "type": "malware",
    "id": "malware--08784a9d-09e9-4dce-a839-9612398214e8",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2018-10-17T00:14:20.652Z",
    "modified": "2018-12-11T20:40:31.461Z",
    "name": "Allwinner",
    "description": "[Allwinner](https://attack.mitre.org/software/S0319) is a company that supplies processors used in Android tablets and other devices. A Linux kernel distributed by [Allwinner](https://attack.mitre.org/software/S0319) for use on these devices reportedly contained a backdoor. (Citation: HackerNews-Allwinner)",
    "labels": [
        "malware"
    ],
    "external_references": [
        {
            "source_name": "mitre-mobile-attack",
            "url": "https://attack.mitre.org/software/S0319",
            "external_id": "S0319"
        },
        {
            "source_name": "Allwinner",
            "description": "(Citation: HackerNews-Allwinner)"
        },
        {
            "source_name": "HackerNews-Allwinner",
            "description": "Mohit Kumar. (2016, May 11). Kernel Backdoor found in Gadgets Powered by Popular Chinese ARM Maker. Retrieved September 18, 2018.",
            "url": "https://thehackernews.com/2016/05/android-kernal-exploit.html"
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_aliases": [
        "Allwinner"
    ],
    "x_mitre_old_attack_id": "MOB-S0035",
    "x_mitre_platforms": [
        "Android"
    ],
    "x_mitre_version": "1.1"
}

get_mobile_tools
################

get_mobile_tools(self, stix_format=True)
****************************************

Extracts all the available tools STIX objects in the Mobile ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sdo.Tool objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> mobile_tools = lift.get_mobile_tools()
>>> type(mobile_tools)
<class 'list'>
>>>
>>> type(mobile_tools[0])
<class 'stix2.v20.sdo.Tool'>
>>>
>>> print(mobile_tools[0])
{
    "type": "tool",
    "id": "tool--da21929e-40c0-443d-bdf4-6b60d15448b4",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2017-10-25T14:48:48.609Z",
    "modified": "2018-12-11T20:40:31.461Z",
    "name": "Xbot",
    "description": "[Xbot](https://attack.mitre.org/software/S0298) is an Android malware family that was observed in 2016 primarily targeting Android users in Russia and Australia. (Citation: PaloAlto-Xbot)",
    "labels": [
        "tool"
    ],
    "external_references": [
        {
            "source_name": "mitre-mobile-attack",
            "url": "https://attack.mitre.org/software/S0298",
            "external_id": "S0298"
        },
        {
            "source_name": "Xbot",
            "description": "(Citation: PaloAlto-Xbot)"
        },
        {
            "source_name": "PaloAlto-Xbot",
            "description": "Cong Zheng, Claud Xiao and Zhi Xu. (2016, February 18). New Android Trojan \u201cXbot\u201d Phishes Credit Cards and Bank Accounts, Encrypts Devices for Ransom. Retrieved December 21, 2016.",
            "url": "http://researchcenter.paloaltonetworks.com/2016/02/new-android-trojan-xbot-phishes-credit-cards-and-bank-accounts-encrypts-devices-for-ransom/"
        }
    ],
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ],
    "x_mitre_aliases": [
        "Xbot"
    ],
    "x_mitre_old_attack_id": "MOB-S0014",
    "x_mitre_platforms": [
        "Android"
    ],
    "x_mitre_version": "1.1"
}

get_mobile_relationships
########################

get_mobile_relationships(self, stix_format=True)
************************************************

Extracts all the available relationships STIX objects in the Mobile ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of stix2.v20.sro.Relationship objects

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> mobile_relationships = lift.get_mobile_relationships()
>>> type(mobile_relationships)
<class 'list'>
>>>
>>> type(mobile_relationships[0])
<class 'stix2.v20.sro.Relationship'>
>>>
>>> print(mobile_relationships[0])
{
    "type": "relationship",
    "id": "relationship--6186ed87-69a1-43e7-bb60-76527d287e31",
    "created_by_ref": "identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5",
    "created": "2019-04-29T19:35:31.074Z",
    "modified": "2019-04-29T19:35:31.074Z",
    "relationship_type": "revoked-by",
    "source_ref": "attack-pattern--0bcc4ec1-a897-49a9-a9ff-c00df1d1209d",
    "target_ref": "attack-pattern--2d646840-f6f5-4619-a5a8-29c8316bbac5",
    "object_marking_refs": [
        "marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168"
    ]
}

get_mobile_tactics
##################

get_mobile_tactics(self, stix_format=True)
******************************************

Extracts all the available tactics STIX objects in the Mobile ATT&CK matrix

Parameters:

    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List of dictionaries

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> mobile_tactics = lift.get_mobile_tactics()
>>> type(mobile_tactics)
<class 'list'>
>>>
>>> type(mobile_tactics[0])
<class 'dict'>
>>>
>>> print(mobile_tactics[0])
{'external_references': [{'external_id': 'TA0030', 'source_name': 'mitre-attack', 'url': 'https://attack.mitre.org/tactics/TA0030'}], 'object_marking_refs': ['marking-definition--fa42a846-8d90-4e51-bc29-71d5b4802168'], 'id': 'x-mitre-tactic--987cda6d-eb77-406b-bf68-bcb5f3d2e1df', 'name': 'Defense Evasion', 'created': '2018-10-17T00:14:20.652Z', 'modified': '2018-10-17T00:14:20.652Z', 'type': 'x-mitre-tactic', 'created_by_ref': 'identity--c78cb6e5-0c4b-4611-8297-d1b8b55e40b5', 'description': 'Defense evasion consists of techniques an adversary may use to evade detection or avoid other defenses. Sometimes these actions are the same as or variations of techniques in other categories that have the added benefit of subverting a particular defense or mitigation. Defense evasion may be considered a set of attributes the adversary applies to all other phases of the operation.', 'x_mitre_shortname': 'defense-evasion'}

get_data_sources
################

get_data_sources(self)
**********************

Extracts all data sources mapped to techniques across all matrices.

Returns: List

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()
>>>
>>> lift.get_data_sources()
['Process command-line parameters', 'Process monitoring', 'File monitoring', 'SSL/TLS inspection', 
'Web logs', 'Web application firewall logs', 'Network intrusion detection system', 'Network protocol analysis', 
'Network device logs', 'Netflow/Enclave netflow', 'Sensor health and status', 'Process use of network', 
'BIOS', 'Component firmware', 'Packet capture', 'Application logs', 'Windows Registry', 'Services', 
'Windows event logs', 'API monitoring', 'Kernel drivers', 'MBR', 'DNS records', 'PowerShell logs', 
'Anti-virus', 'Email gateway', 'DLL monitoring', 'Authentication logs', 'Web proxy', 'Windows Error Reporting', 
'System calls', 'Data loss prevention', 'Third-party application logs', 'Binary file metadata', 
'Asset management', 'Detonation chamber', 'Mail server', 'Loaded DLLs', 'Browser extensions', 
'Access tokens', 'Environment variable', 'User interface', 'Malware reverse engineering',
'Digital certificate logs', 'Disk forensics', 'Host network interface', 'WMI Objects', 'VBR', 'Named Pipes', 'EFI']

get_techniques_by_datasources
#############################

get_techniques_by_datasources(self, *args, stix_format=True)
************************************************************

Extracts all techniques mapped to one or multiple data sources.

Parameters:

    * ``*args``: one or more data sources ("datasource1", "datsasource2")
    * ``stix_format``: returns results in original STIX format or friendly syntax ('attack-pattern' or 'technique')

Returns: List

Examples
********

>>> from attackcti import attack_client
>>> lift = attack_client()

>>> techniques = lift.get_techniques_by_datasources("windows event logs")
>>> len(techniques)
22
>>> for t in techniques:
...     print(t['name'],t['x_mitre_data_sources'])
... 
Inhibit System Recovery ['Windows Registry', 'Services', 'Windows event logs', 'Process command-line parameters', 'Process monitoring']
Group Policy Modification ['Windows event logs']
File Permissions Modification ['File monitoring', 'Process monitoring', 'Process command-line parameters', 'Windows event logs']
BITS Jobs ['API monitoring', 'Packet capture', 'Windows event logs']
CMSTP ['Process monitoring', 'Process command-line parameters', 'Process use of network', 'Windows event logs']
Control Panel Items ['API monitoring', 'Binary file metadata', 'DLL monitoring', 'Windows Registry', 'Windows event logs', 'Process command-line parameters', 'Process monitoring']
Indirect Command Execution ['File monitoring', 'Process monitoring', 'Process command-line parameters', 'Windows event logs']
Kerberoasting ['Windows event logs']
SIP and Trust Provider Hijacking ['API monitoring', 'Application logs', 'DLL monitoring', 'Loaded DLLs', 'Process monitoring', 'Windows Registry', 'Windows event logs']
Distributed Component Object Model ['API monitoring', 'Authentication logs', 'DLL monitoring', 'Packet capture', 'Process monitoring', 'Windows Registry', 'Windows event logs']
Dynamic Data Exchange ['API monitoring', 'DLL monitoring', 'Process monitoring', 'Windows Registry', 'Windows event logs']
Hooking ['API monitoring', 'Binary file metadata', 'DLL monitoring', 'Loaded DLLs', 'Process monitoring', 'Windows event logs']
Image File Execution Options Injection ['Process monitoring', 'Windows Registry', 'Windows event logs']
LLMNR/NBT-NS Poisoning and Relay ['Windows event logs', 'Windows Registry', 'Packet capture', 'Netflow/Enclave netflow']
SID-History Injection ['API monitoring', 'Authentication logs', 'Windows event logs']
Create Account ['Process monitoring', 'Process command-line parameters', 'Authentication logs', 'Windows event logs']
Modify Registry ['Windows Registry', 'File monitoring', 'Process monitoring', 'Process command-line parameters', 'Windows event logs']
Account Manipulation ['Authentication logs', 'API monitoring', 'Windows event logs', 'Packet capture']
Indicator Removal on Host ['File monitoring', 'Process monitoring', 'Process command-line parameters', 'API monitoring', 'Windows event logs']
Scheduled Task ['File monitoring', 'Process monitoring', 'Process command-line parameters', 'Windows event logs']
New Service ['Windows Registry', 'Process monitoring', 'Process command-line parameters', 'Windows event logs']
Obfuscated Files or Information ['Network protocol analysis', 'Process use of network', 'File monitoring', 
'Malware reverse engineering', 'Binary file metadata', 'Process command-line parameters', 'Environment variable', 
'Process monitoring', 'Windows event logs', 'Network intrusion detection system', 'Email gateway', 'SSL/TLS inspection']