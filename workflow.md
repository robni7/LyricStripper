<b>Filter Finder Items</b>  
file extension is lrc  
file extension is txt  
  
<b>Open Finder Items</b>  
open with textedit.app

<b>Run Applescript</b>  
````
on run {input, parameters}
	delay 1 --wait for all windows to be opened
	tell application "TextEdit"
		
		-- set originalFileName[n] to the name of the file
		tell text of document of every window
			
			repeat with P from (count of paragraphs) to 1 by -1
				if character 1 of paragraph P contains "[" then --only run the stripping when it has not already been stripped
					delete (characters 1 through 10) of paragraph P
				end if
			end repeat
			
		end tell
		delay 1 --wait for all text to be stripped
		save every document --as originalFileName[n].txt
		--close every window --close the windows after the deed is done (v1.3b: now disabled)
	end tell
	
end run
````
