<p><span style="font-weight: 400;">Set up a private Ethereum Node</span></p>
<p><span style="font-weight: 400;">Manual For Linux Distribution</span></p>
<p><span style="font-weight: 400;">First use Ethereum private network manager, called Puppeth:</span></p>
<p>&nbsp;</p>
<p><span style="font-weight: 400;">This tool lets you create a new Ethereum network down to the genesis block, bootnodes, miners and ethstats servers without the hassle that it would normally entail. Puppeth uses SSH to dial in to remote servers, and builds its network components out of Docker containers using the docker-compose toolset.</span></p>
<p>&nbsp;</p>
<p><span style="font-weight: 400;">You can start your terminal and type: </span></p>
<p><em><span style="font-weight: 400;">~/private$ puppeth</span></em></p>
<p>&nbsp;</p>
<p><span style="font-weight: 400;">Please specify a network name to administer (no spaces, hyphens or capital letters please)</span></p>
<p><em><span style="font-weight: 400;">&gt; genesis_network</span></em></p>
<p>&nbsp;</p>
<p><span style="font-weight: 400;">What would you like to do? (default = stats)</span></p>
<ol>
<li><span style="font-weight: 400;"> Show network stats</span></li>
<li><span style="font-weight: 400;"> Configure new genesis</span></li>
<li><span style="font-weight: 400;"> Track new remote server</span></li>
<li><span style="font-weight: 400;"> Deploy network components</span></li>
</ol>
<p><em><span style="font-weight: 400;">&gt;2</span></em></p>
<p>&nbsp;</p>
<p><em><span style="font-weight: 400;">What would you like to do? (default = create)</span></em></p>
<ol>
<li><em><span style="font-weight: 400;"> Create new genesis from scratch</span></em></li>
<li><em><span style="font-weight: 400;"> Import already existing genesis</span></em></li>
</ol>
<p><em><span style="font-weight: 400;">&gt; 1</span></em></p>
<p>&nbsp;</p>
<p><em><span style="font-weight: 400;">Which consensus engine to use? (default = clique)</span></em></p>
<ol>
<li><em><span style="font-weight: 400;"> Ethash - proof-of-work</span></em></li>
<li><em><span style="font-weight: 400;"> Clique - proof-of-authority</span></em></li>
</ol>
<p><em><span style="font-weight: 400;">&gt; 1</span></em></p>
<p>&nbsp;</p>
<p><em><span style="font-weight: 400;">Which accounts should be pre-funded? (advisable at least one)</span></em></p>
<p><em><span style="font-weight: 400;">&gt; 0x</span></em></p>
<p>&nbsp;</p>
<p><em><span style="font-weight: 400;">Should the precompile-addresses (0x1 .. 0xff) be pre-funded with 1 wei? (advisable yes)</span></em></p>
<p><em><span style="font-weight: 400;">&gt; y &nbsp;&nbsp;</span></em></p>
<p>&nbsp;</p>
<p><em><span style="font-weight: 400;">Specify your chain/network ID if you want an explicit one (default = random)</span></em></p>
<p><em><span style="font-weight: 400;">&gt; 4224</span></em></p>
<p><em><span style="font-weight: 400;">Configured new genesis block</span></em></p>
<p>&nbsp;</p>
<p><em><span style="font-weight: 400;">What would you like to do? (default = stats)</span></em></p>
<ol>
<li><em><span style="font-weight: 400;"> Show network stats</span></em></li>
<li><em><span style="font-weight: 400;"> Manage existing genesis</span></em></li>
<li><em><span style="font-weight: 400;"> Track new remote server</span></em></li>
<li><em><span style="font-weight: 400;"> Deploy network components</span></em></li>
</ol>
<p><em><span style="font-weight: 400;">&gt; 2</span></em></p>
<p>&nbsp;</p>
<ol>
<li><em><span style="font-weight: 400;"> Modify existing fork rules</span></em></li>
<li><em><span style="font-weight: 400;"> Export genesis configurations</span></em></li>
<li><em><span style="font-weight: 400;"> Remove genesis configuration</span></em></li>
</ol>
<p><em><span style="font-weight: 400;">&gt; 2</span></em></p>
<p>&nbsp;</p>
<p><em><span style="font-weight: 400;">Which folder to save the genesis specs into? (default = current)</span></em></p>
<p><em><span style="font-weight: 400;"> &nbsp;Will create genesis_network.json, genesis_network-aleth.json, genesis_network-harmony.json, genesis_network-parity.json</span></em></p>
<p><em><span style="font-weight: 400;">&gt; [ENTER]</span></em></p>
<p>&nbsp;</p>
<p><span style="font-weight: 400;">Than exit from this process by [Ctrl + C].</span></p>
<p>&nbsp;</p>
<p><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span><em><span style="font-weight: 400;">~/private$ geth --datadir . init genesis_network.json</span></em></p>
<p>&nbsp;</p>
<p><span style="font-weight: 400;">That&rsquo;s how you wrote your custom genesis block. Now create new account:</span></p>
<p><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span><em><span style="font-weight: 400;">~/private$ geth --datadir . account new</span></em></p>
<p><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">Passphrase: [password364]</span></em></p>
<p><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">Repeat passphrase: [password364]</span></em></p>
<p>&nbsp;</p>
<p><em><span style="font-weight: 400;">If you write something else, you must configure in ./password.sec</span></em></p>
<p><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span><em><span style="font-weight: 400;">$ geth --datadir . account list</span></em></p>
<p><span style="font-weight: 400;">Start startnode.sh script to run miners.</span></p>
<p>&nbsp;</p>
<p><em><span style="font-weight: 400;">~/private$ chmod +x startnode.sh</span></em></p>
<p><em><span style="font-weight: 400;">~/private$ ./startnode.sh</span></em></p>
<p>&nbsp;</p>
<p><em><span style="font-weight: 400;">You will see something like that:</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:19.411] 🔗 block reached canonical chain &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=1 hash=410e77&hellip;e4ecea</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:19.411] 🔨 mined potential block &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=8 hash=ac2842&hellip;0ae9e5</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:19.411] Commit new mining work &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=9 sealhash=794d0e&hellip;0c8111 uncles=0 txs=0 gas=0 fees=0 elapsed=126.326&micro;s</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:21.284] Successfully sealed new block &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=9 sealhash=794d0e&hellip;0c8111 hash=b59861&hellip;c900cc elapsed=1.872s</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:21.284] 🔗 block reached canonical chain &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=2 hash=af6df4&hellip;91dd7e</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:21.284] 🔨 mined potential block &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=9 hash=b59861&hellip;c900cc</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:21.284] Commit new mining work &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=10 sealhash=925090&hellip;5dfe50 uncles=0 txs=0 gas=0 fees=0 elapsed=205.569&micro;s</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:26.485] Successfully sealed new block &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=10 sealhash=925090&hellip;5dfe50 hash=86b4e8&hellip;1a9093 elapsed=5.200s</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:26.485] 🔗 block reached canonical chain &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=3 &nbsp;hash=68e8bd&hellip;545faa</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:26.485] 🔨 mined potential block &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=10 hash=86b4e8&hellip;1a9093</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:26.485] Commit new mining work &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=11 sealhash=5df01a&hellip;581bf3 uncles=0 txs=0 gas=0 fees=0 elapsed=121.381&micro;s</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:27.789] Successfully sealed new block &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=11 sealhash=5df01a&hellip;581bf3 hash=d6f3d8&hellip;fe5515 elapsed=1.303s</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:27.789] 🔗 block reached canonical chain &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=4 &nbsp;hash=02b5be&hellip;98b113</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:27.789] 🔨 mined potential block &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=11 hash=d6f3d8&hellip;fe5515</span></em></p>
<p><em><span style="font-weight: 400;">INFO [03-08|15:33:27.789] Commit new mining work &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">number=12 sealhash=88907c&hellip;672fc0 </span></em></p>
<p><em><span style="font-weight: 400;">* </span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">*</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;"> *</span></em></p>
<p>&nbsp;</p>
<p><span style="font-weight: 400;">Now connect to your node in new terminal while the script is running. </span></p>
<p><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span><em><span style="font-weight: 400;">~$ geth attach</span></em></p>
<p><em><span style="font-weight: 400;">&gt; eth.accounts</span></em></p>
<p><em><span style="font-weight: 400;">["0x68733cb74ac5ef1a89b683ed05a32deef2bd44e3"]</span></em></p>
<p><em><span style="font-weight: 400;">&gt; eth.coinbase</span></em></p>
<p><em><span style="font-weight: 400;">"0x68733cb74ac5ef1a89b683ed05a32deef2bd44e3"</span></em></p>
<p><em><span style="font-weight: 400;">&gt; eth.getBalance(eth.coinbase)</span></em></p>
<p><em><span style="font-weight: 400;">152000000000000000000</span></em></p>
<p><em><span style="font-weight: 400;">&gt; eth.getBalance(eth.coinbase)</span></em></p>
<p><em><span style="font-weight: 400;">154000000000000000000</span></em></p>
<p><em><span style="font-weight: 400;">&gt; eth.getBalance(eth.coinbase)</span></em></p>
<p><em><span style="font-weight: 400;">156000000000000000000</span></em></p>
<p><em><span style="font-weight: 400;">&gt; eth.getBalance(*specify the address of account*)</span></em></p>
<p><span style="font-weight: 400;">Get ether from account one:</span></p>
<p><em><span style="font-weight: 400;">&gt; web3.fromWei(eth.getBalance(eth.accounts[1], "ether")</span></em></p>
<p><em><span style="font-weight: 400;">&gt;147</span></em></p>
<p><span style="font-weight: 400;">Stop &amp; start miners:</span></p>
<p><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span><em><span style="font-weight: 400;">&gt;miner.stop()</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">&gt;miner.start()</span></em></p>
<p><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">true</span></em><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em></p>
<p><em><span style="font-weight: 400;">Or see the specified network:</span></em></p>
<p><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">&gt;net.version</span></em></p>
<p><em><span style="font-weight: 400;">&nbsp;&nbsp;&nbsp; </span></em><em><span style="font-weight: 400;">&ldquo;4224&rdquo;</span></em></p>
