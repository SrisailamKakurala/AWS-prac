### **Pre-Signed URLs in Amazon S3**

---

### **What is a Pre-Signed URL?**
- A **Pre-Signed URL** is a secure, time-limited URL that grants temporary access to a specific S3 object.
- It allows users to upload, download, or perform other actions on an object without requiring permanent access permissions.

---

### **Why Use Pre-Signed URLs?**
1. **Temporary Access**: Share an object securely for a limited time.
2. **Controlled Permissions**: Restrict access to specific operations (GET, PUT, DELETE, etc.).
3. **No Permanent Access Keys**: Avoid sharing your AWS credentials or making objects public.

---

### **How Do Pre-Signed URLs Work?**
1. The **server-side application** generates the URL using AWS SDKs.
2. The generated URL includes:
   - The **S3 object key** (path or filename).
   - The **action** allowed (e.g., GET or PUT).
   - An **expiration timestamp**.
   - A **signature** for authentication.
3. The client uses the URL to access the object without needing AWS credentials.

---

### **Code Example: Generate Pre-Signed URLs in Node.js**

#### **Setup**:
Install the AWS SDK:
```bash
npm install aws-sdk
```

#### **Code to Generate a Pre-Signed URL**:
```javascript
const AWS = require('aws-sdk');

// Initialize S3
const s3 = new AWS.S3({
  region: 'your-region',
  accessKeyId: 'your-access-key-id',
  secretAccessKey: 'your-secret-access-key',
});

// Generate Pre-Signed URL
const generatePresignedUrl = async () => {
  const params = {
    Bucket: 'my-bucket-name',
    Key: 'my-object-key.txt', // File name or path
    Expires: 60, // URL valid for 60 seconds
  };

  try {
    const url = await s3.getSignedUrlPromise('getObject', params);
    console.log('Pre-Signed URL:', url);
  } catch (err) {
    console.error('Error generating URL:', err);
  }
};

generatePresignedUrl();
```

#### **Uploading an Object Using a Pre-Signed URL**:
```javascript
const params = {
  Bucket: 'my-bucket-name',
  Key: 'upload-file.txt', // File name to upload
  Expires: 60, // URL valid for 60 seconds
};

s3.getSignedUrlPromise('putObject', params)
  .then((url) => {
    console.log('Pre-Signed URL (PUT):', url);
    // Use this URL in your client to upload files
  })
  .catch((err) => {
    console.error('Error generating PUT URL:', err);
  });
```

---

### **Use Cases**
1. **File Downloads**:
   - Allow users to download private files without making them public.
   - Example: A user downloads an invoice or report.

2. **File Uploads**:
   - Enable users to upload files directly to S3 without exposing backend credentials.
   - Example: Uploading profile pictures or documents.

3. **Temporary Access for Partners**:
   - Share data with external stakeholders for a limited time.

4. **Secure File Sharing**:
   - Avoid making an object public while sharing it securely with specific users.

---

### **Advantages**
1. **Secure**: Grants temporary and limited access without exposing credentials.
2. **Customizable**: Specify expiration time, object key, and permissions.
3. **No Backend Overhead**: Allows direct client access to S3, reducing server load.

---

### **Expiration of Pre-Signed URLs**
- URLs expire after the time specified in the `Expires` parameter.
- Once expired, the URL becomes invalid, and the user can no longer access the object.

---

### **Best Practices**
1. Use **short expiration times** for enhanced security.
2. Limit permissions (e.g., `GET` only for downloads, `PUT` only for uploads).
3. Monitor usage with **CloudTrail** or **server access logs**.

---

This provides a secure and efficient way to manage object access, perfect for web and mobile applications that need to interact with S3.