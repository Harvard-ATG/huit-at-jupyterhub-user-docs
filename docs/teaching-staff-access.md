# Teaching Staff Access to JupyterHub

Instructors and TAs/TFs have access to admin tools in JupyterHub to help students with their environments. The Admin interface can be accessed from the JupyterHub homepage, visible when JupyterHub is first launched from Canvas. If a member of course staff has already started their server and entered a JupyterLab environment, they can get back to the JupyterHub homepage through File -> Hub Control Panel at the top of the page.

## JupyterHub Usernames

In the Admin panel, you will see a list of student servers. The usernames in JupyterHub come from unique user IDs in Canvas, which are distinct from other identifiers like HUIDs or netIDs. Any user in JupyterHub can see their user ID in the top right corner of the JupyterHub interface. 

To find the Canvas user ID for a student outside of JupyterHub, find them in the list of people on the Canvas "People" page and click on their name you should be taken to a profile page for the student. If a sidebar pops up on the right, click the student's name in the sidebar to get to this profile page. The number at the end of the url for this page is the student's Canvas ID, which is also their username in JupyterHub. That url will look similar to this: `https://canvas.harvard.edu/courses/<course_id>/users/<user_id>`. If you use Safari, you may have to click in to the URL bar to see the full url of the page.

!!!warning
    **Do not change JupyterHub usernames**

Admins have permission to change usernames in the admin dashboard, but doing so will break access for that user. The numeric user names are used in the authentication process, so changing them will result in a new user being created and permissions errors server-side when launching Jupyterhub, preventing the launch from completing successfully.

## Managing Student Servers

Once you have identified the student whose server you want to troubleshoot, you can access their server with the "Access Server" button in the row with their username. This will give you access to their running server, where you can directly view their files and notebooks and interact with their environment.

You can also stop their server if it is not responding and they are having difficulty stopping it themselves. They will be able to launch a fresh server once their server has stopped.

## Managing the Hub

The "Start All", "Stop All", and "Shutdown Hub" buttons should not be used by course staff. These will affect the entire JupyterHub setup for the course, and may have effects that course staff will be unable to undo. If there is an issue affectign the entire course setup, please reach out to [atg@fas.harvard.edu](mailto:atg@fas.harvard.edu) so that we can address the issue. If an issue is affecting an entire course, there is likely a problem with a system that course staff do not have access to, and developers within Academic Technology will need to diagnose and address the issue.
