# Front End Design

We decided to use ReactJS for the from end.
ReactJS coupled with the ES6 Javasecript extended language provide a powerful component-driven platform that can fit the needs of our design.
We wanted our design to be scalable, dynamic and cross-platform.
Using React's stateful and component driven Module means that each feature is contained in it's our descriptive class that can be added, removed and modified easily without affecting the functionality of the other components.
For example, we are able to develop button components and add them to our navigation bar component with ease. Eeach button can be imported without affecting the functionality of other buttons since its functionality is contained within its class which makes it easy to maintain and upgrade.
React is also very dynamic in the sense that it utilizes a virtual DOM to render the HTML document while allowing for tremendous control and easy of development. Since each compnent has it's own rendering function, descriping and adding new features requires very minimal modifications to the containners and sections of the page. More importantly, since the UI is state-drive, each component is able to cause a chain of events that ripples within the user interface, updating the necessary parts with easy.
On top of all that, react is compatible with all major browsers known to day. Although the program is required to run on a unix system that supports NodeJS and the other react dependncies, the UI can be accessed through the web from any device without the need for us to make special accomidations.
In addition, since ReactJS works on top of NodeJS, we are able to utilize react's features and also NodeJS's wealth of web-based server-side libraries.

Our pipeline is very simple, ReactJS is served through NodeJS to the user's browser. ReactJS is then able to control NodeJS through sending HTTP or XHR requests, which allows it to issue a command to run our python program and execute our algorithim on the user's data. It is then able to pull back the data, allowing users to modify it and export it.

Front-End Design:
The UI is composed of three parts, each part is represented with a component and has its own child components:
- Header
- Navigation Bar
- Team Viewer

Header:
A simple static title compoenets, takes a title property and displays it nicely

Navigation Bar:
Tool bar to allow the users to process the phases of the program. Contains:
- Import Button Component:
	A button with import functionality. Allows the user to select a file, the uses the FineUploader library to upload the file to the server (storage/input.csv). Then notifies the state handler of the import. Once the upload is completed, the Node server notifies the UI which then requests the data from the server and parses it and stores it in the _team_data Object.
- Process Button Component:
	A button which directs the NodeJS server to run the python program on the imported file. The python program generates a file (storage/output.csv) with three additional columns indicating the algorithim's recommendations. The button then listens for an http response indicating the success/failure of the operation. once the opreation is successful, it requests data from output.csv and stores it in the _team_data Object.
- Finish Button Componenet:
	A component which prepares an export button out of the current data in _team_data Object.
- Export Button Component:
	The button is a download link to a CSV file containing the current _team_data Object information. It is the same file as the CSV generated by the google surveys with additional columns indicating team assignments

Team Viewer:
The team viewer displays the information in the _team_data Object. It allows the user to modify the data reflecting real changes on the data in the object.
The team viewer contains:
- Team List component:
 Multiple instances of this comonents are present on the Team Viewer container. Each of them represents a team formation. Eeach team formation contains multiple instances of a Team Member component.
- Team Memeber Component:
 An object which is rendered as a row in the table. Can be dragged to other Team Lists. The change is directly reflected in the _team_data Object. It can be seen in the final exported CSV file.
