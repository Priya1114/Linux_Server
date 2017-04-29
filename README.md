# Linux_Server

Accessed the web app with the following credentials:

    IP address: http://35.167.27.204
    SSH port: 2200
    User: grader

Get your server.

1. Start a new Ubuntu Linux server instance on Amazon Lightsail. There are full details on setting up your Lightsail instance on the next page.
2. Follow the instructions provided to SSH into your server.
Secure your server.

3. Update all currently installed packages.
4. Change the SSH port from 22 to 2200. Make sure to configure the Lightsail firewall to allow it.
5. Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123).
6. Create a new user account named grader.
7. Give grader the permission to sudo.
8. Create an SSH key pair for grader using the ssh-keygen tool.
Prepare to deploy your project.

9. Configure the local timezone to UTC.
10. Install and configure Apache to serve a Python mod_wsgi application.
11. Install and configure PostgreSQL:

    Do not allow remote connections
    Create a new database user named catalog that has limited permissions to your catalog application database.

12. Install git.
Deploy the Item Catalog project.

13. Clone and setup your Item Catalog project from the Github repository you created earlier in this Nanodegree program.
14. Set it up in your server so that it functions correctly when visiting your server’s IP address in a browser. Make sure that your .git directory is not publicly accessible via a browser!


