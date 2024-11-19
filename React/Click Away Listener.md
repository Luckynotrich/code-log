```js
import  { useRef, useEffect } from 'react';
import PropTypes from 'prop-types';

export const ClickAwayListener = ({ children, onClickAway }) => {
  const wrapperRef = useRef(null);

  useEffect(() => {
    function handleClickOutside(event) {
      if (wrapperRef.current && !wrapperRef.current.contains(event.target)) {
        onClickAway();
      }
    }

    document.addEventListener('mousedown', handleClickOutside);
    return () => {
      document.removeEventListener('mousedown', handleClickOutside);
    };
  }, [onClickAway]);

  return <div ref={wrapperRef}>{children}</div>;
};
ClickAwayListener.propTypes = {
    children:PropTypes.func,
    onClickAway:PropTypes.func
}
// const MyComponent = () => {
//   const [isOpen, setIsOpen] = React.useState(false);

//   const handleClick = () => setIsOpen(true);
//   const handleClickAway = () => setIsOpen(false);

//   return (
//     <div>
//       <button onClick={handleClick}>Open Dropdown</button>
//       {isOpen && (
//         <ClickAwayListener onClickAway={handleClickAway}>
//           <div className="dropdown">
//             <p>Dropdown content</p>
//           </div>
//         </ClickAwayListener>
//       )}
//     </div>
//   );
// };

// export default MyComponent;
```