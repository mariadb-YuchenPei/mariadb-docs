# Error 3001: Query partially completed on the master (error on master) and was aborted

Error 3001: Query partially completed on the master (error on master: %d) and was aborted. There is a chance that your master is inconsistent at this point. If you are sure that your master is ok, run this query manually on the slave and then restart the slave with SET GLOBAL SQL\_SLAVE\_SKIP\_COUNTER=1; START SLAVE;. Query:'%s'"

| Error Code | SQLSTATE | Error                 | Description                                                                                                                                                                                                                                                                                                                     |
| ---------- | -------- | --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 3001       |          | ER\_ERROR\_ON\_MASTER | Query partially completed on the master (error on master: %d) and was aborted. There is a chance that your master is inconsistent at this point. If you are sure that your master is ok, run this query manually on the slave and then restart the slave with SET GLOBAL SQL\_SLAVE\_SKIP\_COUNTER=1; START SLAVE;. Query:'%s'" |

## Possible Causes and Solutions

{% hint style="success" %}
This article doesn't currently contain any content. [You can help!](../../../../about/readme/contributing-documentation.md)
{% endhint %}

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
