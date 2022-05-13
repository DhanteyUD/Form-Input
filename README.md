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

3. Functional Sign-up Form :

```js
import React, { ChangeEvent, useState, useEffect } from "react";
import { FaEye } from "react-icons/fa";
import axios from "axios";


const Signup = () => {
const [errorMessage, setErrorMessage] = useState('');
  const [successMessage, setSuccessMessage] = useState('');
  const [profile, setProfile] = useState({
    email: "",
    fullname: "",
    mobile: "",
    password: ""
  })
 
  const handleProfile =(e:ChangeEvent<HTMLInputElement>) => {
  const {value,name} = e.target
  setProfile((prevState) =>({...prevState, [name] : value})
  )
  }

  const onSubmit = async (e: React.SyntheticEvent) => {
    e.preventDefault();
    try {
      let response: any = await axios.post(
        "http://localhost:3000/register",
        {
          email: profile.email,
          fullname: profile.fullname,
          mobile: profile.mobile,
          password: profile.password,
        }
      ); 
      
setSuccessMessage(response.data.message);
setErrorMessage('')

    } catch (e: React.SyntheticEvent) {
      let error = e.response.data;

     
 setErrorMessage(e.response.data);
 setSuccessMessage('')
	
 console.log(error);

    }
  };
  
  const [state, setState] = useState(true);

  const toggleBtn = () => {
    setState((prevState) => !prevState);
  };
  console.log(errorMessage)

  return (
    <>
      <div>
        <h2>Signup</h2>
      </div>
        <div className="form">
          <form onSubmit={onSubmit}>
              <div>
                <label>Enter your full name</label>
              </div>
              <input
                type="text"
                name="fullname"
                value={profile.fullname}
                placeholder="Full name"
                onChange={handleProfile}
              />
            </div>
	    
            <div>
              <div>
                <label>Email address</label>
              </div>
              <input
                type="email"
                name="email"
                value={profile.email}
                placeholder="Email address"
                onChange={handleProfile}
              />
            </div>

            <div>
              <div>
                <label>Password</label>
              </div>
              <div id="password-toggle">
                <input
                  type={state ? "password" : "text"}
                  name="password"
                  value={profile.password}
                  placeholder="Password"
                  onChange={handleProfile}
                />
                <button onClick={toggleBtn}>
                  <FaEye></FaEye>
                </button>
              </div>
            </div>

            <div>
              <div>
                <label>Enter your phone number</label>
              </div>
              <input
                type="text"
                name="mobile"
                value={profile.mobile}
                placeholder="Phone"
                onChange={handleProfile}
              />
            </div>

            <div>
              <button type="submit"> Signup </button>
            </div>
            <div>
              {errorMessage.length > 0 ? (
                <div> {errorMessage} </div>
              ) : null}
              {successMessage.length > 0 ? (
                <div> {successMessage} </div>
              ): null}
          </form>
        </div>
    </>
  );
};

export default Signup;
```
