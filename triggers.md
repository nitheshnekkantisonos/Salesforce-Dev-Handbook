# Triggers

* Standard Trigger Syntax

```java
trigger TriggerName on ObjectName (trigger_events) { code_block
}
```
* The following are the trigger events
	* before insert 
	* before update 
	* before delete 
	* after insert
	* after update
	* after delete
	* after undelete

* Use **addError(errorMessage)** on the Trigger object lists to add an error

* Trigger.OperationType returns enum, Possible values of the System.TriggerOperation enum are: BEFORE_INSERT, BEFORE_UPDATE, BEFORE_DELETE,AFTER_INSERT, AFTER_UPDATE, AFTER_DELETE, and AFTER_UNDELETE

  * Example
```
trigger AccountTrigger1 on Account ( before Insert ,Before Update , After Insert, After Update) {
       switch on Trigger.OperationType  {
            when BEFORE_INSERT
            {
                System.debug('BEFORE_INSERT------>' + Trigger.OperationType );
                System.debug(Trigger.OperationType +'-Before Insert-->'+Trigger.isInsert+'--->'+Trigger.isBefore);
            }
            when AFTER_INSERT
            {
                System.debug('AFTER_INSERT ------->' +Trigger.OperationType );
                System.debug(Trigger.OperationType +'-After Insert-->'+Trigger.isInsert+'--->'+Trigger.isAfter);
            }
            when BEFORE_UPDATE, AFTER_UPDATE
            {
                System.debug('BEFORE_UPDATE or AFTER_UPDATE----->' +Trigger.OperationType );
            }
        }
}
```
