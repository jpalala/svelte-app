<script>
  import logo from './assets/svelte.png'
  let authorized = false;
  console.log(import.meta.env.VITE_SOME_KEY);
  import axios from 'axios';
  const baseUrl = 'http://localhost:3003';
  const cookie = document.cookie;
  axios.defaults.withCredentials = true

  //generates the sanctum token
//   axios.get(baseUrl + '/sanctum/csrf-cookie',).then(() => {
     //make a request to get /github_id


  if(cookie.includes("XSRF-TOKEN")) {
    axios.post(baseUrl + '/api/github_id', {
          email: "joe@mentorsdojo.com",
        }).then((res) => {
            console.log(res);
            authorized = true;
        });
  } else {
    console.error('No XSRF Token!');
  }
</script>

<main>
  <img src={logo} alt="Svelte Logo" />
  <h1>Lets Login!</h1>

  <p>
  Authorized: {authorized}
  </p>

</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 16rem;
    width: 16rem;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  }
</style>
