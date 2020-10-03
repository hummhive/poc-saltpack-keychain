<script>
 import { Button } from 'svelma'
 import { box } from 'tweetnacl'
 import { encodeBase64 } from 'tweetnacl-util'

 import PSpace from '../layout/PSpace.svelte'
 import DefLink from '../text/DefLink.svelte'

 import { Highlight } from 'svelte-highlight'
 import { javascript } from 'svelte-highlight/languages'
 import { obsidian } from 'svelte-highlight/styles'

 import { entropyToMnemonic } from '@ethersproject/hdnode'

 let bytes = new Uint8Array(32)
 let newRandom = () => {
  let newBytes = new Uint8Array(32)
  crypto.getRandomValues(newBytes)
  bytes = newBytes
 }
 newRandom()
</script>

<svelte:head>
  {@html obsidian}
</svelte:head>

<section class="section white-bg">
 <div class="container">
	 <h1 class="title">Mnemonic seed phrase</h1>

  <p>
   Our exact choice of seed phrase generation is not so important.<br />
   This example uses <DefLink url={"https://docs.ethers.io/v5/"} text={"ethers.js"} /> but there are many options such as various <DefLink url={"https://bip49.com/"} text={"Bitcoin BIPs"} />.<br />
   Consistency in generation and restoration is most important so BIP39 is recommended.<br />
   Note that BIP39 is for representing secure randomness in a seed phrase, not for encoding relatively weak human passphrases or "brain wallets".<br />
   Note also that base64 is a far more compact format, compatible with URLs.
  </p>

  <PSpace />

  <p>
   This example uses the browser native <code>crypto.getRandomValues</code> API.<br />
   Most high level libraries, including Tweet NaCl provide their own methods for randomness that should be used instead.<br />
  </p>


  <PSpace />

  <Button type="is-primary" on:click={newRandom}>Generate 32 random bytes</Button>

  <PSpace />

  Bytes:
  <Highlight language={"javascript"} code={bytes} />

  <PSpace />

  Bytes base64:
  <Highlight language={"javascript"} code={encodeBase64(bytes)} />

  <PSpace />
  Bytes mnemonic:
  <Highlight language={"javascript"} code={entropyToMnemonic(bytes)} />

  <PSpace />

  <p>
   Ed25519 public keys can be generated for any 32 byte private key.<br />
   BIP39 mnemonics all map to Tweet NaCl compatible public keys.
  </p>

  <PSpace />

  Bytes/mnemonic keypair:
  <Highlight language={"javascript"} code={JSON.stringify(box.keyPair.fromSecretKey(bytes))} />

 </div>
</section>
