# iVendNext-Demostack-Restore-Guide
iVendNext Demostack Restore Guide
## Step 1: How to restore a MariaDB backup

If you’re using bench (the Frappe CLI tool), you can restore the database using:
    
    bench --site [sitename] --force restore path/to/backup.sql
    
Example

    bench --dev.ravinder.localhost --force restore /backups/20250609_123456-mysite_local-database.sql

## Step 2: Restore all Apps installed on Demostack DB


### Elavon Payment Processor: V1.0.0 (main)

  bench get-app https://github.com/ivendnext/elavon_payment_processor.git --branch main
  bench --site ivenddemostack.localhost install-app elavon_payment_processor
 
### iVendNext: V1.0.0 (Release-1.0)

 NA
 
### iVend Framework: V1.0.0 (Release-1.0)

 NA
 
HW Integration: V1.0.0 (develop)
 bench get-app https://github.com/ivendnext/hw_integration.git --branch develop
 bench --site ivenddemostack.localhost install-app hw_integration
iVend Loyality: V1.0.0 (main)
 bench get-app https://github.com/ivendnext/ivend_loyality.git --branch main
 bench --site ivenddemostack.localhost install-app ivend_loyality
iVendNext POS: V1.0.0 (staging)
 NA
iVendNext Reports: V1.0.0 (main)
 bench get-app https://github.com/ivendnext/iVendNextDashboards.git --branch main
 bench --site ivenddemostack.localhost install-app ivendnext_reports
Ivendnext Theme: V1.0.0 (Release-1.0)
 bench get-app https://github.com/ivendnext/iVendNext-Theme.git --branch Release-1.0
 bench --site ivenddemostack.localhost install-app iVendNext_Theme
Moneris Payment Processor: V1.0.0 (main)
 bench get-app https://github.com/ivendnext/moneris_payment_processor.git --branch main
 bench --site ivenddemostack.localhost install-app moneris_payment_processor
Payments: V1.0.0 (version-15)
 NA
Print Designer: V1.0.0 (main)
 bench get-app https://github.com/frappe/print_designer.git --branch main
 bench --site ivenddemostack.localhost install-app print_designer
Secugen: V1.0.0 (develop)
 bench get-app https://github.com/ivendnext/Secugen.git --branch develop
 bench --site ivenddemostack.localhost install-app secugen
Webshop: V1.0.0 (dev-15)
 bench get-app https://github.com/ivendnext/iVendNextWebShop.git --branch develop
 bench --site ivenddemostack.localhost install-app webshop
