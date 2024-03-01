# [How to Create Your Own Custom Material UI Theme: A Step-by-Step Guide | V5](https://www.youtube.com/watch?v=s-qYhDPpCl4)
[GrepSoft](https://www.youtube.com/@Grepsoft)

`/home/lucky/webdev/dynamic-mui-theme-grepsoft/`
###### Notes: `<ThemeProvider>` applies theme to all Mui elements inside  components... `deepmerge` blends settings from different themes so spacing and size remain consistent as you change themes.
![[Pasted image 20240220123205.png]]
![[Pasted image 20240220123507.png]]
###### Note: `theme1` was written as a string constant  for demonstration of how the theme could be set programatically. String must be wrapped in back ticks and `JSON.parse` used to be applied  (see `App.jsx`)
![[Pasted image 20240220123422.png]]
###### Note: `deepmerge`  allow the spacing from the base theme to be spread accross all three themes.
![[Pasted image 20240220123604.png]]
