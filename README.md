Following commands need to be executed for the cronjob to run.


   To allow the cronjob to mount the hostpath

      ! oc adm policy add-scc-to-user hostmount-anyuid system:serviceaccount:nvs-rstudio-ide:ssp-dc-scaler
   
   
   To patch this cronjob

      ! oc login 

      ! oc project <project-name>

      ! oc apply -f <file-name.yaml>

   
   To delete the changes
   
      ! oc delete -f <file-name.yaml>
 
   Jupyterhub issues

   If Singleuser Notebook startup times out with 504 Gateway Time-out. Potential reason is Ingress timeout for HTTP traffic after 30s. Patch your Route to set extended timeout.

   Referrence Material https://access.redhat.com/documentation/en-us/red_hat_process_automation_manager/7.1/html/managing_and_monitoring_process_server/configuring-openshift-connection-timeout-proc

      ! oc patch route <route-name> -p  '{"metadata":{"annotations":{"haproxy.router.openshift.io/timeout":"90s"}}}'
