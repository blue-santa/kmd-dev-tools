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
										<v-text-field
											class="mt-2 mb-2"
											name="rpc-title"
											label="RPC Name"
											v-model="name"
											hint="For example: `sendtoaddress`"
										/>
										<v-text-field
											class="mt-2 mb-2"
											name="rpc-descriptive-example"
											label="Descriptive Example"
											v-model="descriptiveExample"
											hint="For example: `sendtoaddress destination_address amount" 
										/>
										<v-text-field
											class="mt-2 mb-2"
											name="rpc-description"
											label="Detailed RPC Description"
											v-model="description"
											hint="For example: `The `sendtoaddress` method sends the `amount` of funds to `destination address`."
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
										<v-text-field
											class="mt-2 mb-2"
											name="argument-name"
											label="Argument Name"
											v-model="argumentName"
											hint="For example: amount"
										/>
										<v-text-field
											class="mt-2 mb-2"
											name="argument-type"
											label="Argument Type"
											v-model="argumentType"
											hint="We recommend looking at other type values in the documentation. Avoid creating new types, and instead reuse existing type values, such as ` an array of strings`. Example for amount: number"
										/>
										<v-text-field
											class="mt-2 mb-2"
											name="argument-description"
											label="Argument Description"
											v-model="argumentDescription"
											hint="Description of the argument. Don't use a capital letter for the first sentence. Try to use `;` semi-colons instead of periods. Use the articles `the` and `a`, to keep the phrasing natural. Only end in a `.` period if the description necessitates becoming so long, it becomes awkward. For example: the amount of funds to send"
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
										<v-text-field
											class="mt-2 mb-2"
											name="response-name"
											label="Response Name"
											value=""
											hint="The name of this response value. To prevent confusion for a fast reader, try to avoid using extremely abbreviated terminology, such as `txid`. Instead, use the full term: transaction_id"
										/>
										<v-text-field
											class="mt-2 mb-2"
											name="response-type"
											label="Response Type"
											value=""
											hint="We recommend looking at other type values in the documentation. Avoid creating new types, and instead reuse existing type values, such as ` an array of strings`. Example for transaction_id: string"
										/>
										<v-text-field
											class="mt-2 mb-2"
											name="response-description"
											label="Response Description"
											value=""
											hint="Description of the response value. Don't use a capital letter for the first sentence. Try to use `;` semi-colons instead of periods. Use the articles `the` and `a`, to keep the phrasing natural. Only end in a `.` period if the description necessitates becoming so long, it becomes awkward. For example: the transaction id for this transaction"
										/>
									</div>
									<v-card-actions>
										<v-btn class="mt-2">Submit Response</v-btn>
									</v-card-actions>
								</div>
							</v-card-title>
						</v-card>
						<v-card class="mt-2">
							<v-card-title primary-title>
								<div>
									<div class="headline text-xs-center" style="min-width: 100%">Example</div>

									<div>
										<v-text-field
											class="mt-2 mb-2"
											name="example-description"
											label="Example Description"
											value=""
											hint="A description of the example. It should be short."
										/>
										<v-text-field
											class="mt-2 mb-2"
											name="terminal-input"
											label="Full Terminal Input"
											value=""
											hint="The ENTIRE input for the example. Generally, DO NOT abbreviate anything; the only exceptions are private keys and other strings/parameters that could be accidentally entered by the developer, and which would then result in a loss of funds."
										/>
										<v-text-field
											class="mt-2 mb-2"
											name="terminal-output"
											label="Full Terminal Output"
											value=""
											hint="The ENTIRE output for the example. As before, DO NOT abbreviate any information, except that which pertains to the security of private funds."
										/>
									</div>
									<v-card-actions>
										<v-btn class="mt-2">Submit Example</v-btn>
									</v-card-actions>
								</div>
							</v-card-title>
						</v-card>
						<v-card class="mt-2">
							<v-card-title primary-title>
								<div>
									<div class="headline text-xs-center" style="min-width: 100%">Additional Content</div>

									<div>
										<v-text-field
											class="mt-2 mb-2"
											name="additional-content"
											label="Additional Content"
											value=""
											hint="Use the appropriate markdown format for any content provided here. See the raw documentation for examples."
										/>
										<span class="subheading">
											Where should this be placed?
										</span>
										<v-radio-group v-model="groupGoesHere">
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
										<v-btn class="mt-2">Submit Example</v-btn>
									</v-card-actions>
								</div>
							</v-card-title>
						</v-card>
					</v-flex>
					<v-flex xs8>
						<v-card color="red darken-4" class="white--text mt-2">
							<v-card-title primary-title>
								<div>
									<div class="headline">Result Formatted for VuePress:</div>
									<div class="mt-4">
										<p># {{ name }}<br>
										<br>
										**{{ descriptiveExample }}**<br>
										<br>
										The {{ name }} method {{ description }}<br>
										<br>
										### Arguments:<br>
										<span v-for="(test, id) in tests" v-bind:key="id">
											{{ test.something }}<br>
										</span>
										<br>
										Name|Type|Description<br>
										----|----|-----------<br>
										<span v-if="args[0].name">
											{{ console.log('here') }}
											{{ buildArgs() }}
										</span>
										<span v-if="argumentName">{{ argumentName }} | {{ argumentType }} | {{ argumentDescription }}<br></span>
										<span v-else>(none) | | <br></span>
										</p>
									</div>
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
			description: '...',
			argumentName: '',
			argumentType: '',
			argumentDescription: '',
			args: [
				{
					argName: '(none)',
					argType: '',
					argDescription: ''
				}
			],
			resps: {
				play: {
					name: '',
					type: '',
					description: ''
				}
			},
			examples: {
				play: {
					description: '',
					content: ''
				}
			},
			additional: {
				play: {
					content: '',
					value: 6
				}
			}
		}
	},
	computed: {
		buildArgs() {
			return this.args[0].argName + ' | ' + this.args[0].argType + ' | ' + this.args[0].argDescription
		}
	},
	methods: {
		addArgument() {
			this.args[this.args.length - 1] = {
				argName: this.argumentName,
				argType: this.argumentType,
				argDescription: this.argumentDescription
			}
			this.argumentName = ''
			this.argumentType = ''
			this.argumentDescription = ''
			this.args.push({	
				name: '',
				type: '',
				description: ''
			})
		}
	}
}
</script>
