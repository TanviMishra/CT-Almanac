<%*
const allFiles = app.vault.getMarkdownFiles();
const currentFileContent = await app.vault.read(app.workspace.getActiveFile());
checkNamesInFile(currentFileContent, allFiles)

function checkNamesInFile(text, array) {
text = text.toLowerCase(); 
for (let i = 0; i < array.length; i++) { 
	const name = array[i].basename.toLowerCase(); 
	const regex = new RegExp("\\b" + name.replace(/[.*+?^${}()|[\]\\]/g, '\\$&') + "\\b", "gi");
	//console.log(name,text);
	if (regex.test(text)) 
		{ 
			console.log(array[i].basename)
			//return true; 
		} 
	} 
	//return false; 
}
%> 