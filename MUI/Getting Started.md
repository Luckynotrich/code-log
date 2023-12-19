
[Installation](https://mui.com/material-ui/getting-started/installation/)
```
npm install @mui/material @emotion/react @emotion/styled
```

## Roboto font[](https://mui.com/material-ui/getting-started/installation/#roboto-font)

Material UI uses the [Roboto](https://fonts.google.com/specimen/Roboto) font by default. Add it to your project via Fontsource, or with the Google Fonts CDN.
```
npm install @fontsource/roboto
```

Most of the code can be copied directly from  [Mui website](https://mui.com/material-ui/getting-started/) on the components tab. Some components like the BasicDateRangeCalendar are only available through Mui-x which is the subscription library.

Mui supports a large variety of [components](https://mui.com/components/)

Mui has  default theme that in in effect automatically. 
[The Default Theme Viewer](https://mui.com/material-ui/customization/default-theme/)
![[Pasted image 20231218155516.png]]
The above code can create a custom theme
![[Pasted image 20231218155711.png]]
Values including colors and icons can be imported from Mui. The above is not a single color, but an object and sets all the secondary colors in the theme.

### Choosing a font other than the default 'Roboto'
![[Pasted image 20231218160334.png]]
Select the fonts you wish to use in all the weight used by Mui and select the import option and paste them into css.
![[Pasted image 20231218161035.png]]
Then paste the name of the fontFamily into your theme, along with  weights for the various values.
