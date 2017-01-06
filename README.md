README:

The point of this repo is to create the ability to log successful bitcoin transactions on the
bitcoin network directly to a datastore of your choice as opposed to logging to the bitcoin blockchain.
As the code progresses you will be able to just create a logger in modular fashion to log to your own datastore.

Datastores I'm planning to log to:

* DynamoDB
* MySQL
* Elasticsearch

This code makes use of the wonderful full bitcoin node written in Go: btcd, you can read more about that here.
https://github.com/btcsuite/btcd


I got some help with starting finding a point to start this code on the IRC channel on freenode from @davec:
<pre>
...
12:31 <@davec> The first thing you'd want to do is register for https://github.com/btcsuite/btcd/blob/master/docs/json_rpc_api.md#notifynewtransactions?
12:32 <@davec> if you're using the btcrpcclient, the function is https://godoc.org/github.com/btcsuite/btcrpcclient#Client.NotifyNewTransactions
12:33 <@davec> then you'll want to setup the handler for the https://github.com/btcsuite/btcd/blob/master/docs/json_rpc_api.md#txaccepted (or the verbose variant depending on
               what you want)
12:34 <@davec> with the btcrpcclient that is the "OnTxAccepted" field of the https://godoc.org/github.com/btcsuite/btcrpcclient#NotificationHandlers
12:34 <@davec> at that point you'll be gettin real time notifications of all txns as they show up on the network
12:34 <@davec> you can do whatever you like with the data then
...
</pre>


To run export following environment variables and run:

<pre>

$ export RPC_USER="someusername"

$ export RPC_PASS="someveryrandompassword"

$ go run main.go


</pre>
