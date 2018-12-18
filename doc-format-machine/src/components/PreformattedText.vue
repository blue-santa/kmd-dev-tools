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
