<%*
const dv = app.plugins.plugins["dataview"].api;
const openPublishPanel = app.commands.commands["publish:view-changes"].callback;

// Add as many filenames and queries as you'd like!
const fileAndQuery = new Map([
  [
    "../Navigation/Recent/Recently edited",
    'TABLE WITHOUT ID file.link AS Note, dateformat(file.mtime, "ff") AS Modified FROM "Published" WHERE publish SORT file.mtime desc LIMIT 7',
  ],
  [
    "../Navigation/Recent/Recent new files",
    'TABLE WITHOUT ID file.link AS Note, dateformat(file.ctime, "DD") AS Added FROM "Published" WHERE publish SORT file.ctime desc LIMIT 7',
  ],
  [
    "../Navigation/Links/C++",
	`
	TABLE WITHOUT ID
		file.frontmatter.emoji + " - " + link(file.frontmatter.link, file.name) as Name, 
		author AS "Author" 
	FROM "Published/__meta/Links" 
	WHERE "Name" 
	SORT file.name
	`
  ],
]);

await fileAndQuery.forEach(async (query, filename) => {
  if (!tp.file.find_tfile(filename)) {
    await tp.file.create_new("", filename);
    new Notice(`Created ${filename}.`);
  }
  const tFile = tp.file.find_tfile(filename);
  const queryOutput = await dv.queryMarkdown(query);
  const fileContent = `---\npublish: true\n---\n%% update via "Update Publish Files" template %% \n\n${queryOutput.value}`;
  try {
    await app.vault.modify(tFile, fileContent);
    new Notice(`Updated ${tFile.basename}.`);
  } catch (error) {
    new Notice("⚠️ ERROR updating! Check console. Skipped file: " + filename , 0);
  }
});
//openPublishPanel();
%>