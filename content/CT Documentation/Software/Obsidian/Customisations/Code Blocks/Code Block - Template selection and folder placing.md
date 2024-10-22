---
tags:
  - code-block
---
<%*
 //FINDING ALL TEMPLATES
 const templateFolder = "Obsidian Templates/Templates";  
 const allFiles = app.vault.getMarkdownFiles();
 let fileInFolder = new Array();
 allFiles.forEach((file) => {
	if (file.path.includes(templateFolder)) {
		fileInFolder.push({ name: file.basename, path: file.path });
	};
});

//USER INPUT
//SELECT TEMPLATE
let selectedTemplateType = await tp.system.suggester(fileInFolder.map((item) => item.name), fileInFolder.map((item) => item.name));
if(!selectedTemplateType){
	console.log("no selected template");
	selectedTemplateType="Default Template";
}
//SELECT PATH
let selectedFilePath = await tp.system.prompt("Note Path (format as /folder/subfolder/)");
if(!selectedFilePath){
	console.log("no selected path");
	if(selectedTemplateType=="Gotchas Template"){
		selectedFilePath="/Gotchas/"
	}
	if(selectedTemplateType=="How Tos Template"){
		selectedFilePath="/How Tos/"
	}
	if(selectedTemplateType=="Code Blocks Template"){
		selectedFilePath="/Obsidian Templates/Code Blocks/"
	}
	if(selectedTemplateType=="Default Template"){
		selectedFilePath="/Unsorted/"
	}
}
//SELECT NAME
let selectedFileName = await tp.system.prompt("Note Title");
if(!selectedFileName){
	console.log("no selected name");
	selectedFileName = generateRandomString(5);
}
//CONTENT FORMATTING
const selectedTemplatePath = tp.file.find_tfile(selectedTemplateType+".md");
const selectedTemplateContent = await app.vault.read(selectedTemplatePath);

//CURRENT FILE
const currentFile = app.workspace.getActiveFile(); 

//CHANGES
await tp.file.rename(selectedFileName)
console.log(selectedFilePath, selectedFileName)
await tp.file.move(selectedFilePath + selectedFileName);
app.vault.modify(currentFile, selectedTemplateContent);

//RANDOM STRING
function generateRandomString(length) {
  const charset = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
  let randomString = "";

  for (let i = 0; i < length; i++) {
    const randomIndex = Math.floor(Math.random() * charset.length);
    randomString += charset.charAt(randomIndex);
  }

  return randomString;
}
-%>