
### Install dependencies

Time to install the `@tiptap/react` package, `@tiptap/pm` (the ProseMirror library) and `@tiptap/starter-kit`, which includes the most popular extensions to get started quickly.

```
npm install @tiptap/react @tiptap/pm @tiptap/starter-kit
```

## Integrate Tiptap

To actually start using Tiptap we need to create a new component. Let’s call it `Tiptap` and put the following example code in `src/Tiptap.tsx`.

```jsx
// src/Tiptap.tsx
import { EditorProvider, FloatingMenu, BubbleMenu } from '@tiptap/react'
import StarterKit from '@tiptap/starter-kit'

// define your extension array
const extensions = [StarterKit]

const content = '<p>Hello World!</p>'

const Tiptap = () => {
  return (
    <EditorProvider extensions={extensions} content={content}>
      <FloatingMenu editor={null}>This is the floating menu</FloatingMenu>
      <BubbleMenu editor={null}>This is the bubble menu</BubbleMenu>
    </EditorProvider>
  )
}

export default Tiptap
```

**Important Note**: You can always use the `useEditor` hook if you want to avoid using the Editor context.

```jsx
// src/Tiptap.tsx
import { useEditor, EditorContent, FloatingMenu, BubbleMenu } from '@tiptap/react'
import StarterKit from '@tiptap/starter-kit'

// define your extension array
const extensions = [StarterKit]

const content = '<p>Hello World!</p>'

const Tiptap = () => {
  const editor = useEditor({
    extensions,
    content,
  })

  return (
    <>
      <EditorContent editor={editor} />
      <FloatingMenu editor={editor}>This is the floating menu</FloatingMenu>
      <BubbleMenu editor={editor}>This is the bubble menu</BubbleMenu>
    </>
  )
}

export default Tiptap
```


### Add it to your app

Finally, replace the content of `src/App.tsx` with our new `Tiptap` component.

```jsx
import Tiptap from './Tiptap'

const App = () => {
  return (
    <div className="card">
      <Tiptap />
    </div>
  )
}

export default App
```


### Add it to your app

Finally, replace the content of `src/App.tsx` with our new `Tiptap` component.

```jsx
import Tiptap from './Tiptap'

const App = () => {
  return (
    <div className="card">
      <Tiptap />
    </div>
  )
}

export default App
```

### Consume the Editor context in child components

If you use the `EditorProvider` to setup your Tiptap editor, you can now easily access your editor instance from any child component using the `useCurrentEditor` hook.

```tsx
import { useCurrentEditor } from '@tiptap/react'

const EditorJSONPreview = () => {
  const { editor } = useCurrentEditor()

  return <pre>{JSON.stringify(editor.getJSON(), null, 2)}</pre>
}
```

### Consume the Editor context in child components

If you use the `EditorProvider` to setup your Tiptap editor, you can now easily access your editor instance from any child component using the `useCurrentEditor` hook.

```tsx
import { useCurrentEditor } from '@tiptap/react'

const EditorJSONPreview = () => {
  const { editor } = useCurrentEditor()

  return <pre>{JSON.stringify(editor.getJSON(), null, 2)}</pre>
}
```
### Add before or after slots

Since the `EditorContent` component is rendered by the `EditorProvider` component, we now can't directly define where to render before or after content of our editor. For that we can use the `slotBefore` & `slotAfter` props on the `EditorProvider` component.

```tsx
<EditorProvider
  extensions={extensions}
  content={content}
  slotBefore={<MyEditorToolbar />}
  slotAfter={<MyEditorFooter />}
/>
```

### [Container props](https://tiptap.dev/docs/editor/getting-started/install/react#container-props)

The `EditorProvider` component accepts a `editorContainerProps` prop that allows you to pass props to the container element of the editor provider.

```tsx
<EditorProvider
  extensions={extensions}
  content={content}
  editorContainerProps={{ className: 'editor-container' }}
/>
```

## [Optimize your performance](https://tiptap.dev/docs/editor/getting-started/install/react#optimize-your-performance)


We strongly recommend visiting the [React Performance Guide](https://tiptap.dev/docs/guides/performance) to integrate the Tiptap Editor efficiently. This will help you avoid potential issues as your app scales.
### [Getting started with React and TipTap](https://tiptap.dev/docs/editor/getting-started/install/react#add-it-to-your-app)
