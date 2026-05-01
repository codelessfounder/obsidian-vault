---

---

Docker is like a shipping container for your apps. 

There are 3 main components:

1. Images: This is the software for your app. When you update the app, you are just downloading a newer version of this blueprint.
2. Containers: This is the instance. You can start, stop and delete these whenever you want 
3. Volumes: This is your data storage for your app. You can plug volumes into new containers as you please, but these are permanent and should not be deleted. 


Core workflow in Docker:

4. Build (the dockerfile): You write a text file (recipe) that says: "Start with Linux, install Node.js, and copy my code inside.”
5. Ship (the image): you turn that recipe into a *blueprint (*hence the name “image”). This is a static file that contains everything your app needs to run. You cannot change an image once its built. 
6. Run (the container): you take the *image *you created and “start it”. This creates *a container - *a living process on your computer. 

### **Cheat Sheet: Essential Commands:**

- **ActionCommandCheck status**`docker ps` (Shows what's running right now)
- **See errors**`docker logs -f n8n_recovered` (The "-f" follows the logs in real-time)
- **Stop n8n**`docker stop n8n_recovered`
- **Update n8n**`docker pull n8nio/n8n:latest` (Downloads the newest blueprint)
- **Cleanup**`docker system prune` (Deletes old images you aren't using anymore)


### Port mapping:

- you must map a port on your mac into the container so your computer can talk to the container’s contents 
- done through “-p”
- This is how [localhost](http://localhost/) works 


### Docker composer:

- run multiple containers at once 
- Add a postgres database to your setup 
- Set up a config file YAML instead of typing multiple commands. e.g:

“””services:
n8n:
image: n8nio/n8n:latest
container_name: n8n_worker
restart: always
ports:
- "5678:5678"
volumes:
- n8ndata:/home/node/.n8n

volumes:
n8ndata:
external: true”””



