# Simply smarter - Data Layer Overview 

Dashboard 
- [Download](https://raw.githubusercontent.com/dynatrace-ace-services/segment/refs/heads/main/_OverviewWithSegment-Web_Service_Process_Host_0.1.json)  v0.1
- [Demo live](https://guu84124.apps.dynatrace.com/ui/document/v0/#share=a8181e08-be06-4265-8750-bd31bd68b0d3) (internal access)  
(for demo live there is no segment with web application entities, you can use this one `host_group` / `google_cloud`)  


Use case
- legacy application
- cloud native application

Based on segment, this dashboard displays 
- Application / Key User Action / Synthetic 
- Service
- K8s
- Process Group
- Host

![image](https://github.com/user-attachments/assets/3dba6418-a13b-465b-b3a2-4e8298b07371)


The status is 
- red if there is at least one problem is open
- orange if there is at least one problem closed - and no problem open
- green if there is no problem

Drilldown 
- on the entity (new app or classic view)
- on the most recent problem  

![image](https://github.com/user-attachments/assets/ed780cb7-9822-475f-8eb5-66e5a4685899)


Configure the segment, differnt possibility
1) segment based on tags (recommanded)
![image](https://github.com/user-attachments/assets/2f9c910e-a1ad-4f1b-99cc-b8db50a2f05d)
![image](https://github.com/user-attachments/assets/ffd2a9ed-35a1-4e34-ac36-e75e075fe4c3)
```
fetch dt.entity.cloud_application_namespace
| fields namespace = entity.name
| dedup namespace
| sort namespace
```

2) segment based on namespace  
![image](https://github.com/user-attachments/assets/cef64f7e-9ff7-4e88-a11c-0ede6416c630)  

with variables configuration = 

```
fetch dt.entity.cloud_application_namespace
| fields namespace = entity.name
| dedup namespace
| sort namespace
```

3) segment based on host group
![image](https://github.com/user-attachments/assets/91422f93-b5fa-4674-ba3b-1e87c684c6d4)  
with variables configuration =  
```
fetch dt.entity.host_group
| fields hostgroup = entity.name
| sort upper(hostgroup)
```


- the entities

![image](https://github.com/user-attachments/assets/e93af1b2-fb1b-4dbf-b58e-20f4ba920a7e)


