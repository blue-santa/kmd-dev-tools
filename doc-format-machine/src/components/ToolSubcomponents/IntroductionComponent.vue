<template>
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
</template>
