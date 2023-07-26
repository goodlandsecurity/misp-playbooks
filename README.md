# MISP playbooks

MISP playbooks address common use-cases encountered by SOCs, CSIRTs or CTI teams to detect, react and analyse specific intelligence received by MISP.

The MISP playbooks are built with Jupyter notebooks and contain
- **Documentation** in **Markdown** format, including text and graphical elements;
- **Computer code** in the **Python** programming language, primarily with the use of PyMISP to interact with MISP and other sources for enrichment and notification.

## Documentation

This repository contains the documentation to get started with MISP playbooks.

- The [MISP playbook structure](documentation/MISP%20playbook%20structure.md) and [Jupyter notebook example](documentation/MISP%20playbook.ipynb) describe the structure of the MISP playbooks.
- The [MISP playbook guidelines](documentation/MISP%20playbook%20guidelines.md) help you with building and maintaining your playbooks.
- The [MISP playbook technical documentation](documentation/MISP%20playbook%20technical%20documentation.md) helps you with setting up your environment to run the playbooks.
- The [MISP playbook FAQ](documentation/MISP%20playbook%20FAQ.md) contains tips and tricks for using and developing playbooks.

## Playbooks

The repository contains these playbooks

| Title  | Purpose  | Playbook  | Issue |
|:---|:---|:---|---|
| **Query CVE information** | Query MISP events for the use of specific CVEs. List these events with their context (galaxies, focus on MITRE ATT&CK).<br>Query public sources (CVE search, vulners, XForceExchange, exploitdb) for additional CVE information.<br>Results are stored in the playbook, in a MISP event and sent to Mattermost and TheHive.| [MISP Playbook](misp-playbooks/pb_query_cve_information-with_output.ipynb)<br><br>[MISP Playbook with output](misp-playbooks/pb_query_cve_information-with_output.ipynb) |[25](https://github.com/MISP/misp-playbooks/issues/25)|
| **Query domain reputation** |Query enabled OSINT feeds and MISP events for matches with one or more domain name(s).<br>Query URLscan for historical scans related to these domains and extract screenshots.<br>Use MISP modules to look up the DNS resolutions and query VirusTotal, Shodan and URLhaus for information related to the domains.<br>Results are stored in the playbook, in a MISP event and sent to Mattermost and TheHive.|[MISP Playbook](misp-playbooks/pb_query_domain_reputation.ipynb)<br><br>[MISP Playbook with output](misp-playbooks/pb_query_domain_reputation-with_output.ipynb)|[13](https://github.com/MISP/misp-playbooks/issues/13) |
| **Create a custom MISP warninglist** |Create a custom MISP warninglist with a set of entries provided by the analyst as input. A check is done if the warninglist already exists. If the warninglist exists then the entries are added to the existing warninglist. When the warninglist is created the MISP events are queried for matches ('retro-search').<br>Query Shodan and VirusTotal for matches with entries in the warninglist. The result of the creation of the warninglist as well as the matches is summarised aand sent to Mattermost and added as an alert in TheHive. |[MISP Playbook](misp-playbooks/pb_create_custom_MISP_warninglist.ipynb)<br><br>[MISP Playbook with output](misp-playbooks/pb_create_custom_MISP_warninglist-with_output.ipynb)|[7](https://github.com/MISP/misp-playbooks/issues/7)|
| **Create MISP objects and relationships** |This playbook walks the analyst through the phases of creating MISP objects and adding a relationship between these objects.<br>The playbook is typically *triggered* when an an analyst wants to add related, contextually linked, attributes to a MISP event.<br>The objects are added to a new or an existing MISP event. The playbook prints out a summary that can be used to notify colleagues via Mattermost.<br>The playbook uses an Emotet sample to demonstrate the functionality, with links from a file object to URL and HTTP request objects. It also creates the victim objects.|[MISP Playbook](misp-playbooks/pb_create_MISP_objects_and_relationship.ipynb)<br><br>[MISP Playbook with output](misp-playbooks/pb_create_MISP_objects_and_relationship-with_output.ipynb)|[11](https://github.com/MISP/misp-playbooks/issues/11) | 
| **Create or update a MISP event with information from a phishing incident with a link** |This playbook creates a MISP event with details of a **phishing incident**.<br>The playbook requires the phishing indicators such as the **links**, e-mail body, **headers**, **subject** and **senders** as *input*. It encodex these values as attributes and objects. It creates relationships between the objects and sets default tags and MISP clusters.<br>Query MISP events and OSINT feeds for matches with the indicators. URLscan is queried for the links in the e-mail and historical scan results and screenshots are imported in the playbook and MISP. Use IP and ASN information of the location where the URL is hosted. Submit URLs to Lookyloo for further analysis.<br>A final report with indicators is summarised in the playbook and sent via chat to Mattermost.<br>The results can also be added as an alert to TheHive.|[MISP Playbook](misp-playbooks/pb_create_or_update_a_MISP_event_with_information_from_a_phishing_incident_with_a_link.ipynb)<br><br>[MISP Playbook with output](misp-playbooks/pb_create_or_update_a_MISP_event_with_information_from_a_phishing_incident_with_a_link-with_output.ipynb)|[1](https://github.com/MISP/misp-playbooks/issues/1)|
| **Using timestamps in MISP** | A playbook that documents the different timestamps that are used in MISP.<br>Go through the timestamp for publishing and last changes as well as how these can be used in search queries.<br>Document what changes a timestamp in a MISP event.|[MISP Playbook](misp-playbooks/pb_using_timestamps_in_MISP.ipynb)<br><br>[MISP Playbook with output](misp-playbooks/pb_using_timestamps_in_MISP-with_output.ipynb)|[42](https://github.com/MISP/misp-playbooks/issues/42)|
| **Skeleton MISP playbook** | This playbook can be used as a skeleton (or **template**) to start new MISP playbooks.| Use [MISP playbook guidelines](documentation/MISP%20playbook%20guidelines.md) to create a new MISP playbook.| |
  
## Requesting new playbooks

If you identify a missing playbook then submit a [New MISP playbook proposal](https://github.com/MISP/misp-playbooks/issues) via the GitHub issue tracker.
