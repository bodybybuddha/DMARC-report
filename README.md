# DMARC-report script with PowerBI and GEO Heatmaps support

Many customers I visit ask me: Do you know a good tool to generate DMARC reports? Do they have support for PowerBI?
And the answer is always the same: Sorry I don’t know a end to end report generation tool that will meet your needs. So to fill this gap i started a project to develop  a own PowerShell DMARC reporting tool that will handle it from end to end and supports PowerBI and GEO lookup. The tool will do the following: 

        1. Connect to the reporting mailbox
        2. Downloads the report attachments
        3. Move the processed item to different folder
        4. Move non DMARC items to a different folder
        5. Unzip the downloaded attachment
        6. Load all the xml data and rearrange the data into a usable csv database
        7. Create disk structure for per month reporting
        8. Create a master html report containing data of last 6 months
        9. Create sub html report per running month
       10. If GEO is enabled enhance the reports with GEO country location information
       11. If GEO is enabled Create country specific reports
       12. If PowerBI is enable upload a incremental dataset to PowerBI API
       13. HTML can be saved directly in a IIS published folder to have end to end automated reporting process
       14. Optional Report to PowerBI
       
A report generated by this code can be viewed here: http://www.tech-savvy.nl/wp-content/dmarc/report/index.html 
A simple report in PowerBi can be viewed here: https://app.powerbi.com/view?r=eyJrIjoiNjJjZDBmN2QtNmQ2OS00ZjgwLWFlZmEtYmVlOTlhMWEzNTIyIiwidCI6ImM3YmEyYWEwLTYxOGItNDA0MS04NTRmLTQ0NjQzZDcxODAwMyIsImMiOjh9
More information about the script is on my blog site: Http://tech-savvy.nl
updates history:
updates: Version 2.0

Fixed issues:
    IP table sometimes truncated the hostname to only 1 character.
    Export of IP table did not export incremental causing errors of duplicate keys in 
    hash table.
New Features:
    Added possibility to add GEO IP lookups using "-geolookupenabled" switch. If the
    switch is used the script will add a additional table with the sources per country.
    Additionaly the country, city, lattitude and longitude will also be send to
    PowerBI if PowerBI switch is enabled.
    Added per domain per country reports to zoom in on countrys.
    Added Power BI integration with the switch "-powerbiuploadenabled". If the switch
    is used the script will do a incremental upload with the powerBI API. This makes it
    possible to create rich reports in PowerBI.  
    Added possibility to add report on failed items only using the "-DMARCfailedonly"
    switch. Only items failing  both alignment checks will be in the report.                                                               
HTML changes:
    Added Reports total of DMARC passed VS DMARC failed.
    Added tables for DMARC alignment of SPF.
    Added tables for DMARC alignment of DKIM.
.


Full version history see readme file
