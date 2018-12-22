<template>
<v-layout row wrap>
        <v-flex xs12>
                <v-card>
                        <v-card-title primary-title>
                                <div>
                                        <div class="headline text-xs-center" style="min-width: 95vw">Example Docs</div>
                                        <span class="text-xs-left" style="min-width: 100%">
                                                <p>
                                                        ## getlocalsolps<br>
                                                        <br>
                                                        **getlocalsolps**<br>
                                                        <br>
                                                        The `getlocalsolps` method returns the average local solutions per second since this node was started.<br>
                                                        <br>
                                                        ::: tip<br>
                                                        This is the same information shown on the metrics screen (if enabled).<br>
                                                        :::<br>
                                                        <br>
                                                        ### Arguments:<br>
                                                        <br>
                                                        Structure|Type|Description<br>
                                                        ---------|----|-----------<br>
                                                        (none)                                       |                             |<br>
                                                        <br>
                                                        ### Response:<br>
                                                        Structure|Type|Description<br>
                                                        ---------|----|-----------<br>
                                                        "data"                                       |(numeric)                    |solutions per second average<br>
                                                        <br>
                                                        #### :pushpin: Examples:<br>
                                                        <br>
                                                        Command:<br>
                                                        <br>
                                                        ```bash<br>
                                                        ./komodo-cli getlocalsolps<br>
                                                        ```<br>
                                                        <br>
                                                        Response:<br>
                                                        <br>
                                                        ```bash<br>
                                                        0.4141607577247555<br>
                                                        ```<br>
                                                        <br>
                                                        You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.<br>
                                                        <br>
                                                        Command:<br>
                                                        <br>
                                                        ```bash<br>
                                                        curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getlocalsolps", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/<br>
                                                        ```<br>
                                                        <br>
                                                        Response:<br>
                                                        <br>
                                                        ```json<br>
                                                        {<br>
                                                                "result": 0.4141607577247555,<br>
                                                                "error": null,<br>
                                                                "id": "curltest"<br>
                                                        }<br>
                                                        ```<br>
                                                        <br>
                                                </p>
                                        </span>
                                </div>
                        </v-card-title>
                </v-card>
        </v-flex>
</v-layout>
</template>
