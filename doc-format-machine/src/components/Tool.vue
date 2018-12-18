<template>
	<div class="text-center">
		<v-card
		class="ma-2 mt-3"
		style="max-width: 100%; margin: auto;"
		>
		<v-container
		fluid
		grid-list-lg
		>
		<v-layout row wrap>
			<v-flex xs12>
				<v-card color="blue-grey darken-4" class="white--text">
					<v-card-title primary-title>
						<div>
							<div class="headline text-xs-center">RPC Editing Tool</div>
							<div class="subheading text-xs-center">Instructions</div>
							<span class="text-xs-left">
								<p>The goal of this simple RPC GUI is to facilitate Komodo contributors in creating uniform documentation. The GUI takes your details and applies a specific style-set to the markdown required for our Vuepress docs. </p>
								<p>By keeping the markdown and writing style as homogenous and uniform as possible across all contributors, we are able to make changes much more quickly with scripts and databases, as opposed to manually reformatting each time a major structural change arises. </p>
								<p>In the first box you add the basic RPC aspects. In the second and third boxex, you add an argument and response, one-at-a-time. In the fourth box, you add an example and its description, one-at-a-time. </p>
								<p>If you wish to delete anything in the process, simply click the `delete` button to the right of the final `Result` value. </p>
								<p>Anything that is additional to your RPC Call should go in the fifth, `Additional`, box. Make sure to write everything in this box using the markdown format for Vuepress. Look at the raw documentation <a href="https://github.com/KomodoPlatform/developer-docs/tree/master/docs/basic-docs">in GitHub</a> for examples. </p>
								<p>Please <a href="https://github.com/siddhartha-komodo/">reach out to me</a> if you have questions.</p>
							</span>
						</div>
					</v-card-title>
				</v-card>
			</v-flex>
		</v-layout>
		<v-layout row wrap>
			<v-flex xs4>
				<v-card class="mt-2">
					<v-card-title primary-title>
						<div>
							<div class="headline text-xs-center" style="min-width: 100%">Primary RPC Details</div>

							<v-form>
								<v-textarea
								class="mt-2 mb-2"
								name="rpc-title"
								label="RPC Name"
								v-model="name"
								hint="For example: `sendtoaddress`"
								persistent-hint="true"
								/>
								<v-textarea
								class="mt-2 mb-2"
								name="rpc-descriptive-example"
								label="Descriptive Example"
								v-model="descriptiveExample"
								hint="For example: `sendtoaddress destination_address amount"
								persistent-hint="true"
								/>
								<v-textarea
								class="mt-2 mb-2"
								name="rpc-description"
								label="Detailed RPC Description"
								v-model="description"
								hint="For example: The `sendtoaddress` method sends the `amount` of funds to `destination_address`."
								persistent-hint="true"
								/>
							</v-form>
						</div>
					</v-card-title>
				</v-card>
				<v-card class="mt-2">
					<v-card-title primary-title>
						<div>
							<div class="headline text-xs-center" style="min-width: 100%">Arguments</div>

							<div>
								<v-textarea
								class="mt-2 mb-2"
								name="argument-name"
								label="Argument Name"
								v-model="argumentName"
								hint="For example: amount"
								persistent-hint="true"
								/>
								<v-textarea
								class="mt-2 mb-2"
								name="argument-type"
								label="Argument Type"
								v-model="argumentType"
								hint="We recommend looking at other type values in the documentation. Avoid creating new types, and instead reuse existing type values, such as ` an array of strings`. Example for amount: number"
								persistent-hint="true"
								/>
								<v-textarea
								class="mt-2 mb-2"
								name="argument-description"
								label="Argument Description"
								v-model="argumentDescription"
								hint="Description of the argument. Don't use a capital letter for the first sentence. Try to use `;` semi-colons instead of periods. Use the articles `the` and `a`, to keep the phrasing natural. Only end in a `.` period if the description necessitates becoming so long, it becomes awkward. For example: the amount of funds to send"
								persistent-hint="true"
								/>
							</div>
							<v-card-actions>
								<v-btn class="mt-2" v-on:click="addArgument">Submit Argument</v-btn>
							</v-card-actions>
						</div>
					</v-card-title>
				</v-card>
				<v-card class="mt-2">
					<v-card-title primary-title>
						<div>
							<div class="headline text-xs-center" style="min-width: 100%">Response</div>

							<div>
								<v-textarea
								class="mt-2 mb-2"
								name="response-name"
								label="Response Name"
								v-model="responseName"
								hint="The name of this response value. To prevent confusion for a fast reader, try to avoid using extremely abbreviated terminology, such as `txid`. Instead, use the full term: transaction_id"
								persistent-hint="true"
								/>
								<v-textarea
								class="mt-2 mb-2"
								name="response-type"
								label="Response Type"
								v-model="responseType"
								hint="We recommend looking at other type values in the documentation. Avoid creating new types, and instead reuse existing type values, such as ` an array of strings`. Example for transaction_id: string"
								persistent-hint="true"
								/>
								<v-textarea
								class="mt-2 mb-2"
								name="response-description"
								label="Response Description"
								v-model="responseDescription"
								hint="Description of the response value. Don't use a capital letter for the first sentence. Try to use `;` semi-colons instead of periods. Use the articles `the` and `a`, to keep the phrasing natural. Only end in a `.` period if the description necessitates becoming so long, it becomes awkward. For example: the transaction id for this transaction"
								persistent-hint="true"
								/>
							</div>
							<v-card-actions>
								<v-btn class="mt-2" v-on:click="addResponse">Submit Response</v-btn>
							</v-card-actions>
						</div>
					</v-card-title>
				</v-card>
				<v-card class="mt-2">
					<v-card-title primary-title>
						<div>
							<div class="headline text-xs-center" style="min-width: 100%">Example</div>

							<div>
								<v-textarea
								class="mt-2 mb-2"
								name="example-input-description"
								label="Example Input Description"
								v-model="exampleInputDescription"
								hint="A description of the example's input. It should be short."
								persistent-hint="true"
								/>
								<v-textarea
								class="mt-2 mb-2"
								name="terminal-input"
								label="Full Terminal Input"
								v-model="exampleInput"
								hint="The ENTIRE input for the example. Generally, DO NOT abbreviate anything; the only exceptions are private keys and other strings/parameters that could be accidentally entered by the developer, and which would then result in a loss of funds."
								persistent-hint="true"
								/>
								<v-textarea
								class="mt-2 mb-2"
								name="example-output-description"
								label="Example Output Description"
								v-model="exampleOutputDescription"
								hint="A description of the example's output. It should be short."
								persistent-hint="true"
								/>
								<v-textarea
								class="mt-2 mb-2"
								name="terminal-output"
								label="Full Terminal Output"
								v-model="exampleOutput"
								hint="The ENTIRE output for the example. As before, DO NOT abbreviate any information, except that which pertains to the security of private funds."
								persistent-hint="true"
								/>
								<v-textarea
								class="mt-2 mb-2"
								name="example-language"
								label="Example Language"
								v-model="exampleLanguage"
								hint="The language for the example. For example: bash, python, javascript, etc."
								persistent-hint="true"
								/>
							</div>
							<v-card-actions>
								<v-btn class="mt-2" v-on:click="addExample">Submit Example</v-btn>
							</v-card-actions>
						</div>
					</v-card-title>
				</v-card>
				<v-card class="mt-2">
					<v-card-title primary-title>
						<div>
							<div class="headline text-xs-center" style="min-width: 100%">Additional Content</div>

							<div>
								<v-textarea
								class="mt-2 mb-2"
								name="additional-content"
								label="Additional Content"
								v-model="additionalContent"
								hint="Use the appropriate markdown format for any content provided here. See the raw documentation for examples."
								persistent-hint="true"
								/>
								<span class="subheading">
									Where should this be placed?
								</span>
								<v-radio-group v-model="groupPlacement">
									<v-radio
									:key="0"
									:label="`After the RPC Name`"
									:value="0"
									></v-radio>
									<v-radio
									:key="1"
									:label="`After the RPC Descriptive Example`"
									:value="1"
									></v-radio>
									<v-radio
									:key="2"
									:label="`After the RPC Description`"
									:value="2"
									></v-radio>
									<v-radio
									:key="3"
									:label="`After the Arguments`"
									:value="3"
									></v-radio>
									<v-radio
									:key="4"
									:label="`After the Responses`"
									:value="4"
									></v-radio>
									<v-radio
									:key="5"
									:label="`After the examples`"
									:value="5"
									></v-radio>
								</v-radio-group>
							</div>
							<v-card-actions>
								<v-btn class="mt-2" v-on:click="addAdditionalContents">Submit Additional Content</v-btn>
							</v-card-actions>
						</div>
					</v-card-title>
				</v-card>
			</v-flex>
			<v-flex xs8>
				<v-card color="red darken-4" class="white--text mt-2">
					<v-card-title primary-title>
						<div>
							<div class="headline">Result Formatted for VuePress</div>
							<div class="subheading">
								Use the input boxes on the left to start the documentation. Once you have it close enough, select everything below and copy/paste it into your editor or IDE for further changes.
							</div>
