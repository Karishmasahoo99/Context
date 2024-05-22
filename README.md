Context API provides a store from where we can access the data which helps in reducing prop-drilling. Two things need to be done one is create context and another is context provider and we need to wrap it over the parent of the component where we require the data, since the start of flow usually starts from App.jsx we wrap <App/> to <Provider>

    import React from 'react';
    const UserContext=React.createContext();
    export default UserContext;

For the provider, 
    import React, { useState } from "react";
    import UserContext from "./UserContext";
    
    const UserContextProvider=({children})=>{
       const [user, setUser]=useState(null);
       return(
        <UserContext.Provider value={{user, setUser}}>
         {children}
        </UserContext.Provider>
       )
    }
    
    export default UserContextProvider;

Here the values are passed are user and setUser. But we can send methods also here. It is our choice if we wrap <App/> in <UserContextProvider> via main.jsx or App.jsx.
