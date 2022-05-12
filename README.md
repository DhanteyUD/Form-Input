# React-typescript Form Input

1. Use event on form :

```js
import React, {ChangeEvent, useState} from 'react'

const Signin = () => {
  
  const [formData, setFormData]= useState({
    email: "",
    password: ""
  })

  const handleSubmit=(e: React.SyntheticEvent)=>{
    e.preventDefault()
    console.log(formData)
  };

return (
  <div className="container">
   <form onSubmit={handleSubmit}>
    <label> Sign In </label>
    <div data-validate="Please enter a username">
     <label htmlFor="email"> Email Address </label>
     <input className="input" 
                 type="text" 
	         name="email" 
		value={formData.email}
	     onChange={(e: ChangeEvent<HTMLInputElement>) => setFormData({
                        ...formData, email: e.target.value})
                       }
	  placeholder="Email Address" 
      />
    </div>
	
    <div data-validate="Please enter password">
     <label htmlFor="password"> Password </label>
     <input className="input" 
		 type="password" 
		 name="password"
	        value={formData.password}
	     onChange={(e: ChangeEvent<HTMLInputElement>)=> setFormData({
                       ...formData, password: e.target.value})
                       } 
	  placeholder="Password" 
      />
    </div>
            
    <input type="submit" value="Sign In" />
        
  </form>
</div>
);
}

export default Signin;
```
2. Use event with handler function :

```js
import React, {ChangeEvent, useState} from 'react'

function Signin () {
  
  const [email, setEmail] = useState("")
  const [password, setPassword] = useState("")
  
  const emailChangeHandler=(e: ChangeEvent<HTMLInputElement>) => {
    setEmail(e.target.value)
  };
  
 const passswordChangeHandler=(e: ChangeEvent<HTMLInputElement>) => {
    setPassword(e.target.value)
  };

  const onSubmitHandler=(e: React.SyntheticEvent) => {
    e.preventDefault()
    console.log("Email: ", email, " password", password)
  };

return (
  <div className="container">
   <form onSubmit={onSubmitHandler}>
    <label> Sign In </label>
    <div data-validate="Please enter a username">
     <label htmlFor="email"> Email Address </label>
     <input className="input" 
                 type="text" 
	         name="email" 
		value={email}
	     onChange={emailChangeHandler}
	  placeholder="Email Address" 
      />
    </div>
	
    <div data-validate="Please enter password">
     <label htmlFor="password"> Password </label>
     <input className="input" 
		 type="password" 
		 name="password"
	        value={password}
	     onChange={passwordChangeHandler} 
	  placeholder="Password" 
      />
    </div>
            
    <button>Sign In</button>
        
  </form>
</div>
);
}

export default Signin;
```

3. Using prev state :

```js

```
