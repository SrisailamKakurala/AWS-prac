### **Elastic IP (EIP) - AWS Notes**

1. **Definition**:  
   - A **static, public IPv4 address** provided by AWS for dynamic cloud environments.  
   - It ensures a **fixed IP address** that can be remapped between instances.

2. **Why Elastic IPs Are Needed**:  
   - **Dynamic Public IPs Issue**: Public IPs assigned to EC2 instances change when stopped/restarted.  
   - **Consistency**: EIPs provide a constant IP for hosting services (e.g., websites or APIs).  
   - **Disaster Recovery**: Quickly remap the EIP to another instance if the current one fails.  
   - **DNS Stability**: Avoid breaking DNS records due to changing IPs.  

3. **Key Features**:  
   - **Static & Persistent**: Remains fixed regardless of instance state.  
   - **Reassignable**: Can be attached to or detached from instances as needed.  
   - **Region-Specific**: Available only within the region where it's allocated.

4. **Use Cases**:  
   - Hosting websites, APIs, or services requiring fixed public IPs.  
   - Ensuring uptime during instance scaling, migrations, or failures.

5. **Costs**:  
   - **Free** if attached to a running instance.  
   - **Charged** if not associated with any resource.  

6. **Example Workflow**:  
   - **Allocate**: Request an Elastic IP in the AWS Console.  
   - **Associate**: Attach it to an EC2 instance.  
   - **Reassociate**: Move it to another instance if needed.

---

Elastic IPs are essential for maintaining consistent and reliable connectivity for services running on AWS. They minimize downtime, ensure service continuity, and support disaster recovery.