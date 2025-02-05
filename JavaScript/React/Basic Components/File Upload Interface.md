
```javascript
import './App.css';
import React, {useState} from 'react';
import axios from 'axios';
var FormData = require('form-data');

function App() {

  const [file, setFile] = useState()

  function handleChange(event) {
    setFile(event.target.files[0])
  }
  
  function handleSubmit(event) {
    event.preventDefault()
    const url = 'http://localhost:3000/uploadFile';
    const formData = new FormData();
    formData.append('file', file);
    formData.append('fileName', file.name);
    const config = {
      headers: {
        'content-type': 'multipart/form-data',
      },
    };
    axios.post(url, formData, config).then((response) => {
      console.log(response.data);
    });

  }

  return (
    <div className="App">
        <form onSubmit={handleSubmit}>
          <h1>React File Upload</h1>
          <input type="file" onChange={handleChange}/>
          <button type="submit">Upload</button>
        </form>
    </div>
  );
}

export default App;
```
![[Pasted image 20240916132729.png]]![[Pasted image 20240916133126.png]]
![[Pasted image 20240916131516.png]]
![[Pasted image 20240916133825.png]]
![[Pasted image 20240916135930.png]]
![[Pasted image 20240916135604.png]]
