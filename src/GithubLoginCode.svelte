<GithubLogin
  clientId="xyz2345678"
  scope="user:email"
  redirectUri="http://localhost:3003/auth/github/callback"
  on:success={
    params => {
        console.log(params.detail);
         authorized = true;
    }
  }
  on:error={error => 
    console.log(error)}
  let:onLogin = ""
>
  <button on:click={onLogin}>Github Login</button>
</GithubLogin>