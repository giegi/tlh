# tlh
tlh stands for Traffic Light Handler. 
You might never need this tool in your whole programmer life. Most of the web developers won't have the need to use a library download manager to handle which library to load first, and which libraries need to be waited before downloading another one. Many developers won't need to wait data from three, four, five other javascript sources.
But if you might need to do this, tlh is right for you.
TLH is a js/css library download handler for complex javascript ecosystems. 

Let's draw a scenario.
An analytics system, in order to work properly, needs to have available a serie of objects and informations in page. These objects have different sources. A javascript library, the result of an asynchronous ajax call, the acceptance of the Gdpr Infoprivacy, the analytics sdk, its initialization.
Putting in order the script tags in the head tag is not enough to be sure that everything will work in the correct sequence.
TLH does this for you. 
Let's see a pratical example.
