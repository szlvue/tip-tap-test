<template>
  <div id="app">
    <HelloWorld>
      <editor-menu-bar :editor="editor" v-slot="{ commands, isActive }">
        <div class="menubar">
          <button class="menubar__button" @click="commands['knowledge-item']({ id: 1, label: 'Philipp Kühn' })">
            <!-- <icon name="mention" /> -->
            <span>Insert Mention</span>
          </button>
          <button :class="{ 'is-active': isActive.bold() }" @click="commands.bold">
            Bold
          </button>
          <button
            class="menubar__button"
            :class="{ 'is-active': isActive.blockquote() }"
            @click="commands.blockquote"
          >
          blockquote
        </button>
        </div>        
      </editor-menu-bar>
      <editor-content :editor="editor" />
    </HelloWorld>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import { Editor, EditorContent, EditorMenuBar } from 'tiptap';
import { Heading, Bold, Blockquote } from 'tiptap-extensions';
import KnowledgeItem from './custom-nodes/knowledge-item';

export default {
  name: 'app',

  components: {
    HelloWorld,
    EditorContent,
    EditorMenuBar
  },
  data() {
    return {
      // Create an `Editor` instance with some default content. The editor is 
      // then passed to the `EditorContent` component as a `prop`
      editor: new Editor({
        content: '<p>This <h1>is</h1> just a boring paragraph</p>',
          extensions: [
            // The editor will accept paragraphs and headline elements as part of its document schema.
            new Heading({
              levels: [1, 2, 3],
            }),
            new Bold(),
            new KnowledgeItem(),
            new Blockquote(),
          ],
      }),
    }
  },
  beforeDestroy() {
    this.editor.destroy()
  },
}
</script>

<style lang="scss">
@import "./assets/sass/variables.scss";

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: $primary-text-color;
  margin-top: 60px;
}

blockquote {
  margin: 1rem 0;

  &:first-child {
    margin-top: 0;
  }

  &:last-child {
    margin-bottom: 0;
  }
  border-left: 3px solid rgba(#ffffff, 0.5);
  color: rgba(#ffffff, 0.8);
  padding-left: 0.8rem;
  font-style: italic;

  p {
    margin: 0;
  }
}
.mention {
  color: black;
  background-color: #806464;
  border: 1px solid #ddda00;
  border-radius: 4px;
  padding: 2px;
  margin: 1px;
  border-spacing: 15px;
  display: inline-block;
}
</style>
