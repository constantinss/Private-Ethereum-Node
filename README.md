

# Set up a private Ethereum Node

Manual For Linux Distribution

First use Ethereum private network manager, called Puppeth:

This tool lets you create a new Ethereum network down to the genesis block, bootnodes, miners and ethstats servers without the hassle that it would normally entail. Puppeth uses SSH to dial in to remote servers, and builds its network components out of Docker containers using the docker-compose toolset.

You can start your terminal and type:

~/private$ puppeth

Please specify a network name to administer (no spaces, hyphens or capital letters please)

>\&gt; genesis_network

What would you like to do? (default = stats)

 1. Show network stats

 2. Configure new genesis

 3. Track new remote server

 4. Deploy network components

>\&gt;2

What would you like to do? (default = create)

1. Create new genesis from scratch

2. Import already existing genesis

>\&gt; 1

Which consensus engine to use? (default = clique)

1. Ethash - proof-of-work

2. Clique - proof-of-authority_

>\&gt; 1

Which accounts should be pre-funded? (advisable at least one)
>\&gt; 0x

Should the precompile-addresses (0x1 .. 0xff) be pre-funded with 1 wei? (advisable yes)
>\&gt; y

Specify your chain/network ID if you want an explicit one (default = random)
>\&gt; 4224

Configured new genesis block

What would you like to do? (default = stats)
1. Show network stats
2. Manage existing genesis
3. Track new remote server
4. Deploy network components

>\&gt; 2

1. Modify existing fork rules
2. Export genesis configurations
3. Remove genesis configuration
>\&gt; 2_

Which folder to save the genesis specs into? (default = current)
Will create genesis\_network.json, genesis\_network-aleth.json, genesis\_network-harmony.json, genesis\_network-parity.json_
>\&gt; [ENTER]

Than exit from this process by [Ctrl + C].

        _~/private$ geth --datadir . init genesis\_network.json_

That&#39;s how you wrote your custom genesis block. Now create new account:

        _~/private$ geth --datadir . account new_

_        Passphrase: [password364]_

_        Repeat passphrase: [password364]_

_If you write something else, you must configure in ./password.sec_

        _$ geth --datadir . account list_

Start startnode.sh script to run miners.

_~/private$ chmod +x startnode.sh_

_~/private$ ./startnode.sh_

_You will see something like that:_

_INFO [03-08|15:33:19.411] 🔗 block reached canonical chain              number=1 hash=410e77…e4ecea_

_INFO [03-08|15:33:19.411] 🔨 mined potential block                      number=8 hash=ac2842…0ae9e5_

_INFO [03-08|15:33:19.411] Commit new mining work                       number=9 sealhash=794d0e…0c8111 uncles=0 txs=0 gas=0 fees=0 elapsed=126.326µs_

_INFO [03-08|15:33:21.284] Successfully sealed new block                number=9 sealhash=794d0e…0c8111 hash=b59861…c900cc elapsed=1.872s_

_INFO [03-08|15:33:21.284] 🔗 block reached canonical chain              number=2 hash=af6df4…91dd7e_

_INFO [03-08|15:33:21.284] 🔨 mined potential block                      number=9 hash=b59861…c900cc_

_INFO [03-08|15:33:21.284] Commit new mining work                       number=10 sealhash=925090…5dfe50 uncles=0 txs=0 gas=0 fees=0 elapsed=205.569µs_

_INFO [03-08|15:33:26.485] Successfully sealed new block                number=10 sealhash=925090…5dfe50 hash=86b4e8…1a9093 elapsed=5.200s_

_INFO [03-08|15:33:26.485] 🔗 block reached canonical chain              number=3  hash=68e8bd…545faa_

_INFO [03-08|15:33:26.485] 🔨 mined potential block                      number=10 hash=86b4e8…1a9093_

_INFO [03-08|15:33:26.485] Commit new mining work                       number=11 sealhash=5df01a…581bf3 uncles=0 txs=0 gas=0 fees=0 elapsed=121.381µs_

_INFO [03-08|15:33:27.789] Successfully sealed new block                number=11 sealhash=5df01a…581bf3 hash=d6f3d8…fe5515 elapsed=1.303s_

_INFO [03-08|15:33:27.789] 🔗 block reached canonical chain              number=4  hash=02b5be…98b113_

_INFO [03-08|15:33:27.789] 🔨 mined potential block                      number=11 hash=d6f3d8…fe5515_

_INFO [03-08|15:33:27.789] Commit new mining work                       number=12 sealhash=88907c…672fc0_

_\*         \*        \*_

Now connect to your node in new terminal while the script is running.

        _~$ geth attach_

_\&gt; eth.accounts_

_[&quot;0x68733cb74ac5ef1a89b683ed05a32deef2bd44e3&quot;]_

_\&gt; eth.coinbase_

_&quot;0x68733cb74ac5ef1a89b683ed05a32deef2bd44e3&quot;_

_\&gt; eth.getBalance(eth.coinbase)_

_152000000000000000000_

_\&gt; eth.getBalance(eth.coinbase)_

_154000000000000000000_

_\&gt; eth.getBalance(eth.coinbase)_

_156000000000000000000_

_\&gt; eth.getBalance(\*specify the address of account\*)_

Get ether from account one:

_\&gt; web3.fromWei(eth.getBalance(eth.accounts[1], &quot;ether&quot;)_

_\&gt;147_

Stop &amp; start miners:

        _\&gt;miner.stop()                        \&gt;miner.start()_

_        true       _

_Or see the specified network:_

_        \&gt;net.version_

_        &quot;4224&quot;_