<div class="mt-4" style=".pre-formatted { white-space: pre; }">
<pre>
# {{ insertBreak(name) }}<br>
<span v-for="(additional, id) in additionalContents.afterName" v-bind:key="id">
<br>
{{ additional.content }}<br>
</span>
<br>
**{{ descriptiveExample }}**<br>
<span v-for="(additional, id) in additionalContents.afterDescriptiveExample" v-bind:key="id">
<br>
{{ additional.content }}<br>
</span>
<br>
{{ description }}<br>
<span v-for="(additional, id) in additionalContents.afterDescription" v-bind:key="id">
<br>
{{ additional.content }}<br>
</span>
<br>
### Arguments:<br>
Name|Type|Description<br>
----|----|-----------<br>
<span v-if="args.length < 1 && argumentName === ''">
(none) | | <br>
</span>
<span v-for="(arg, id) in args" v-bind:key="id">
{{ arg.argName }} | {{ arg.argType }} | {{ arg.argDescription }}<br>
</span>
<span v-if="argumentName">
{{ argumentName }} | {{ argumentType }} | {{ argumentDescription }}<br>
</span>
<br>
<span v-for="(additional, id) in additionalContents.afterArguments" v-bind:key="id">
{{ additional.content }}<br>
<br>
</span>
### Response:<br>
Name|Type|Description<br>
----|----|-----------<br>
<span v-if="resps.length < 1 && responseName === ''">
(none) | | <br>
</span>
<span v-for="(resp, id) in resps" v-bind:key="id">
{{ resp.respName  }} | {{ resp.respType }} | {{ resp.respDescription }}<br>
</span>
<span v-if="responseName">{{ responseName }} | {{ responseType }} | {{ responseDescription }}<br></span>
<br>
<span v-for="(additional, id) in additionalContents.afterResponse" v-bind:key="id">
<br>
{{ additional.content }}<br>
<br>
</span>
#### :pushpin: Examples:<br>
<span v-if="examples.length < 1 && exampleInput === ''">
[Example Here - Include Full Input and Output]<br>
[Click Submit when Finished]
<br>
</span>
<span v-for="(example, id) in examples" v-bind:key="id">
<br>
{{ example.exampInputDesc }}<br>
<br>
:::{{ example.exampLang }}<br>
{{ example.exampInput }}<br>
:::<br>
<br>
{{ example.exampOutputDesc }}<br>
<br>
:::{{ example.exampLang }}<br>
{{ example.exampOutput }}<br>
:::<br>
</span>
<span v-for="(additional, id) in additionalContents.afterExamples" v-bind:key="id">
<br>
{{ additional.content }}<br>
</span>
</pre>
</div>
						</div>
					</v-card-title>
				</v-card>
			</v-flex>
		</v-layout>
		<v-layout row wrap>
			<v-flex xs12>
				<v-card>
					<v-card-title primary-title>
						<div>
							<div class="headline text-xs-center">Example Docs</div>
							<span class="text-xs-left">
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
	</v-container>
