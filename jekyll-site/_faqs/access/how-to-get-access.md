---
title: "How do I get access to MIMIC?"
layout: default
parent: "FAQs"
nav_order: 1
permalink: /faqs/access/how-to-get-access/
---

# How do I get access to MIMIC?

Getting access to MIMIC data requires completing human subjects training and signing a data use agreement. Here's the step-by-step process:

## Step 1: Complete PhysioNet Credentialing

1. **Create a PhysioNet account** at [physionet.org](https://physionet.org)
2. **Complete the credentialing process**:
   - Take the required training course in human subjects research
   - Provide your institutional affiliation
   - Submit reference information (required for students/postdocs)
3. **Wait for approval** (typically 1-5 business days)

{: .important }
> **Students and Postdocs**: You must provide your supervisor's contact information as a reference. Do not list yourself as a reference.

## Step 2: Sign the Data Use Agreement

Once credentialed:

1. **Log in** to your PhysioNet account
2. **Navigate** to the dataset page you need:
   - [MIMIC-IV](https://physionet.org/content/mimiciv/)
   - [MIMIC-III](https://physionet.org/content/mimiciii/)
   - [MIMIC-CXR](https://physionet.org/content/mimic-cxr/)
3. **Review and sign** the Data Use Agreement (DUA)
4. **Download** or access data through cloud platforms

## Step 3: Choose Your Access Method

### Cloud Access (Recommended)
- **Google Cloud (BigQuery)**: Easiest for SQL queries
- **AWS**: Good for large-scale processing
- **Physionet**: Direct cloud access

### Local Download
- Download individual CSV files
- Set up local PostgreSQL database
- Requires more setup but full control

## Common Questions

### How long does credentialing take?
Typically 1-5 business days if all information is complete. Incomplete applications may be delayed or rejected.

### What training is required?
You must complete human subjects research training. Most institutions offer this through CITI Program or similar platforms.

### Can I access data immediately after signing the DUA?
Yes, for cloud platforms. Local download may take additional time depending on file sizes.

### Do I need separate access for each dataset?
Yes, you need to sign separate DUAs for MIMIC-III, MIMIC-IV, MIMIC-CXR, etc.

## Troubleshooting

### Application Rejected
- Ensure all required fields are completed
- Provide valid institutional email address
- Include proper reference information
- Contact PhysioNet support if issues persist

### Can't Find Reference Information
- Use your supervisor or department head
- Must be someone who can verify your affiliation
- Should not be yourself or a peer student

### Institutional Issues
- Some institutions may require additional approvals
- Check with your IRB or research office
- International users may need additional documentation

## Next Steps

Once you have access:

1. **Start with tutorials** - Try our [first query tutorial](/tutorials/first-query/)
2. **Understand the data** - Read the [schema overview](/concepts/schema-overview/)
3. **Join the community** - Follow [community guidelines](/docs/community/)

## Still Having Issues?

- **PhysioNet Support**: Contact through the PhysioNet website
- **Technical Questions**: Check our [technical FAQs](/faqs/technical/)
- **Data Questions**: See our [analysis FAQs](/faqs/analysis/)

---

{: .highlight }
> Remember: The Data Use Agreement is legally binding. Make sure you understand and can comply with all terms before signing.
