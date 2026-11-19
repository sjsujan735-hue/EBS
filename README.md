# WORKING WITH EBS
## NAME: Sujan S
## REG NO: 212225220108

## Aim

To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.

---

## Algorithm / Steps

1. Create a new Amazon EBS volume with a size of 1 GiB.
2. Select the same Availability Zone as the EC2 instance.
3. Attach the EBS volume to the EC2 instance using `/dev/sdb`.
4. Connect to the EC2 instance using AWS Systems Manager Session Manager.
5. Check the available storage using `df -h`.
6. Create an `ext3` file system on the EBS volume.
7. Create the `/mnt/data-store` directory.
8. Mount the EBS volume to `/mnt/data-store`.
9. Configure `/etc/fstab` for automatic mounting.
10. Verify that the EBS volume is successfully mounted.
11. Create `file.txt` inside the mounted EBS volume.
12. Verify the contents of the created file.
13. Create an EBS snapshot named `My Snapshot`.
14. Delete `file.txt` from the original EBS volume.
15. Create a new EBS volume from the snapshot.
16. Attach the restored volume to the EC2 instance using `/dev/sdc`.
17. Create the `/mnt/data-store2` directory.
18. Mount the restored volume to `/mnt/data-store2`.
19. Verify that `file.txt` has been successfully restored.

---

## Program

### 1. Check Available Storage

```bash
df -h
```

### 2. Create an ext3 File System

```bash
sudo mkfs -t ext3 /dev/sdb
```

### 3. Create a Mount Directory

```bash
sudo mkdir /mnt/data-store
```

### 4. Mount the EBS Volume

```bash
sudo mount /dev/sdb /mnt/data-store
```

### 5. Configure Automatic Mounting

```bash
echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
```

### 6. View the File System Configuration

```bash
cat /etc/fstab
```

### 7. Verify the Mounted Volume

```bash
df -h
```

### 8. Create a File in the EBS Volume

```bash
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
```

### 9. Read the File

```bash
cat /mnt/data-store/file.txt
```

### 10. Delete the File

```bash
sudo rm /mnt/data-store/file.txt
```

### 11. Verify File Deletion

```bash
ls /mnt/data-store/
```

### 12. Create a Mount Directory for the Restored Volume

```bash
sudo mkdir /mnt/data-store2
```

### 13. Mount the Restored EBS Volume

```bash
sudo mount /dev/sdc /mnt/data-store2
```

### 14. Verify Snapshot Restoration

```bash
ls /mnt/data-store2/
```

Expected output:

```text
file.txt
```

---

## Outputs
<img width="1917" height="920" alt="Screenshot 2026-11-18 150420" src="https://github.com/user-attachments/assets/103b3a7e-1f9f-4b78-9598-441547a422f6" />
<img width="1917" height="910" alt="Screenshot 2026-11-18 150520" src="https://github.com/user-attachments/assets/84e300b0-247a-4126-98c0-ff8db0c6c330" />
<img width="1917" height="913" alt="Screenshot 2026-11-18 150625" src="https://github.com/user-attachments/assets/3c34d80e-c48f-47e9-a53d-b87cb84a3181" />
<img width="1917" height="916" alt="Screenshot 2026-11-18 150738" src="https://github.com/user-attachments/assets/a6b1772b-411a-44bc-ab16-b191d9881f54" />
<img width="1912" height="913" alt="Screenshot 2026-11-18 150803" src="https://github.com/user-attachments/assets/3beca03a-14fb-45c7-ad9c-f5783d02dc57" />
<img width="1917" height="917" alt="Screenshot 2026-11-18 150941" src="https://github.com/user-attachments/assets/2c19abf8-563c-492e-ab5c-be826260889a" />
<img width="1917" height="907" alt="Screenshot 2026-11-18 151023" src="https://github.com/user-attachments/assets/d2cfcd93-cb2a-478c-b3ef-01682a50933d" />
<img width="1917" height="898" alt="Screenshot 2026-11-18 151041" src="https://github.com/user-attachments/assets/241b9744-cf8b-4aeb-93ff-da65d8f4f5df" />
<img width="1911" height="922" alt="Screenshot 2026-11-18 151301" src="https://github.com/user-attachments/assets/dbb06f47-3bdd-42d2-98e6-6ff7ff6ea62f" />
<img width="1917" height="920" alt="Screenshot 2026-11-18 151320" src="https://github.com/user-attachments/assets/d202ef17-b02f-411a-8a08-68fba20c47a5" />
<img width="1912" height="912" alt="Screenshot 2026-11-18 151441" src="https://github.com/user-attachments/assets/834d232f-749c-4da3-bbbe-63800c264c81" />
<img width="1917" height="907" alt="Screenshot 2026-11-18 152649" src="https://github.com/user-attachments/assets/3e9dbf52-6511-4c98-a216-eda991f62fff" />
<img width="1916" height="951" alt="Screenshot 2026-11-18 152508" src="https://github.com/user-attachments/assets/f394689e-1e24-428f-879c-cdab55f4cf42" />
<img width="1912" height="925" alt="Screenshot 2026-11-18 152745" src="https://github.com/user-attachments/assets/0e4486f6-8e1d-4a65-b74b-05f641f679ce" />
















## Result
Thus, an Amazon EBS volume was successfully created and attached to an Amazon EC2 instance. The volume was formatted with an ext3 file system, mounted, and used for storing data. An EBS snapshot was successfully created as a backup, and a new EBS volume was restored from the snapshot. The previously deleted file.txt was successfully recovered, demonstrating the backup and restore functionality of Amazon EBS.
