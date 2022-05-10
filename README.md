# React-typescript Form Input Challenge

1. Using event on form

`
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
`
