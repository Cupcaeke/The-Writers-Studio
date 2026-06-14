 <%*
// Project Name & Path
let projName = await tp.system.prompt("Enter Project Name: (Avoid using \', \\, \", \;, etc)");

// Create Project Masterboard
await tp.file.create_new(tp.file.find_tfile("~Templates/Note Templates/04. Misc/! Project Masterboard Template"), projName + " Masterboard", false, projName);

// Create Plotting/Arcs/Arcs Dashboard.md
await tp.file.create_new(tp.file.find_tfile("~Templates/Note Templates/00. Plotting Templates/! Arcs Dashboard Template"), "Arcs Dashboard", false, projName + "/Plotting/Arcs");

// Create Plotting/Timelines/Timelines Dashboard.md
await tp.file.create_new(tp.file.find_tfile("~Templates/Note Templates/03. Timeline Templates/! Timelines Dashboard Template"), "Timelines Dashboard", false, projName + "/Plotting/Timelines");

// Create Wiki/Characters/Characters Dashboard.md
await tp.file.create_new(tp.file.find_tfile("~Templates/Note Templates/01. Character Templates/! Characters Dashboard Template"), "Characters Dashboard", false, projName + "/Wiki/Characters");

// Create Wiki/Factions/Factions Dashboard.md
await tp.file.create_new(tp.file.find_tfile("~Templates/Note Templates/02. World Templates/! Factions Dashboard Template"), "Factions Dashboard", false, projName + "/Wiki/Factions");

// Create Wiki/Items and Artifacts/Items and Artifacts Dashboard.md
await tp.file.create_new(tp.file.find_tfile("~Templates/Note Templates/04. Misc/! Items and Artifacts Dashboard Template"), "Items and Artifacts Dashboard", false, projName + "/Wiki/Items and Artifacts");

// Create Wiki/Magic Systems/Magic Systems Dashboard.md
await tp.file.create_new(tp.file.find_tfile("~Templates/Note Templates/04. Misc/! Magic Systems Dashboard Template"), "Magic Systems Dashboard", false, projName + "/Wiki/Magic Systems");

// Create Wiki/Regions/Regions Dashboard.md
await tp.file.create_new(tp.file.find_tfile("~Templates/Note Templates/02. World Templates/! Regions Dashboard Template"), "Regions Dashboard", false, projName + "/Wiki/Regions");
%>