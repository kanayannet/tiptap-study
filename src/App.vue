<template>
  <div class="editor">
    <editor-menu-bar :editor="editor" v-slot="{ commands, isActive }">
      <div>
        <button :class="{ 'is-active': isActive.bold() }" @click="commands.bold">
          Bold
        </button>
        <button :class="{ 'is-active': isActive.italic() }" @click="commands.italic">
          Italic
        </button>
      </div>
    </editor-menu-bar>
    <editor-content :editor="editor" />
  </div>
</template>

<script>
// Import the basic building blocks
import { Editor, EditorContent, EditorMenuBar} from 'tiptap'
//import { Editor } from 'tiptap'
import { Bold, Italic, Link, HardBreak, Heading } from 'tiptap-extensions'

export default {
  components: {
    EditorMenuBar,
    EditorContent,
  },
  data() {
    return {
      editor: new Editor({
        content: 'aaaa',
        extensions: [
          new Bold(),
          new Italic(),
          new Link(),
          new HardBreak(),
          new Heading(),
        ],
      }),
    }
  },
  beforeDestroy() {
    this.editor.destroy()
  },
}
</script>
