![[Pasted image 20230817135238.png]]
#### Use useEffect to be notified when form state is changed

![[Pasted image 20230817110109.png]]

#### useForm errors caught in errors array 'onSubmit'

![[Pasted image 20230817125826.png]]

#### isDirty rendered false while all fields were empty and true when 1 character was entered. Returns to false when the character is deleted

![[Pasted image 20230817130329.png]]

#### dirtyFields detects whether individual fields have values entered. 
Depends on default value to make this determination.


![[Pasted image 20230817130657.png]]

#### touchFields indicates whether fields get focus and then blurred

![[Pasted image 20230817131425.png]]
#### isSubmittedSuccessful is true if it all entered values meet rules like 'required'

![[Pasted image 20230817131816.png]]
#### submitCount indicates how many times form is submitted

![[Pasted image 20230817132800.png]]
#### isValid checks all validation for every input on the form.
It only works in mode: 'onChange' and requires react to check every keystroke. It only resolves True, in this case when both fields have input

![[Pasted image 20230817133752.png]]
#### isSubmitting detects whether an asynchronous function is still resolving. 
Returns False before submit, True during submit and False again after

![[Pasted image 20230817134400.png]]
#### isValidating returns true while validate is active. 
Not sure, validate maybe a key word for creating validation
