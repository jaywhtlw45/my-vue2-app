<template>
    <container class="conatiner">
        <header class="header">
            <h1>Vue 2 Smart Clipboard handler</h1>
            <h2>Try pasting text or images using <strong>Ctrl + V</strong></h2>
        </header>

        <body class="body">
            <textarea ref="emailTextarea" class="emailInput" @focus="focusTextBox" @blur="unfocusTextBox"
                autocomplete="off" @keydown="handleKeydown"></textarea>

            <div v-if="isSelected">Text Box Selected</div>
        </body>
        <footer class="footer">
            <div class="fileAttachmentText">
                Attached Files:
            </div>
            <ul>
                <li v-for="(file, index) in attachedFiles" :key="index">
                    {{ file.types }}
                </li>
            </ul>



        </footer>
    </container>
</template>

<script>
export default {
    name: 'EmailBox',
    data() {
        return {
            attachedFiles: [],
            isSelected: false,
        }
    },
    methods: {
        handleKeydown(event) {
            if (event.ctrlKey && event.key == 'v') {
                event.preventDefault();
                this.customPasteFunction();
            }
        },
        async customPasteFunction() {
            const clipboardItems = await navigator.clipboard.read();

            for (const item of clipboardItems) {
                if (item.types.includes('image/png') ||
                    item.types.includes('image/jpeg') ||
                    item.types.includes('imnage/gif'))
                    await this.handleImagePaste(item);
                return;

            }
            const clipboardData = await navigator.clipboard.readText();
            this.insertTextAtCursor(clipboardData);
        },
        async handleImagePaste(item) {
            console.log(item);
            this.attachedFiles.push(item);
            return;
        },
        focusTextBox() {
            this.isSelected = true;
        },
        unfocusTextBox() {
            this.isSelected = false;
        }
    },
    watch: {
        attachedFiles {

}
    }
}
</script>


<style>
.container {
    max-width: 500px;
    min-width: 200px;
}

ul {
    list-style: none;
}

.emailInput {
    width: 500px;
    height: 300px;
    padding: 12px;
    border: 2px solid #ccc;
    border-radius: 8px;
}

.fileAttachmentText {}
</style>