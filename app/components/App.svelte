<style>
  h1 {
    font-family: "Comic Sans MS";
    font-weight: 300;
    color: purple;
    margin: 2em auto;
    text-align: center;
  }
</style>

<main>
  <h1>Hellocoo!</h1>
</main>

<script lang="ts">
  import { AlpacaStream } from '@master-chief/alpaca'
  import { config } from 'dotenv'
  config()

  const stream = new AlpacaStream(
    {
      credentials: {
        key: process.env.CLIENT,
        secret: process.env.secret,
      },
      stream: 'market_data'
    }
  )

  stream.on("aggregate_minute", console.log)

  stream.subscribe(['AM.GME'])

</script>