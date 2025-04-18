[main.tsx](https://github.com/cosdensolutions/code/blob/master/videos/long/react-router-tutorial/src/main.tsx)
```js
import React from 'react';
import ReactDOM from 'react-dom/client';
import { createBrowserRouter, RouterProvider } from 'react-router-dom';

import HomePage from './pages/HomePage';
import NotFoundPage from './pages/NotFoundPage';
import ProfilePage from './pages/ProfilePage';
import ProfilesPage from './pages/ProfilesPage';

import './index.css';

const router = createBrowserRouter([
  {
    path: '/',
    element: <HomePage />,
    errorElement: <NotFoundPage />,
  },
  {
    path: '/profiles',
    element: <ProfilesPage />,
    {/* Allows ProfilePage to become a child(component) of ProfilesPage and display concurrently. */}
    children: [
      {
        path: '/profiles/:profileId',
        element: <ProfilePage />,
      },
    ],
  },
]);

ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    <RouterProvider router={router} />
  </React.StrictMode>,
);

```

`HomePage.tsx`
```tsx
export default function HomePage() {
  return (
    <div>
      <h1>Home Page</h1>
    </div>
  );
}
```

`NotFoundPage.tsx`
```tsx
import { Link } from 'react-router-dom';

export default function NotFoundPage() {
  return (
    <div className="flex flex-col gap-2">
      404 Not Found
      <Link to="/">Home from Link</Link>
    </div>
  );
}
```

`ProfilePage.tsx`
```jsx
import { useParams } from 'react-router-dom';

export default function ProfilePage() {
{/* useParams makes all parameters available */}
  const params = useParams<{ profileId: string }>();
  return (
    <div>
      <h1>Profile Page {params.profileId}</h1>
    </div>
  );
}
```

`ProfilesPage.tsx`
```tsx
import { NavLink, Outlet } from 'react-router-dom';

export default function ProfilesPage() {
  const profiles = [1, 2, 'three', 4, 5];

  return (
    <div className="flex gap-2">
      <div className="flex flex-col gap-2">
        {profiles.map((profile) => (
          <NavLink
            key={profile}
            to={`/profiles/${profile}`}
            className={({ isActive }) => {
              return isActive ? 'text-primary-700' : '';
            }}
          >
            Profile {profile}
          </NavLink>
        ))}
      </div>
      <Outlet />
    </div>
  );
}
```

`package.json`
```json
{
  "name": "vite-ts",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "lint": "eslint . --ext ts,tsx --report-unused-disable-directives --max-warnings 0",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.21.2"
  },
  "devDependencies": {
    "@types/react": "^18.2.43",
    "@types/react-dom": "^18.2.17",
    "@typescript-eslint/eslint-plugin": "^6.14.0",
    "@typescript-eslint/parser": "^6.14.0",
    "@vitejs/plugin-react": "^4.2.1",
    "autoprefixer": "^10.4.16",
    "eslint": "^8.55.0",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-react-refresh": "^0.4.5",
    "eslint-plugin-simple-import-sort": "^10.0.0",
    "postcss": "^8.4.33",
    "prettier": "^3.2.2",
    "prettier-plugin-tailwindcss": "^0.5.11",
    "tailwindcss": "^3.4.1",
    "typescript": "^5.2.2",
    "vite": "^5.0.8"
  }
}
```