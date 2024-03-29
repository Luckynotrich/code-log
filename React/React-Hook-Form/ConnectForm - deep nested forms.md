When we are building forms, there are times when our input lives inside of deeply nested component trees, and that's when [FormContext](https://react-hook-form.com/docs/useformcontext) comes in handy. However, we can further improve the Developer Experience by creating a `ConnectForm` component and leveraging React's [renderProps](https://reactjs.org/docs/render-props.html). The benefit is you can connect your input with React Hook Form much easier.
``` javascript
import { FormProvider, useForm, useFormContext } from "react-hook-form"

export const ConnectForm = ({ children }) => {
  const methods = useFormContext()


  return children({ ...methods })
}

export const DeepNest = () => (
  <ConnectForm>
    {({ register }) => <input {...register("deepNestedInput")} />}
  </ConnectForm>
)

export const App = () => {
  const methods = useForm()

  return (
    <FormProvider {...methods}>
      <form>
        <DeepNest />
      </form>
    </FormProvider>
  )
}
```