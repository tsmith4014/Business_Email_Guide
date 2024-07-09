# Setting Up a Business Email with Cloudflare and Zoho Mail

This guide provides step-by-step instructions to set up a professional business email (for my domain devopschad.com) using Cloudflare and Zoho Mail.

## Prerequisites

1. A custom domain (e.g., devopschad.com).
2. A Cloudflare account to manage DNS settings.
3. A Zoho Mail account for email hosting.

### Step 1: Sign Up for Zoho Mail

1. **Go to Zoho Mail**:

   - Visit the [Zoho Mail website](https://www.zoho.com/mail/zohomail-pricing.html).

2. **Choose a Plan**:

   - Select a plan that suits your needs. Zoho Mail offers a free plan for personal use and various paid plans for business use.

3. **Sign Up**:
   - Click on the "Sign Up Now" button under your chosen plan and follow the instructions to create an account.

### Step 2: Add Your Domain to Zoho Mail

1. **Add Your Domain**:

   - During the setup process, you will be asked to add your domain. Enter your domain name (e.g., devopschad.com).

2. **Verify Domain Ownership**:
   - Zoho Mail will provide you with DNS records to add to your Cloudflare account to verify domain ownership. Typically, this will include a TXT record for verification.

### Step 3: Configure DNS Records in Cloudflare

1. **Log in to Cloudflare**:

   - Go to your [Cloudflare dashboard](https://www.cloudflare.com/login) and log in.

2. **Select Your Domain**:

   - Click on your domain (devopschad.com).

3. **Go to DNS Settings**:

   - Click on the **DNS** tab in the navigation bar.

4. **Remove Existing MX Records** (if any):

   - Identify the existing MX records (e.g., eforwardX.registrar-servers.com).
   - Click on the **Delete** button next to each of these records to remove them.

5. **Add New MX Records for Zoho Mail**:

   - Click on **Add Record** and select **MX** from the dropdown menu.
   - Add the following MX records as provided by Zoho Mail:

     ```
     Type: MX
     Name: @
     Mail Server: mx.zoho.com
     Priority: 10
     ```

     ```
     Type: MX
     Name: @
     Mail Server: mx2.zoho.com
     Priority: 20
     ```

     ```
     Type: MX
     Name: @
     Mail Server: mx3.zoho.com
     Priority: 50
     ```

6. **Add SPF, DKIM, and DMARC Records**:

   - **SPF Record**:

     ```
     Type: TXT
     Name: @
     Value: v=spf1 include:zoho.com ~all
     ```

   - **DKIM Record**:

     ```
     Type: TXT
     Name: zmail._domainkey
     Value: (the long DKIM key provided by Zoho)
     ```

   - **DMARC Record (Optional)**:
     ```
     Type: TXT
     Name: _dmarc
     Value: v=DMARC1; p=none; rua=mailto:your-email@devopschad.com
     ```

### Step 4: Create Email Accounts in Zoho Mail

1. **Log in to Zoho Mail**:

   - Go to the [Zoho Mail Login](https://mail.zoho.com) and log in with your Zoho credentials.

2. **Navigate to User Details**:

   - Go to the **Admin Console**.
   - Click on **User Details**.

3. **Create a New User**:
   - Add a new user with the email address you want (e.g., support@devopschad.com).

### Step 5: Configure Email Client (Optional)

If you prefer to use an email client (e.g., Outlook, Thunderbird, Apple Mail), you need to configure it with Zoho Mail’s IMAP and SMTP settings.

#### IMAP and SMTP Settings for Zoho Mail

- **IMAP Settings**:

  - IMAP Server: imap.zoho.com
  - Port: 993
  - Security: SSL
  - Username: support@devopschad.com
  - Password: Your Zoho Mail password

- **SMTP Settings**:
  - SMTP Server: smtp.zoho.com
  - Port: 465 or 587
  - Security: SSL/TLS
  - Username: support@devopschad.com
  - Password: Your Zoho Mail password

#### Example Configuration in Outlook

1. **Open Outlook** and go to **File** > **Add Account**.
2. **Enter Your Email Address**: support@devopschad.com and click **Connect**.
3. **Choose Account Type**: Select **IMAP**.
4. **Enter IMAP and SMTP Settings**:
   - IMAP Server: imap.zoho.com, Port: 993, Encryption: SSL
   - SMTP Server: smtp.zoho.com, Port: 465 or 587, Encryption: SSL/TLS
   - Username: support@devopschad.com
   - Password: Your Zoho Mail password
5. **Complete Setup**: Follow the prompts to complete the setup.

### Step 6: Set Display Name and Signature in Zoho Mail

1. **Log in to Zoho Mail**:

   - Go to [Zoho Mail Login](https://mail.zoho.com) and log in with your Zoho credentials.

2. **Navigate to Settings**:

   - Click on the **Settings** icon (gear icon) usually found in the top right corner.

3. **Change Display Name**:

   - Go to **Send Mail As** under the **Mail** section.
   - Click on the **Edit** button (pencil icon) next to the email address.
   - Change the display name to **Chad Thompson-Smith** or **DevOpsChad**.
   - Click **Save**.

4. **Set Up Email Signature**:

   - In the Settings menu, find and click on **Signatures** under the **Mail** section.
   - Click on **Add New Signature**.
   - Enter the following details:

     - **Signature Name**: Professional Signature
     - **Signature Content**:

     ```
     Best regards,
     Chad Thompson-Smith
     DevOps and Cloud Engineer | Software Developer
     Email: support@devopschad.com
     Website: www.devopschad.com
     LinkedIn: https://www.linkedin.com/in/chad-thompson-smith/

     ---
     "Empowering businesses with cloud solutions, innovative software development, and AI to increase productivity and accelerate learning."
     ```

   - Highlight the text and use the formatting toolbar to set **Arial** as the font type and **12 pt** as the font size.
   - Click on **Save**.

### Testing Your Setup

1. **Send a Test Email**: Send an email from support@devopschad.com to another email address you own (e.g., chjthomps@gmail.com) to ensure that sending works.
2. **Receive a Test Email**: Send an email to support@devopschad.com from another email address to ensure that receiving works.

### Conclusion

By following these steps, you have successfully set up a professional business email using Cloudflare and Zoho Mail. You can now send and receive emails using your custom domain (support@devopschad.com), ensuring a professional appearance for your business communications.
