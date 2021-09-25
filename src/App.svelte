<main id="app">
  <header>
    <NavBar />
    <GetStarted />
  </header>

  <div class="body">
    <ShortenBox />
    <UrlList urlList={urlList}/>
    <Statistics />
  </div>
  <div>
    <BoostLinks />
    <Footer />
  </div>



</main>

<script lang="ts">
  import NavBar from "./components/NavBar.svelte"
  import GetStarted from "./components/GetStarted.svelte"
  import ShortenBox from "./components/ShortenBox.svelte"
  import UrlList from "./components/UrlList.svelte"
  import Statistics from "./components/Statistics.svelte" 
  import BoostLinks from "./components/BoostLinks.svelte";
  import Footer from "./components/Footer.svelte"

  let urlList:Object[] = [
    {"original": "http://localhost:5000","shorten":"http://localhost:5000"}
  ] 
</script>

<style type="text/scss">
  @import "./shared";
  #app {
    header {
      background: white;
    }
    body {
      background: #f0f1f6;
    }
  }
  @include media(">=tablet") {
    $max-w: $pc;
    $min-w: $tablet;
    #app {
      header , .body  {
        padding: 40px applyMath(260,30,$max-w,$min-w) 0; 
      }
    }
  }
  @include media("<tablet",">phone") {
    $max-w: $tablet;
    $min-w: $phone;
    #app {
      header , .body  {
        padding: 40px applyMath(30,10,$max-w,$min-w) 0; 
      }
    }
  }
  @include media("<=phone") {
    #app {
      header , .body  {
      padding: 40px 10px 0; 
      }
    }
  }
</style>

