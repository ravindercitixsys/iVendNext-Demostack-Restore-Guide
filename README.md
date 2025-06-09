# iVendNext-Demostack-Restore-Guide
iVendNext Demostack Restore Guide
## Step 1: Download the DB backup file from frappe site (https://demostack.ivendnext.com/app/backups)

Download the Database file from the site the DB which need to restore.
This can be download fromdownload backup setion or visit https://{SiteName}/app/backups
    
    ![image](https://github.com/user-attachments/assets/049f8bb7-b1af-49ef-8c34-81c3be559fd5)
    
## Step 1: How to restore a MariaDB backup

If you’re using bench (the Frappe CLI tool), you can restore the database using:
    
    bench --site [sitename] --force restore path/to/backup.sql
    
Example

    bench --dev.ravinder.localhost --force restore /backups/20250609_123456-mysite_local-database.sql

## Step 2: Restore all Apps installed on Demostack DB


### 1. Elavon Payment Processor: V1.0.0 (main)

    bench get-app https://github.com/ivendnext/elavon_payment_processor.git --branch main
    bench --site dev.ravinder.localhost install-app elavon_payment_processor
 
### 2. iVendNext: V1.0.0 (Release-1.0)
As this is laready installed, so no need to install it.

    NA
 
### 3. iVend Framework: V1.0.0 (Release-1.0)
As this is laready installed, so no need to install it.

    NA
 
### 4. HW Integration: V1.0.0 (develop)

    bench get-app https://github.com/ivendnext/hw_integration.git --branch develop
    bench --site dev.ravinder.localhost install-app hw_integration
 
### 5. iVend Loyality: V1.0.0 (main)

    bench get-app https://github.com/ivendnext/ivend_loyality.git --branch main
    bench --site dev.ravinder.localhost install-app ivend_loyality
 
### 6. iVendNext POS: V1.0.0 (staging)
As this is laready installed, so no need to install it.

    NA
 
### 7. iVendNext Reports: V1.0.0 (main)

    bench get-app https://github.com/ivendnext/iVendNextDashboards.git --branch main
    bench --site dev.ravinder.localhost install-app ivendnext_reports
 
### 8. Ivendnext Theme: V1.0.0 (Release-1.0)

    bench get-app https://github.com/ivendnext/iVendNext-Theme.git --branch Release-1.0
    bench --site dev.ravinder.localhost install-app iVendNext_Theme
 
### 9. Moneris Payment Processor: V1.0.0 (main)

    bench get-app https://github.com/ivendnext/moneris_payment_processor.git --branch main
    bench --site dev.ravinder.localhost install-app moneris_payment_processor
 
### 10. Payments: V1.0.0 (version-15)
As this is laready installed, so no need to install it.

    NA
 
### 11. Print Designer: V1.0.0 (main)

    bench get-app https://github.com/frappe/print_designer.git --branch main
    bench --site dev.ravinder.localhost install-app print_designer
 
### 12. Secugen: V1.0.0 (develop)

    bench get-app https://github.com/ivendnext/Secugen.git --branch develop
    bench --site dev.ravinder.localhost install-app secugen
 
### 13. Webshop: V1.0.0 (dev-15)

    bench get-app https://github.com/ivendnext/iVendNextWebShop.git --branch develop
    bench --site dev.ravinder.localhost install-app webshop
