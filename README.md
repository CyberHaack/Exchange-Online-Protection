# Exchange-Online-Protection

# How to Create Transport Rule (Mail Flow Rule)in Microsoft Exchange Online to Reduce Phishing Attacks

 ## Objective
 
The primary objective of this project is to help IT/Security admins to set up Mail Flow rule on Microsoft Exchange Online to significantly reduce potential phishing attacks on users/ Groups Mailboxes. 
We all know that phishing attacks is one of the common ways attackers exfiltrate sensitive or confidential user/ organization data, to carry out sinister activities without the affected user's consent. 


### Skills Learned

- Mail Flow 
- Exchange Online Protection
- Mailbox Security

### Tools Needed 
- Microsoft 365/ Office 365 Subscription
- Exchange Admin Role
  
## Humans: The Weakest Link in Cybersecurity
Humans are often the weakest link in the cybersecurity chain. Phishing attacks remain a prevalent threat, with cybercriminals using deceptive emails to trick unsuspecting users into revealing sensitive information or downloading malicious attachments. These attacks can wreak havoc on an organization’s security profile.


## The Role of Transport Rules
Your work as an IT administrator or cybersecurity analyst is essential to the protection of your company. Creating Transport Rules is one practical first step. These rules can be implemented to any cloud provider service that your company uses, including Google, Amazon, and Microsoft. However, for the purpose of this article, I will be using Microsoft 365.

## What Are Mail Flow Rules?
Mail Flow rules, also known as Transport Rules are rules that take action on messages while they’re in transit, not after the message is delivered to the mailbox.

Unlike email forwarding, which occurs after a message is delivered to the mailbox, mail flow rules intercept and process emails before they reach the recipient’s inbox thereby eliminating the likelihood that the recipient will erroneously or naively open it.

For the purpose of this demo, I will be assigning the transport rule to a specific user. However, note that this rule can be created and enforced Org Wide or tenant Wide, it can also be assigned to a group. It all depends on your organization needs/policies. 

# Creating a Transport Rule in Microsoft 365 Admin Center

1. sign in to your office.com account using your credentials, open the Admin Center by the lower left hand corner — Follow the red highlight

   ![IMG-20241110-WA0008](https://github.com/user-attachments/assets/eec877fc-9d5d-432d-872a-d3e47f259567)

2. Click on Show All > Exchange

   ![IMG-20241110-WA0009](https://github.com/user-attachments/assets/07588dbf-509e-4c3d-a504-1b541930fb1c)

   ![IMG-20241110-WA0010](https://github.com/user-attachments/assets/37840d66-b142-47b6-9892-df5fac139db0)

3. Click on the Drop Down arrow for Mail Flow > Rules

![IMG-20241110-WA0013](https://github.com/user-attachments/assets/209babd5-62f3-4eb2-a03e-5a17f20343c7)

4. Add a Rule > Create a New Rule

   ![IMG-20241110-WA0011](https://github.com/user-attachments/assets/11c08ff4-6ee6-44bc-beba-409527c7fc20)

5. Give the rule a preferred name > Define the desired action based on your organization’s policy.
For this demo, I chose to block all emails sent to this user that contains any executable file(.exe).

![IMG-20241110-WA0012](https://github.com/user-attachments/assets/1c466291-ecb6-4928-aee5-7f367b877fde)

![IMG-20241110-WA0018](https://github.com/user-attachments/assets/e37a5141-5c02-4d0a-9b52-43fe99634a9b)

![IMG-20241110-WA0014](https://github.com/user-attachments/assets/6a528603-a9c0-4cea-832e-abcdd0e10517)

![IMG-20241110-WA0016](https://github.com/user-attachments/assets/ca32226e-e6ab-48f6-bc8c-7471f8037966)

6. Set the priority level according to your organization’s policy, then enforce.

Note: The lower the number, the higher the priority level. This means that if I set the priority level to 3, rules with a priority level of 2 will take precedence over the rule set to 3.

![IMG-20241110-WA0015](https://github.com/user-attachments/assets/ae05206e-d4dc-41fe-9310-5ded864c97bc)

7. Choose the severity level according to your organization’s policy > save

   ![IMG-20241110-WA0017](https://github.com/user-attachments/assets/271c08d5-25cb-48cb-a1ef-f9072eb31a92)

8. The image below highlight the summary of the rule I created.

   ![IMG-20241110-WA0019](https://github.com/user-attachments/assets/a51029b9-c583-4e43-8466-b844ab700d9a)


9. It may take some minutes to propagate. After it does, click on the rule you just created and enable the rule by toggling it on.


    ![IMG-20241110-WA0020](https://github.com/user-attachments/assets/5d81889d-33cd-4b31-a2fe-0725b2b4e27d)

10. It’s time to check if our rule is working. Send a mail to the user(s) / Group (s) we enforced this policy on. As per the rule I created, I sent an email with an executable file attachment and got this NDR (Non-delivery Report) immediately. Pay attention to the details in the NDR.

    ![IMG-20241110-WA0024](https://github.com/user-attachments/assets/ed430060-8bdf-4fbb-bb2d-d99a4e721428)

![WhatsApp Image 2024-11-10 at 16 21 48_a720498f](https://github.com/user-attachments/assets/4fc032b5-01aa-4818-81d2-1395293804e2)

![WhatsApp Image 2024-11-10 at 16 09 26_69355a1e](https://github.com/user-attachments/assets/7ade625c-864f-4b61-a74c-4f0c98088c2e)

11. Let’s carry out a message trace to get more information about this rule.
Exchange Admin Center > Start a Trace

Note: As an administrator, you can use the message trace feature in the Exchange admin center (EAC) to track emails in your Microsoft 365 organization. Message tracing lets you check if an email was received, delayed, or delivered.

![IMG-20241110-WA0021](https://github.com/user-attachments/assets/2449246d-3990-4343-90b8-86f3f36b425d)

12. Input the recipient address and search.

    ![IMG-20241110-WA0023](https://github.com/user-attachments/assets/5e88d3eb-f3bc-4db1-bc3c-919ed3de65fc)

13. We can see further details about the message here. The date and time it was sent, the recipient, sender, subject, and the status of the message. As per the enforced rule, the message failed.

    ![IMG-20241110-WA0025](https://github.com/user-attachments/assets/414ab956-0293-4848-afa5-9f4a4594277a)

14. Analyzing the report below provides more details about the message, including why it failed, which rule caused the failure, and who created the rule. Specifically, we can see that a mail flow rule ‘Rule 1’ was created and caused this message to fail.

Also, the ‘Not Delivered’ section of the report reminds us of the definition of Mail Flow Rules above, which states that the rules take action while messages are in transit.

![IMG-20241110-WA0026](https://github.com/user-attachments/assets/8f1114fd-0a7e-47e3-835e-4325b9e1fafe)

### Reference

<a href="https://learn.microsoft.com/en-us/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules"> Mail flow rules (transport rules) in Exchange Online | Microsoft Learn </a>



