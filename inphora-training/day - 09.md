# Day 9

## Objective

The objective of this session was to understand how attackers may disguise malicious links during phishing campaigns and to learn how Python-based cybersecurity tools are installed and managed using isolated environments.

---

## Topics Covered

### URL Masking

URL masking is a technique used to make a link appear more trustworthy than its actual destination.

Cybercriminals often use this method to:

* Increase click rates
* Hide malicious destinations
* Trick users into visiting fake websites
* Support phishing campaigns

Understanding how these techniques work helps security professionals identify and defend against them.

## Installation
``` bash
git clone https://github.com/spyboy-productions/Facad1ng.git
```
``` bash
cd Facad1ng
```
``` bash
pip3 install -r requirements.txt
```
``` bash
python3 facad1ng.py
```
---

## Python Virtual Environment (venv)

Many cybersecurity tools are written in Python and require additional libraries.

To avoid dependency conflicts, Python Virtual Environments (venv) are used.

Benefits:

* Isolated project environment
* Separate package management
* Prevents system-wide dependency issues
* Easier troubleshooting

---

## Environment Setup Process

### Create a Virtual Environment

```bash
python3 -m venv venv
```

This creates a folder named `venv` containing an isolated Python environment.

---

### Activate the Environment

```bash
source venv/bin/activate
```

After activation, packages installed using pip remain inside the virtual environment.

---

### Install Required Dependencies

```bash
pip install -r requirements.txt
```

This installs all packages listed in the project's requirements file.

---

### Verify Installation

```bash
pip list
```

Displays all installed packages inside the environment.

---

### Deactivate Environment

```bash
deactivate
```

Exits the virtual environment and returns to the system Python installation.

---

## Security Awareness Concepts

During the session, examples were discussed to understand:

* How phishing campaigns use deceptive links
* Why URL verification is important
* Common phishing indicators
* Methods for identifying suspicious URLs

---

## Indicators of Suspicious Links

Common warning signs include:

* Misspelled domain names
* Unusual URLs
* Unknown shortened links
* Unexpected redirects
* Requests for credentials

---

## Defensive Measures

To protect against phishing attacks:

* Verify URLs before clicking
* Inspect domain names carefully
* Enable Multi-Factor Authentication (MFA)
* Avoid opening suspicious links
* Use browser security protections
* Report suspicious websites

---

## Key Takeaways

* Learned the concept of URL masking and its role in phishing attacks.
* Understood why attackers attempt to disguise links.
* Learned how Python virtual environments are created and managed.
* Practiced dependency installation using `pip`.
* Studied defensive techniques for identifying phishing attempts.
* Improved cybersecurity awareness regarding malicious URLs.

---

## Conclusion

This session combined cybersecurity awareness with practical Python environment management. Understanding both secure development practices and common phishing techniques helps build a stronger foundation for cybersecurity and ethical hacking studies.
