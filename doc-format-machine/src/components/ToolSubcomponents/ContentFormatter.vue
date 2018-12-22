<template>
  <div>
    <v-card color="black" class="white--text mb-2">
      <v-card-title primary-title>
        <div class="headline text-xs-center" style="min-width: 100%">Result Formatted for Vuepress</div>
        <div class="subheading">
          Use the input boxes on the left to start the documentation. Once you have it close enough, select everything below and copy/paste it into your editor or IDE for further changes.
        </div>
      </v-card-title>
    </v-card>
    <v-card 
      color="red darken-4" 
      class="white--text scroll-y"
      id="scroll-target"
    >
      <v-card-title primary-title>
        <div
          v-scroll:#scroll-target="onScroll"
          style="max-height: 66.5vh"
        >
          <div class="mt-2 mb-2" style=".pre-formatted { white-space: pre-wrap; }">

<!-- Begin Pre here -->
  
<pre>
## {{ insertBreak(name) }} 
</pre>

<br>

<span v-for="(additional, id) in additionalContents.afterName" v-bind:key="id">
<pre>
{{ additional.content }}
</pre>
<br>
</span>

<pre>
**{{ descriptiveExample }}**
</pre>

<br>

<span v-for="(additional, id) in additionalContents.afterDescriptiveExample" v-bind:key="id">
<pre>
{{ additional.content }}
</pre>
<br>
</span>

<pre>
{{ description }}
</pre>

<br>

<span v-for="(additional, id) in additionalContents.afterDescription" v-bind:key="id">
<pre>
{{ additional.content }}
</pre>
<br>
</span>

<pre>
### Arguments:
Name|Type|Description
----|----|-----------
</pre>

<span v-if="args.length < 1 && argumentName === ''">
  (none) | | <br>
</span>

<span v-for="(arg, id) in args" v-bind:key="id">
<pre>
{{ arg.argName }} | {{ arg.argType }} | {{ arg.argDescription }}
</pre>
</span>

<span v-if="argumentName">
<pre>
{{ argumentName }} | {{ argumentType }} | {{ argumentDescription }}
</pre>
</span>

<br>

<span v-for="(additional, id) in additionalContents.afterArguments" v-bind:key="id">
<pre>
{{ additional.content }}
</pre>
<br>
</span>

<pre>
### Response:
Name|Type|Description
----|----|-----------
</pre>

<span v-if="resps.length < 1 && responseName === ''">
  (none) | | <br>
</span>

<span v-for="(resp, id) in resps" v-bind:key="id">
<pre>
{{ resp.respName  }} | {{ resp.respType }} | {{ resp.respDescription }}
</pre>
</span>

<span v-if="responseName">
<pre>
{{ responseName }} | {{ responseType }} | {{ responseDescription }}
</pre>
</span>

<br>

<span v-for="(additional, id) in additionalContents.afterResponse" v-bind:key="id">
<pre>
{{ additional.content }}
</pre>
<br>
</span>

<pre>
#### :pushpin: Examples:
</pre>

<br>

<span v-if="examples.length < 1">
<pre>
[Example Here - Include ENTIRE Terminal Input and Output]
[Click Submit when Finished]
</pre>

</span>
<span v-for="(example, id) in examples" v-bind:key="id">

<pre>
{{ example.exampInputDesc }}
</pre>

<br>

:::{{ example.exampInLang }}<br>
<pre>
{{ example.exampInput }}
</pre>
:::<br>

<br>

<pre>
{{ example.exampOutputDesc }}
</pre>

<br>

:::{{ example.exampOutLang }}<br>
<pre>
{{ example.exampOutput }}
</pre>
:::<br>

<span v-if="examples.length > 1">
<br>
</span>

</span>

<br>

<span v-for="(additional, id) in additionalContents.afterExamples" v-bind:key="id">
<pre>
{{ additional.content }}
</pre>
<br>
</span>
</pre>


<!-- End Pre -->
        
          </div>
        </div>
      </v-card-title>
    </v-card>
  </div>
</template>


<script>

export default {
  data: function() {
    return {
    
    }
  },
  props: [
    'test',
    'insertBreak',
    'name',
    'descriptiveExample',
    'description',
    'argumentName',
    'argumentType',
    'argumentDescription',
    'responseName',
    'responseType',
    'responseDescription',
    'exampleInputDescription',
    'exampleInput',
    'exampleOutputDescription',
    'exampleOutput',
    'exampleInputLanguage',
    'exampleOutputLanguage',
    'groupPlacement',
    'args',
    'resps',
    'examples',
    'additionalContent',
    'additionalContents'
  ]
}
</script>
