
# [Upload a file to S3 with REACT-QUERY](https://www.youtube.com/watch?v=uFyfnWSbUpY)

```js
import axios, { AxiosError } from 'axios'
import { useState } from 'react'
import { useMutation } from 'react-query'

interface IArgs {
    presignedUploadUrl: string
    file: File
}

export const useFileUploadMutation = () => {
    const [ progress, setProgress ] = useState(0)

    const mutation = useMutation<void, AxiosError, IArgs>(
        args => axios.put(
            args.presignedUploadUrl,
            args.file,
            { onUploadProgress: ev => setProgress(Math.round((ev.loaded * 100) / ev.total)) }
        )
    )

    return { ...mutation, progress }
}

```