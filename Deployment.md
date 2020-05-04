This page contains information about deployment-related considerations. 

## Important Notes

* When deploying the application, review the custom application vars at the bottom of the `settings.py` file. [Link to code.](https://github.com/mkornyev/ReEntry412/blob/master/ReEntryApp/settings.py#L139-L183)

* The instance was set up using the following DO tutorial: [link.](https://www.digitalocean.com/community/tutorials/how-to-set-up-django-with-postgres-nginx-and-gunicorn-on-ubuntu-16-04)

* __Environment variables__ are stored in a `.env` file on the Digital Ocean instance. They are fetched [here in `settings.py`.](https://github.com/mkornyev/ReEntry412/blob/master/ReEntryApp/settings.py#L16-L17)

* CRITICAL FIX: When changing the domain name of the application, make sure to update hard-coded notification link paths. See the [github issue.](https://github.com/mkornyev/ReEntry412/issues/35) 