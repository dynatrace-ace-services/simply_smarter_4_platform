# Overview Dashboard with segment

## Legacy project

Based on segment "tag", this dashboard displays 
- Application based only on the satus (Preview metric is coming soon ... ) 
- Service
- Process Group
- Host


![image](https://github.com/user-attachments/assets/d42d76ef-6536-4802-9768-3b5bd82ca9c9)


The status is 
- red if there is at least one problem is open
- orange if there is at least one problem closed - and no problem open
- green if there is no problem

Drilldown 
- on the entity (new app or classic view)
- on the most recent problem  

![image](https://github.com/user-attachments/assets/ed780cb7-9822-475f-8eb5-66e5a4685899)


Configure the segment,
- the variables

![image](https://github.com/user-attachments/assets/503b15d5-6a65-47ef-9401-e3a8f03a7867)

'''fetch dt.entity.host
| expand  tags
| filter matchesPhrase(tags,"app")
| dedup tags
| fields tags'''


- the entities

![image](https://github.com/user-attachments/assets/e93af1b2-fb1b-4dbf-b58e-20f4ba920a7e)

## Cloud Native project

- coming soon
