# Bounties


# hCaptcha Bug Bounty Program

The hCaptcha Bug Bounty Program provides bounties for identifying vulnerability bugs. Our development and security teams make every effort to eliminate all bugs in our systems, but there is always the chance that we might have missed a potential vulnerability. We appreciate you working with us on any bug you discover, and we offer rewards to show our appreciation.

Before getting started, please see our Service Level Agreements & Eligibility sections for more details.

**Do not submit any vulnerability to** GitHub Issues or any public forum. For all bounty program issues please email support@hcaptcha.com and CC security@hcaptcha.com.

### Service Level Agreements
We appreciate you taking the time to participate in the hCaptcha Bug Bounty Program. We have invested time and energy into our program to make it the best it can be. Here is what you can expect from us when participating in our program:

#### hCaptcha will make our best effort to:
* Provide an initial response on all reports within two business days.
* Let you know if your report qualifies for a bounty within five business days.
* If the report qualifies for a bounty, we will set a risk level of severity and the reward size within five business days.
* Resolve qualifying vulnerabilities within 90 days (1 day for critical, 1-2 weeks for high, 4-8 weeks for medium and 90 days for low issues). More complex issues may require longer to fix. If you have a question regarding the remediation timeline, please inquire on the relevant report.
* Notify you within five business days once an issue has been resolved.
* The value of rewards paid out will vary depending on Severity. The severity is calculated according to the [OWASP risk rating model based on Impact and Likelihood](https://owasp.org/www-community/OWASP_Risk_Rating_Methodology): 
* Please allow up to one week from the time the report was approved and validated to receive your bounty payment. 

Reward sizes are guided by the rules below and payable in USD via PayPal. If you prefer, you may also elect to have your reward donated to a registered charity of your choice that accepts online donations, subject to approval of the charity.

    - Medium, Large or Critical: $100 - $1000
    - Small: up to $100
    
### Eligibility
The following requirements must be adhered to in order to participate in hCaptcha's Bug Bounty Program, and for any report to qualify. Not following these requirements can result in your report being rejected or being banned from the program.

* Report format - for any report to be considered, you must provide clear instructions on how to reproduce the issue, as well as how it could be exploited (attack scenario), and what you think the security impact is. This information helps us assess eligibility and appropriate bounty amounts.
* First come, first served - only the first person to identify a particular vulnerability will qualify for a bounty. Any additional reports will be considered as duplicates and will not qualify.
* Play it safe - all testing must be performed on test accounts under your control. Any attacks against other users without provable express consent are not allowed and may result in a ban from our program. If a particular issue is severe enough that a PoC in itself may expose other users’ data, please ask us for help first so we can work together on how to safely demonstrate the bug. 
* Don't disclose too early - to protect our users, please keep all identified vulnerability details between you and us until we've had a chance to fix the issue. This includes things like posting an obscured video of an issue on Twitter prior to confirmation of a deployed fix; you may think you have concealed critical details, but doing so at minimum alerts the blackhat community to an issue and at worst unintentionally creates early disclosure. Public disclosure prior to us notifying you of the fix may result in a ban from the program. If you have questions regarding the remediation timeline, please inquire on the relevant report.
* No social engineering - bugs that require social engineering to exploit (e.g. tricking someone into clicking a link) may qualify, but please do not actually attempt to socially engineer another user, hCaptcha team members, etc., during your testing. Providing a clear explanation of how social engineering could be used in conjunction with an identified vulnerability is sufficient.
* Best practices are not eligible for bounties - for example, "make your SPF setting stricter" or "enable MTA-STS"; you are welcome to make suggestions, but this does not qualify for a bounty.

### Scope
Any design or implementation issue that substantially affects the confidentiality or integrity of user data or correctness of system operation is likely to be within the scope of the program.

* The website and other public endpoints under hcaptcha.com: [main page](https://www.hcaptcha.com)
* The dashboard: [dashboard](https://dashboard.hcaptcha.com/login)
* Any public code at: [Open Source Code](https://github.com/hCaptcha)

### Out of Scope
* Phishing hCaptcha employees, users, clients, or anyone who has a business relationship with hCaptcha.
* [Known issues](https://github.com/hcaptcha/bounties/issues)

### Common False Positive Reports

#### TLS version / cipher suite
Scanners (e.g. Burp Suite) may report that some hcaptcha.com endpoints support weak TLS ciphers, or old TLS versions. 

This is intentional:

- **unauthenticated** public endpoints do indeed support TLS 1.0, since the hCaptcha service supports browsers as old as IE8. Old browsers do not support newer TLS versions, so this is mandatory for compatibility.
- **authenticated** endpoints like the dashboard service and accounts APIs require TLS 1.2+.

Example:

```
$ curl --tlsv1.1 --tls-max 1.1 https://dashboard.hcaptcha.com
curl: error:SSL routines:ST_CONNECT:tlsv1 alert protocol version
```
