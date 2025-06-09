# iVendNext Demostack Restore Guide
iVendNext Demostack Restore Guide
## Step 1: Download the Database Backup File
Download the required Database backup file from the iVendNext Frappe site.

You can download it from the Backups section on your site:

👉 https://{SiteName}/app/backups

   ![image](https://github.com/user-attachments/assets/aa1994ac-7d64-484f-b278-489f549d82c2)

## Step 2: Copy the Backup File to Bench Location
Since you're running bench inside a Linux Docker container, you need to copy the backup file to your container workspace.

Target Path: /workspace/development/ivend-bench

You can copy the file:

Directly into the Docker container
OR

To a volume-mounted folder like /workspace/development/ivend-bench

   ![image](https://github.com/user-attachments/assets/0740683d-8684-4f7a-98e1-c91abf0bf73c)


## Step 3: Restore the MariaDB Backup

You can restore the DB backup using the bench CLI tool:
    
    bench --site [sitename] restore path/to/backup.sql(.gz)
    
Example

    bench --site dev.ravinder.localhost restore demostack_ivendnext_com-database.sql.gz

## Step 4: Restore/Install Required Apps on Demostack DB
Below is the list of apps used on the Demostack and their installation instructions:

### 1. Elavon Payment Processor: V1.0.0 (main)

    bench get-app https://github.com/ivendnext/elavon_payment_processor.git --branch main
    bench --site dev.ravinder.localhost install-app elavon_payment_processor
 
### 2. iVendNext: V1.0.0 (Release-1.0)

Already installed — No action required
 
### 3. iVend Framework: V1.0.0 (Release-1.0)

Already installed — No action required
 
### 4. HW Integration: V1.0.0 (develop)

    bench get-app https://github.com/ivendnext/hw_integration.git --branch develop
    bench --site dev.ravinder.localhost install-app hw_integration
 
### 5. iVend Loyality: V1.0.0 (main)

    bench get-app https://github.com/ivendnext/ivend_loyality.git --branch main
    bench --site dev.ravinder.localhost install-app ivend_loyality
 
### 6. iVendNext POS: V1.0.0 (staging)

 Already installed — No action required
 
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

Already installed — No action required
 
### 11. Print Designer: V1.0.0 (main)

    bench get-app https://github.com/frappe/print_designer.git --branch main
    bench --site dev.ravinder.localhost install-app print_designer
 
### 12. Secugen: V1.0.0 (develop)

    bench get-app https://github.com/ivendnext/Secugen.git --branch develop
    bench --site dev.ravinder.localhost install-app secugen
 
### 13. Webshop: V1.0.0 (dev-15)

    bench get-app https://github.com/ivendnext/iVendNextWebShop.git --branch develop
    bench --site dev.ravinder.localhost install-app webshop

## Step 5: Update encryption_key in site_config.json
After restoring the database, update the encryption_key to match the key used in the backup.

### 1. Open the site_config.json file located at:

    /sites/[sitename]/site_config.json
   
### 2. Replace the encryption_key value with the one from your backup or configuration source.

![image](https://github.com/user-attachments/assets/1d77a8b0-5488-4ebf-9e8b-06f1e357aa8f)

## Step 6: Final Step — Migrate the Site and Start the Bench
### 6.1 Run Database Migration
This step ensures that the database schema is updated and all patches are applied:

    bench --site dev.ravinder.localhost migrate

### 6.2 Start the Frappe Bench
Now start your bench server:
    
    bench start
    
You can now login with user Administrator and the password you choose when creating the site. Your website will now be accessible at location dev.ravinder.localhost:8000/app
