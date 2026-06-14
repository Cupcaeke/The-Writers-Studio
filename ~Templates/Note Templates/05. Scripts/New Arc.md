<%* let arcNum = await tp.system.prompt("Enter Arc Number: (Ex. \"03\")") + ". " -%>
<%* let arcName = await tp.system.prompt("Enter Arc Name: (Ex. \"Finders Keepers\")") -%>
<%* let arcPath = tp.file.folder(true) + "/" + arcNum + arcName %>
<%* await tp.file.create_new(tp.file.find_tfile("~Templates/Note Templates/00. Plotting Templates/Arc Overview Template"), arcNum + arcName + " Overview", true, arcPath) %>