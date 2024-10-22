---
tags:
  - database
  - code-block
---
note: if a file is renamed or moved, change the hotkeys in settings [[Setting Templater Hotkeys]].

| Code Block                                                 | Function                                                                                                                                                                                                                                 | Application | More                                                                                    |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | --------------------------------------------------------------------------------------- |
| [[Code Block - Template selection and folder placing]]     | Lets user choose one of the templates in "/Obsidion Templates/Templates/" and place it in a folder.<br>If the user does not input a folder path, the file is placed in a manually pre-determined folder (e.g., Rockwell Lab / Gotchas/). | opt + m     | if a template is added, change the code to ensure it has a default folder to sit within |
| [[Code Block - Searching file to find pre-existing links]] | Lets user check if their file have any other links or tags mentioned in their file                                                                                                                                                       | opt + s     |                                                                                         |
### Archive
<%*
const listFileName = "Creative Technoligists.md"; //list file 
const templateFileName = "Names Template.md" //template file


// Find the file
const listFile = tp.file.find_tfile(listFileName);
const templateFile = tp.file.find_tfile(templateFileName);
if (listFile && templateFile) {
    // Read the content
    const contentMD = await app.vault.read(listFile);
    const templateContent = await app.vault.read(templateFile);
    
    const contentArray = contentMD.split("\n").map(contentMD => contentMD.trim()).filter(contentMD => contentMD.length > 0);
    let newContent =""

	const regex = /\{\{\{(.*?)\}\}\}/g; 
	const regex2 = /\{\{\{(.*?),(.*?)\}\}\}/g;
	//newArray= contentArray.map(item => { const match = item.match(regex); return match ? match.map(m => m.slice(3, -3)) : null; }).filter(result => result !== null);
	let createPagesArray = []; 
	let match; 
	while ((match = regex.exec(contentMD)) !== null) { const splitMatch = match[1].split(',').map(item => item.trim()); createPagesArray.push(splitMatch); } 
	console.log(createPagesArray);
    for (let obj of createPagesArray) {
            const filename = `${obj[0].replace(/\[\[(.*?)\]\]/g, '$1')}`; // Create a filename
            const targetFolder = `${obj[1]}`; // target folder
            const filePath = `${targetFolder}/${filename}`; // path to new file
            await tp.file.create_new(templateContent, filePath, false); // create the new file 
    }
    const newcontentMD = contentMD.replace(regex2, (match, p1) => `[[${p1.trim()}]]`);
    await app.vault.modify(listFile, newcontentMD)
} else {
    console.error(`Content list file "${listFileName}" not found.`);
}
%>

 <%*
 let qcFilePath = await tp.system.prompt("Note Path (format as /folder/subfolder/)")
 //let templateType = await tp.system.suggester(["Default Template","Gotchas Template"],["Default Template","Gotchas Template"]);
 
 let templateFolder = "Obsidian Templates/Templates"; 
 //let templateFiles = await tp.file.findFiles(templateFolder); 
 const files = app.vault.getMarkdownFiles();
 const filesInFolder = new Array();
 files.forEach((file) => {
	if (file.path.includes(templateFolder)) {
		filesInFolder.push(file.basename)
	};
 })
 let templateType = await tp.system.suggester(filesInFolder, filesInFolder);
 await tp.file.move(qcFilePath + tp.file.title);
 -%>