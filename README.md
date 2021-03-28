# VUE AUDIO RECORDER AND PLAYBACK

A simple Audio recorder and player to record audio content.

![](https://raw.githubusercontent.com/pratikaher88/vue-audio-recorder-and-player/master/screenshot.png)

## Installation

```
npm i vue-audio-recorder-and-player --save
```

### Module
```
import vue-audio-recorder-and-player from 'vue-audio-recorder-and-player';
```

### Usage

Below is an example of how to handle recording result
```

<template>
  <div>
    <vue-audio-recorder-and-player @recordingstop="recordingStopped" />
  </div>
</template>
 
<script>

import vue-audio-recorder-and-player from 'vue-audio-recorder-and-player';
export default {
},
methods: {
    async recordingStopped(blob) {

      const readBlobAsBase64 = (blob) => {
          var reader = new FileReader();
          return new Promise((resolve) => {
            reader.addEventListener("load", function() {
              resolve(reader.result);
            }); 
            reader.readAsDataURL( blob );
              });
        };

      try {
          this.audioURL = await readBlobAsBase64(blob)  
        } catch (e) {
          console.warn(e.message)
        }

      console.log("here", this.audioURL) // Audio blob as base 64 string
    }
}
</script> 
 
<style lang="css">
</style> 
```

### Return voice recording

This line in package helps to send a response to the parent.

```
this.$emit('recordingstop', blob)
```

You can have a mehtod in the parent classs to fetch the response in a function as shown in the example above.

## Authors

[Pratik Aher](https://www.linkedin.com/in/pratikaher88/) - Developer

