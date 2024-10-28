# How to Encrypt an Unencrypted RDS DB Instance

Amazon RDS can encrypt your Amazon RDS DB Instances.

When the encrypt option is enabled for the AWS RDS Resources, we are able to encrypt DB Instances, Automated Backups, Read replicas, Snapshots and Logs.

Amazon RDS encrypted DB instances use the AES-256 encryption algorithm to encrypt your data on the server that hosts your Amazon RDS DB instances.

The Encrypt option can be enabled only when you are launching the DB instance, it cannot be enabled after launch. However, copies of unencrypted snapshots can be encrypted.

## Steps

1. Sign in to AWS Management Console**
 
2. **Create an Amazon RDS DB Instance (unencrypted)**
   - Navigate to the RDS service.
   - Click on "Create database".
   - Choose a database engine and configure the instance settings.
   - **Important**: Ensure that the "Enable encryption" option is **not selected**.
   - Complete the creation process and wait for the instance to be available.

3. **Take a Snapshot of the Existing DB Instance**
   - In the RDS console, find your DB instance.
   - Select the instance and click on "Actions".
   - Choose "Take snapshot".
   - Name your snapshot and confirm.

4. **Make a Copy of the Snapshot and Encrypt It**
   - Go to the "Snapshots" section in the RDS console.
   - Select the snapshot you just created.
   - Click on "Actions" and select "Copy snapshot".
   - In the copy settings, enable the "Encryption" option and choose the desired KMS key (or use the default).
   - Name the new encrypted snapshot and confirm the copy.

5. **Restore DB Instance from the Encrypted Snapshot**
   - Go to the "Snapshots" section again.
   - Select the newly created encrypted snapshot.
   - Click on "Actions" and choose "Restore snapshot".
   - Configure the instance settings as needed and complete the restoration process.

6. **Change the Name of the Original DB Instance**
   - Find your original unencrypted DB instance in the RDS console.
   - Select the instance and click on "Modify".
   - Change the DB instance identifier (name) to something different.
   - Apply the changes (you may need to reboot the instance).

7. **Change the Name of the Restored DB Instance to the Original Name**
   - Find the restored encrypted DB instance.
   - Select it and click on "Modify".
   - Change the DB instance identifier to match the original instance's name.
   - Apply the changes.

8. **Delete the Original RDS Instance and Snapshot**
   - Select the original (now renamed) RDS instance.
   - Click on "Actions" and choose "Delete".
   - Confirm the deletion.
   - Go to the "Snapshots" section and select the original unencrypted snapshot.
   - Click on "Actions" and choose "Delete snapshot" to remove it.

## Conclusion
Your original unencrypted RDS DB instance has been successfully replaced with an encrypted version. Always ensure that you have backups and understand the implications of data encryption before performing these actions.
Database encryption is a critical component of a comprehensive security strategy. It helps protect data from unauthorized access, complies with regulatory requirements, mitigates the impact of data breaches, enhances cloud security, 
builds trust with customers, and mitigates insider threats.
