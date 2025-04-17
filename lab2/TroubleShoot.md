# EC2 Troubleshooting: Instance Stopped (Can't Connect)

This guide covers how to simulate and resolve the issue where an EC2 instance is stopped and you’re unable to SSH into it.

---

## Simulating the Issue

1. Go to the AWS Console.
2. Navigate to: **EC2 > Instances**.
3. Select your running Ubuntu instance.
4. Click on **Instance state > Stop instance**.
5. Wait for the instance state to change to “stopped”.
6. Try connecting via SSH:
   ```bash
   ssh -i ubuntu-key.pem ubuntu@<your-ec2-ip>
   ```
7. You’ll see an error such as:
   - `Connection timed out`
   - `ssh: connect to host <IP> port 22: Connection refused`

---

## Fixing the Issue

1. Go back to the **EC2 Dashboard > Instances**.
2. Select the stopped instance.
3. Click **Instance state > Start instance**.
4. Wait for the instance to show as **running**.
5. Check the **Public IPv4 address** — it might have changed.
6. Update your SSH command with the new IP:
   ```bash
   ssh -i ubuntu-key.pem ubuntu@<new-ec2-ip>
   ```

You should now be connected.

---

## Notes

- EC2 instances lose their public IP when stopped unless an **Elastic IP** is attached.
- You can avoid changing IPs by assigning an Elastic IP from the EC2 Dashboard > Elastic IPs.

---

## Add to Project

**Filename**: `ec2-instance-stopped.md`  
**Location**: `cloud-labs/docs/` _(or wherever you store troubleshooting guides)_

````md
# EC2 Issue: Instance Stopped, Can't SSH

**Symptom**: SSH fails with timeout or connection refused.

**Cause**: Instance is in a "stopped" state.

**Fix**:

1. Start the EC2 instance via AWS Console.
2. Confirm the new public IP.
3. SSH using:
   ```bash
   ssh -i ubuntu-key.pem ubuntu@<new-ip>
   ```
````

```

---
```
