# Google Maps Memory Leak Demo

To see the issue:

- Clone the repo
- Run `npm install`
- Run `npm run dev`
- In `MapPage.vue`, replace the `api-key` and `mapId` with your own key and map ID.
- Go to the page in your browser
- In Chrome Dev Tools "Performance" tab, start recording
- Every 2-3 seconds, toggle the map by clicking the button. 
- Stop the recording

You will see that JS Heap, Nodes and Listeners all increase, and never decrease (garbage collected).

You can also profile the memory to see a more detailed view of allocations.

- Open the "Memory" tab in Chrome Dev Tools
- Select "Allocations on timeline" and check the "Allocation stack traces" checkbox
- Start recording
- Toggle the map at 2-3 second intervals
- Stop recording
- In the "filter by class" search box, filter by the word "map"

Now, if you drag the timeline slider, you'll notice that the number of allocations for various Google Maps objects are going up, and they never go back down.



