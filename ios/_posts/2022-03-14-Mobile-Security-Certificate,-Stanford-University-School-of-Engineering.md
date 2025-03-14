### #🛡️Mobile Application Security #💻SoftwareDevelopment #📱iOS 
I got my certificate of completion for [Mobile Security Course](https://online.stanford.edu/courses/xacs215-mobile-security) from Stanfrod University School of Engineering. 
In this post, I would like to share my notes about the course, my learnings and what I was expecting from this course, before I purchase. Overall, it was a good experience, and learned many important information from this course, I would like to see this course after it is updated, more recent SDKs and APIs.

## What was my motivation?
Mobile security is crucial. Should be handled properly to protect confidential and prevent exposing private data of user. Security always considered as everyone's responsibility, but at the same time we know that when everyone is responsible, no one is! 
## Why did I choose this course?
**First**, there are not much course options when the topic is Mobile Security. 
**Second**, this course is promising to provide an in-depth technical overview of the security features and limitations of modern mobile operating systems, including the top risks and vulnerabilities, every IT professional needs to know.
**Third**, and most important one, my fellow tweeps recommended me this course.

## My Knowledge Gain
This course is not iOS specific, all sort of security vulnerabilities on mobile devices, including, tablets and watches with phones, proactively mentioned with historical data/previous deficiencies.
My first learning from the course is threat definitions for Privacy and Security. **Privacy:** data and identifier leakage
**Security:** phishing, malware & drive-bys malicious intents

## What are the main fundamental differences and similarities between mobile and traditional malwares?
This is quite meaningful question to understand the perspective of hackers. My main note for this question is the volume of data stolen with the attack. Traditional attacks on web tends to expose high volume of user data, while on mobile there is an individual users information. This is an advantage of the mobile development with highly secure SDKs, which by defaults protects with user and provices ready to use APIs for developers.

## Wha is OWASP? 
The [Open Web Application Security Project® (OWASP)](https://owasp.org/) is a nonprofit foundation that works to improve the security of software. 
OWASP's Mobile Top 10 Mobile Risks list
1. Improper Platform Usage
2. Insecure Data Storage
3. Insecure Communication
4. Insecure Authentication
5. Insufficient Cryptography
6. Insecure Authorization
7. Client Code Quality
8. Code Tampering
9. Reverse Engineering
10. Extraneous Functionality

## iOS Specific Learnings
**iOS Security architecture;** boot process, hardware security features, unlock process
**iOS Cryptography;** key management and the iOS crypto framework

**Secure boot chain**, is a crucial step on iOS architecture, it is a way of authorizing the iOS code. Jailbreaking works by finding and exploiting vulnerabilitis in this chain. 4 main layer ensures that each other signed properly. 

**How data can leak?** We focused on three main ways for data leakage as pasteboard, splash image and data in transit. 

**What to look for in Webview?** WKWebview preferences, such as setJavaScriptEnabled and hasOnlySecureContent.

**What to look for in Networking Layer?** NSURLSessionConfiguration preferences, such as ephemeralSessionConfiguration and setTLSMinimumSupportedProtocol. Avoid servers not supporting TLS 1.2. App Transport Security can be overriden via info.plist, and dangerous to do that. Avoid allowing to use HTTP. Certificate pinning, it is to assure only reaching to your home cloud and meanwhile rejecting all other certs and failing connections.






