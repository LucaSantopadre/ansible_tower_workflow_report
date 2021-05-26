Workflow report - Role
=========

workflow_report is a role that from workflow generates a single global report by hosts.

**eg. output:**


| Workflow id | host   | job_id| job_name| success  | job_id | job_name    | success | job_id | job_name | success |
|-------------|--------|-------|---------|----------|--------|-------------|---------|--------|----------|---------|
| 41010       | node01 | 41013 | prepare | True     | 41014  | calibration | True    | 41018  | scan     | True    |
| 41010       | node02 | 41013 | prepare | True     | 41014  | calibration | True    | 41018  | scan     | True    |
| 41010       | node03 | 41013 | prepare | True     | 41014  | calibration | True    | 41018  | scan     | True    |
| 41010       | node04 | 41013 | prepare | True     | 41014  | calibration | True    | 41018  | scan     | True    |
| 41010       | node05 | 41013 | prepare | True     | 41014  | calibration | True    | 41018  | scan     | True    |


## Requirements

*  `ansible.tower` collection (v. 3.8.1);
*  `Tower credentials`

Role Variables
--------------

- {Required} `workflow_id`  is the id of the workflow execution (Number);
- {Optional} `send_mail`, if TRUE it tries to send the report vie email (bool) [default = False]
- {Optional} `max_hosts`, The number of hosts we are allowd to report (int) [default = 20000]

* *Variable related to the mail*:

- {Required} `email_server` The mail server (string);

- {Required} `email_server_port` The mail server port. This must be a valid integer between 1 and 65534 (Number);

- {Required} `email_username `  SMTP username (string);

- {Required} `email_password` SMTP password (string);

- {Required} `email_receiver` the email-address(es) the mail is being sent to, comma separated  (string) Eg. `John Smith <john.smith@example.com>, mario.rossi@example.com`;

- {Required} `email_starttls` type of connection that can be: (string)

  - `always`, the connection will only send email if the connection is Encrypted. If the server doesn't accept the encrypted connection it will fail;
  - `try`, the connection will attempt to setup a secure SSL/TLS session, before trying to send;
  - `never`, the connection will not attempt to setup a secure SSL/TLS session, before sending;
  - `starttls`, the connection will try to upgrade to a secure SSL/TLS connection, before sending. If it is unable to do so it will fail.

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - role: report-HC
      vars:
        - workflow_id: 1306
        - email_username: 'username@example.com' 
        - email_password: '123password456'
        - email_receiver: 'Demo Mail <demo.mail@example.com>'
        - email_starttls: 'starttls'
        - email_server: 'smtp.gmail.com'
        - email_server_port: 587
```

Author
------------------

[Luca Santopadre](https://it.linkedin.com/in/luca-santopadre-in)