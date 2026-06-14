> [!metadata|nmg ttl-s txt-s txt-c embed collaps no-t clear wfull c-p-sm]
> ```dataview
> TASK 
> FROM -"~Templates"
> GROUP BY (file.folder + "/" + file.link)
> ```