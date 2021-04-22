# conform-password




 const infoaddress=(e)=>{
    if(e.target.name==='name'){
        const namevalid=/^([a-zA-Z ]){2,30}$/.test(e.target.value)
       userInfo=namevalid;
    }

    if(e.target.name==='email'){
        const emailvalid=/^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$/.test(e.target.value)
        userInfo=emailvalid;
    }
    if(e.target.name==='password' ){
        const passvalid=/^(?=.*\d)/.test(e.target.value)
        userInfo=passvalid
        if(passvalid){
          setConform(e.target.value)
        }
    }

    if(e.target.name==='repassword'){
        const repassvalid=/^(?=.*\d)/.test(e.target.value)
        userInfo=repassvalid
        if(repassvalid){
         setReconform(e.target.value)
        }  
    }

     
  
    if(userInfo){
        const infoUser={...user}
        infoUser[e.target.name]=e.target.value;
        setUser(infoUser)
        
    }

    }
    const setAddress=(e)=>{
        console.log(user.email,user.password)
         if(user.email && conform===reconform){
            firebase.auth().createUserWithEmailAndPassword(user.email, user.password)
            .then((userCredential) => {
              // Signed in 
              var users = userCredential.user;
              console.log(users)
              const info={...user}
              info.error=' '
           
              setUser(info)
              updateProfile(user.name)
              setLoginUser(info)
            
            })
