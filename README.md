Following commands need to be executed for the cronjob to run.
-- To allow the cronjob to mount the hostpath
   ! oc adm policy add-scc-to-user hostmount-anyuid system:serviceaccount:nvs-rstudio-ide:ssp-dc-scaler
   
-- To patch this cronjob
   ! oc login 
   ! oc project <project-name>
   ! oc apply -f <file-name.yaml>
   
-- To delete the changes
   ! oc delete -f <file-name.yaml>
 
