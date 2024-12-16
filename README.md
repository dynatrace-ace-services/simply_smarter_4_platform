# Simply smarter - Data Layer Overview

Dashboard v0.2
- [Download](https://raw.githubusercontent.com/dynatrace-ace-services/simply_smarter_4_platform/refs/heads/main/Simply%20smarter%20-%20Data%20Layer%20Overview%20.json) (public access)
- [Demo live](https://guu84124.apps.dynatrace.com/ui/document/v0/#share=a8181e08-be06-4265-8750-bd31bd68b0d3) (internal access)  

Use case
- legacy application
- cloud native application

Based on segment for entities 
- Application / Key User Action / Synthetic 
- Service
- Namespace / Workload / Pod
- Process Group
- Host

![image](https://github.com/user-attachments/assets/3dba6418-a13b-465b-b3a2-4e8298b07371)


The status is 
- red if there is at least one problem is open
- orange if there is at least one problem closed - and no problem open
- green if there is no problem

Drilldown, [↗] Open record with
- on the entity (new app or classic view)
- on the most recent problem  

![image](https://github.com/user-attachments/assets/ed780cb7-9822-475f-8eb5-66e5a4685899)


Configure the segment, different possibilities  

Sample 1) segment based on tags (recommanded on process group)
   
![image](https://github.com/user-attachments/assets/2f9c910e-a1ad-4f1b-99cc-b8db50a2f05d)  

with variables configuration = (here `app` is the tag key value to filter)

![image](https://github.com/user-attachments/assets/ffd2a9ed-35a1-4e34-ac36-e75e075fe4c3)
```
fetch dt.entity.host
| expand  tags
| filter matchesPhrase(tags,"app")
| dedup tags
| fields tags
```

Sample 2) segment based on namespace

![image](https://github.com/user-attachments/assets/cef64f7e-9ff7-4e88-a11c-0ede6416c630)  

with variables configuration = 

```
fetch dt.entity.cloud_application_namespace
| fields namespace = entity.name
| dedup namespace
| sort namespace
```

Sample 3) segment based on host group

![image](https://github.com/user-attachments/assets/91422f93-b5fa-4674-ba3b-1e87c684c6d4)  
with variables configuration =  
```
fetch dt.entity.host_group
| fields hostgroup = entity.name
| sort upper(hostgroup)
```

## known limitation
segement variable = 1000 results for a variable   
other limitation : https://docs.dynatrace.com/docs/manage/segments/reference/segments-reference-limits

