<script>
 import { Button } from 'svelma'
 import { box } from 'tweetnacl'
 import { encodeBase64 } from 'tweetnacl-util'

 import PSpace from '../layout/PSpace.svelte'
 import DefLink from '../text/DefLink.svelte'

 import { Highlight } from 'svelte-highlight';
 import { javascript } from 'svelte-highlight/languages';
 import { obsidian } from 'svelte-highlight/styles';

 $: keygen = `nacl.box.keyPair()`

 let keyPair = null;
 let newKeyPair = () => {
  keyPair = box.keyPair();
 }
 newKeyPair();
</script>

<svelte:head>
  {@html obsidian}
</svelte:head>

<section class="section white-bg">
 <div class="container">
	 <h1 class="title">Tweet NaCl</h1>
		<h2 class="subtitle">A popular tool.</h2>

  <p>
   We want to be boring with our choice of crypto implementation.<br />
   <DefLink text={"Tweet NaCl"} url={"https://www.npmjs.com/package/tweetnacl"} /> is used by <DefLink text={"Keybase"} url={"https://github.com/keybase/node-nacl/blob/master/lib/tweetnacl.js"} />, <DefLink text={"MetaMask"} url={"https://github.com/MetaMask/eth-sig-util/pull/18/files"} />, et al.
  </p>

  <PSpace />

  <h2 class="subtitle">Keypair generation</h2>

  <p>
   The <DefLink text={"crypto subtle API"} url={"https://developer.mozilla.org/en-US/docs/Web/API/Crypto/subtle"} /> native to web browsers does not support the keypairs needed by NaCl and saltpack.<br />
   Keypair generation and storage is dangerous in web browsers but this is about the best we can do.
  </p>

  <PSpace />

  <Button type="is-primary" on:click={newKeyPair}>Generate keypair</Button>

  <PSpace />

  Code:
  <Highlight language={"javascript"} code={keygen} />

  <PSpace />

  Raw output:
  <Highlight language={"javascript"} code={JSON.stringify(keyPair)} />

  <PSpace />

  Pubkey base64:
  <Highlight language={"javascript"} code={encodeBase64(keyPair['publicKey'])} />

  <PSpace />
  Private key base64:

  <Highlight language={"javascript"} code={encodeBase64(keyPair['secretKey'])} />

 </div>
</section>