</v-card>
</div>
</template>

<script>
export default {
	data: function() {
		return {
			name: 'RPC Name',
			descriptiveExample: 'descriptive example',
			description: 'The [RPCCall] method...',
			argumentName: '',
			argumentType: '',
			argumentDescription: '',
			responseName: '',
			responseType: '',
			responseDescription: '',
			exampleInputDescription: 'Command:',
			exampleInput: '',
			exampleOutputDescription: 'Response:',
			exampleOutput: '',
			exampleLanguage: 'bash',
			groupPlacement: 5,
			args: [
			],
			resps: [
			],
			examples: [
			],
			additionalContent: '',
			additionalContents: {
				afterName: [

				],
				afterDescriptiveExample: [

				],
				afterDescription: [

				],
				afterArguments: [

				],
				afterResponses: [

				],
				afterExamples: [

				]
			}
		}
	},
	computed: {
		calculateExampleOutput() {
			return this.exampleOutput
		}
	},
	methods: {
		insertBreak(textData) {
			textData = textData.replace('\n', '`<br/>`\n')
			return textData
		},
		clearArgumentField() {
			this.argumentName = ''
			this.argumentType = ''
			this.argumentDescription = ''
		},
		addArgument() {

			let argumentNameInsert = this.insertBreak(this.argumentName)
			let argumentTypeInsert = this.insertBreak(this.argumentType)
			let argumentDescription = this.insertBreak(this.argumentDescription)

			this.args.push({
				argName: argumentNameInsert,
				argType: argumentTypeInsert,
				argDescription: argumentDescription
			})
			this.clearArgumentField()
		},
		clearResponseField() {
			this.responseName = ''
			this.responseType = ''
			this.responseDescription = ''
		},
		addResponse() {
			let responseNameInsert = this.insertBreak(this.responseName)
			let responseTypeInsert = this.insertBreak(this.responseType)
			let responseDescription = this.insertBreak(this.responseDescription)

			this.resps.push({
				respName: responseNameInsert,
				respType: responseTypeInsert,
				respDescription: responseDescription
			})
			this.clearResponseField()
		},
		clearExampleField() {
			this.exampleInputDescription = 'Command:'
			this.exampleInput = ''
			this.exampleOutputDescription = 'Response:'
			this.exampleOutput = ''
			this.exampleLanguage = 'bash'
		},
		addExample() {

			let exampleInputDescriptionInsert = this.insertBreak(this.exampleInputDescription)
			let exampleInputInsert = this.insertBreak(this.exampleInput)
			let exampleOutputDescriptionInsert = this.insertBreak(this.exampleOutputDescription)
			let exampleLanguageInsert = this.insertBreak(this.exampleLanguage)
			let exampleOutputInsert = this.insertBreak(this.exampleOutput)

			this.examples.push({
				exampInputDesc: exampleInputDescriptionInsert,
				exampInput: exampleInputInsert,
				exampOutputDesc: exampleOutputDescriptionInsert,
				exampLang: exampleLanguageInsert,
				exampOutput: exampleOutputInsert
			})

			this.clearExampleField()
		},
		clearAdditional() {
			this.additionalContent = ''
			this.groupPlacement = 5
		},
		addAdditionalContents() {

			let additionalContentInsert = this.insertBreak(this.additionalContent)

			switch (this.groupPlacement) {

				case 0:

				this.additionalContents.afterName.push({
					content: additionalContentInsert
				})

				this.clearAdditional()
				break

				case 1:

				this.additionalContents.afterDescriptiveExample.push({
					content: additionalContentInsert
				})

				this.clearAdditional()
				break

				case 2:

				this.additionalContents.afterDescription.push({
					content: additionalContentInsert
				})

				this.clearAdditional()
				break

				case 3:

				this.additionalContents.afterArguments.push({
					content: additionalContentInsert
				})

				this.clearAdditional()
				break

				case 4:

				this.additionalContents.afterResponses.push({
					content: additionalContentInsert
				})

				this.clearAdditional()
				break

				case 5:

				this.additionalContents.afterExamples.push({
					content: additionalContentInsert
				})
				this.clearAdditional()

				break

			}
		}
	}
}
</script>
