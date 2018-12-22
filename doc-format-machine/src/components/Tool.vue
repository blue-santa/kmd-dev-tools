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
  <v-flex xs4>
    <v-card 
      class="scroll-y pr-1"
      id="scroll-target"
    >
      <div
        v-scroll:#scroll-target="onScroll"
        style="max-height: 85vh"
      >
          <introduction-component />
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
                                                name="example-input-language"
                                                label="Example Input Language"
                                                v-model="exampleInputLanguage"
                                                hint="The language for the input example. For example: bash, python, javascript, etc."
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
                                                name="example-output-language"
                                                label="Example Output Language"
                                                v-model="exampleOutputLanguage"
                                                hint="The language for the output example. For example: bash, python, javascript, etc."
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
              </div>
          </v-card>
        </v-flex>
        <v-flex xs8>

          <content-formatter 
            :test=test 
            :insertBreak=insertBreak 
            :name=name
            :descriptiveExample=descriptiveExample
            :description=description
            :argumentName=argumentName
            :argumentType=argumentType
            :argumentDescription=argumentDescription
            :responseName=responseName
            :responseType=responseType
            :responseDescription=responseDescription
            :exampleInputDescription=exampleInputDescription
            :exampleInput=exampleInput
            :exampleOutputDescription=exampleOutputDescription
            :exampleOutput=exampleOutput
            :exampleInputLanguage=exampleInputLanguage
            :exampleOutputLanguage=exampleOutputLanguage
            :groupPlacement=groupPlacement
            :args=args
            :resps=resps
            :examples=examples
            :additionalContent=additionalContent
            :additionalContents=additionalContents
          />
        </v-flex>
</v-layout>
<example-documents />
</v-container>
</v-card>
</div>
</template>

<script>
import ContentFormatter from './ToolSubcomponents/ContentFormatter.vue'
import IntroductionComponent from './ToolSubcomponents/IntroductionComponent.vue'
import ExampleDocuments from './ToolSubcomponents/ExampleDocuments.vue'

export default {
components: {
  ContentFormatter,
  IntroductionComponent,
  ExampleDocuments
},
data: function() {
  return {
          test: 'hello world',
          name: 'RPC Name',
          descriptiveExample: 'descriptive example',
          description: 'The `RPCCall` method...',
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
          exampleInputLanguage: 'bash',
          exampleOutputLanguage: 'json',
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
          textData = textData.replace('\n', '\n')
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
          let exampleOutputLanguageInsert = this.insertBreak(this.exampleOutputLanguage)
          let exampleInputLanguageInsert = this.insertBreak(this.exampleInputLanguage)
          let exampleOutputInsert = this.insertBreak(this.exampleOutput)

          this.examples.push({
                  exampInputDesc: exampleInputDescriptionInsert,
                  exampInput: exampleInputInsert,
                  exampOutputDesc: exampleOutputDescriptionInsert,
                  exampInLang: exampleInputLanguageInsert,
                  exampOutLang: exampleOutputLanguageInsert,
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
