Workflow report - Playbook
=========

workflow_report is a playbooks that from workflow generates a single global report by hosts.

You need to provide only the WorkflowID by survey.

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