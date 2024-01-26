So first I had added a number of console logs and stepped though the code in order to see where there were some issues

1. there was a function in home named "saveMessage" that i had to change due to that fact that it was just returning a promise so I had it resolve so the next function "addMessageToConversation" would be able to parse thourgh the object it was expecting..
2. I would manipulate the array order when it was displaying due to being reversed from what it should be... additionally when adding I would use unshift to add to the end (one thing I would think about though is that I should push as it was before then reverse the order... that might have been cleaner...)
