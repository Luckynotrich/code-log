![[Pasted image 20231112133211.png]]Init client above all components that require access to useQuery

![[Pasted image 20231112133308.png]]
Place Provider above all components that will require access 

![[Pasted image 20231112133911.png]]
The '?' forces data to be not null before the screen data is refreshed
![[Pasted image 20231112134654.png]]
'isLoading' is a boolean that is true while data is loading

![[Pasted image 20231112134902.png]]
The 'if' will cause 'Loading...' to display instead of the cat fact

![[Pasted image 20231112135757.png]]![[Pasted image 20231112135717.png]]
refetch allows you to force refresh of the data

![[Pasted image 20231112140105.png]]
renaming data allows for multiple instances of useQuery

![[Pasted image 20231112140500.png]]
prevent refetch when switch back to window tab