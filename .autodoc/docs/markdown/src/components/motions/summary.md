[View code on GitHub](/.autodoc/docs/json/src/components/motions)

The `motions` folder contains a collection of React components that utilize the Framer Motion library to create various animation effects. These components can be used throughout a larger project to add visual interest and improve user experience.

1. **FadeIn.tsx**: This component animates the opacity and position of its child elements, creating a fade-in effect with a slight upward movement. It accepts optional `className` and `delay` props. The `className` prop can be used for styling, while the `delay` prop specifies the time to wait before starting the animation. Example usage:

   ```jsx
   import FadeIn from "./FadeIn";

   const MyComponent = () => (
     <div>
       <FadeIn delay={0.5}>
         <h1>Welcome to my website!</h1>
       </FadeIn>
       <FadeIn delay={1}>
         <p>Here you can find all sorts of interesting things.</p>
       </FadeIn>
     </div>
   );
   ```

2. **FadeOut.tsx**: This component animates the fading out of its child elements, with a slight leftward movement. It accepts optional `className` and `delay` props. The `className` prop can be used for styling, while the `delay` prop specifies the time to wait before starting the animation. Example usage:

   ```jsx
   import FadeOut from "./FadeOut";

   const ListItem = ({ item, onDelete }) => {
     const handleDelete = () => {
       onDelete(item.id);
     };

     return (
       <div>
         <p>{item.text}</p>
         <button onClick={handleDelete}>Delete</button>
       </div>
     );
   };

   const List = ({ items, onDelete }) => (
     <div>
       {items.map((item) => (
         <FadeOut key={item.id}>
           <ListItem item={item} onDelete={onDelete} />
         </FadeOut>
       ))}
     </div>
   );
   ```

3. **expand.tsx**: This component animates the scaling of its child elements, creating an expand effect. It accepts optional `className`, `delay`, and `type` props. The `className` prop can be used for styling, the `delay` prop specifies the time to wait before starting the animation, and the `type` prop specifies the animation type ("spring" or "tween"). Example usage:

   ```jsx
   import Expand from "./Expand";

   const MyComponent = () => (
     <div>
       <h1>Click to Expand</h1>
       <Expand type="tween" delay={0.5}>
         <p>This text will expand when clicked.</p>
       </Expand>
     </div>
   );
   ```

4. **popin.tsx**: This component animates the scaling of its child elements, creating a pop-in effect. It accepts optional `className` and `delay` props. The `className` prop can be used for styling, while the `delay` prop specifies the time to wait before starting the animation. Example usage:

   ```jsx
   import PopIn from "./PopIn";

   function MyButton() {
     return (
       <PopIn delay={0.5}>
         <button className="my-button">Click me!</button>
       </PopIn>
     );
   }
   ```

These components can be combined and customized to create a variety of animations for different elements in a React application. They provide a simple and reusable way to enhance the user interface and improve user experience.
