<template>
	<v-card 
		class="ma-2 mt-4"
		style="max-width: 500px; margin: auto;"
	>
		<v-container
			fluid
			grid-list-lg
		>
			<v-layout row wrap>
				<v-flex xs12>
					<v-card color="blue darken-4" class="white--text mt-2">
						<v-card-title primary-title>
							<div>
								<div class="headline">RPC Editing Tool</div>
								<span>Instructions Element</span>
							</div>
						</v-card-title>
					</v-card>
					<v-card class="mt-2">
						<v-card-title primary-title>
							<div>
								<div class="headline text-xs-center" style="min-width: 100%">Enter RPC Details</div>

								<div>
									<v-text-field
										class="mt-2 mb-2"
										name="rpc-title"
										label="RPC Name"
										value=""
										hint="For example: `sendtoaddress`"
									/>
									<v-text-field
										class="mt-2 mb-2"
										name="rpc-sterilized-example"
										label="Sterlized Example Text"
										value=""
										hint="For example: `sendtoaddress destination_address amount" 
									/>
									<v-text-field
										class="mt-2 mb-2"
										name="rpc-description"
										label="Sterlized Example Text"
										value=""
										hint="For example: `sendtoaddress destination_address amount" 
									/>
								</div>
								<v-card-actions>
									<v-btn class="mt-2">Submit</v-btn>
								</v-card-actions>
							</div>
						</v-card-title>
					</v-card>
					<v-card color="red darken-4" class="white--text mt-2">
						<v-card-title primary-title>
							<div>
								<div class="headline">Result:</div>
							</div>
						</v-card-title>
					</v-card>
				</v-flex>
			</v-layout>
		</v-container>
	</v-card>
</template>
