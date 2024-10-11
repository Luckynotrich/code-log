[webdev simplified](https://blog.webdevsimplified.com/2020-12/react-prop-types/)

npm i prop-types
![[Pasted image 20230823145414.png]]

#### Define yourComponent.propTypes inside your component and select variable types
![[Pasted image 20230823145844.png]]


#### look for Prop Type errors in browser console if the wrong kind of value is provided
![[Pasted image 20230823150403.png]]

#### The .isRequired throws this error if the variable in not present
![[Pasted image 20230823152322.png]]


#### renderable with PropType.node makes the component so that you can write to it
![[Pasted image 20230823152845.png]]
![[Pasted image 20230823152947.png]]
##### Only thing that can be rendered will work. Objects will not work. Other React components will work as will strings



#### This will require one and only one child component and it has to be a React component
![[Pasted image 20230823153605.png]]



#### render this component as a link
![[Pasted image 20230823153952.png]]
#### that is what elementType will be referring to
![[Pasted image 20230823154203.png]]

#### PropType.any.required could be any kind of variable but it is required
![[Pasted image 20230823154508.png]]

#### PropTypes.oneOfType takes an array.
in this instance it will accept an argument of type string on type number
![[Pasted image 20230823154854.png]]

#### PropTypes.oneOf also accepts an array that limits the acceptable inputs.
In this case a string with either "Loading" or "Ready"
![[Pasted image 20230823155343.png]]


![[Pasted image 20230823155943.png]]
![[Pasted image 20230823155802.png]]
![[Pasted image 20230823160239.png]]
##### Both of these situations will work, the next slide wont work, however.
![[Pasted image 20230823160446.png]]
#### This slide accounts for that probability
![[Pasted image 20230823160646.png]]

#### Shape allows objects to be defined
Age as a string will through an error
![[Pasted image 20230823160857.png]]


#### Exact limits the shape to the number of arguments
![[Pasted image 20230823161518.png]]
