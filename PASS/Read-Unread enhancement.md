### Describe the Current Behavior/Feature:

With the message system in place, we don't have a system set for if a message was read or unread. By including a status for `read` in the message object we could keep track on read/unread messages using that. This feature would really just be needed for the inbox and nothing else.

___

### Proposed Behavior/Feature:

By including a `read` status property for the message object, we could the value toggled from `false` to `true` after viewing the message for the first time by clicking on for a preview of the message.

___

### Rationale:

As stated in the description for this feature, by including a `read` status as part of the message object, PASS could keep track of read/unread messages of the user.

___

### Proposed Implementation (if applicable):

We could include this `read` status as part of the message object. This status could be toggled from `false` to `true` after viewing the message for the first time by clicking on for a preview of the message.

To make this backwards compatible with older message that doesn't have the read status, we could simply have them behave as if they're unread and add the unread status to the old message.


### Message tracking:
(unordered)

pages/Messages.jsx
line #12
![[Pasted image 20230907133823.png]]
line #34
![[Pasted image 20230907133249.png]]
line #38
![[Pasted image 20230907133143.png]]
line #52
![[Pasted image 20230907133432.png]]
line #98
![[Pasted image 20230907133612.png]]

