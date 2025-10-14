### **🔹 Pull Your First Docker Image & Run Your First Docker Container**

---

#### **1. Pull Your First Docker Image** 🐳🔽

The first thing you need to do is **pull an image** from Docker Hub. In this case, we’ll use the official **Nginx** image.

```bash
docker pull nginx
```

This will download the **Nginx** image to your local machine.

---

#### **2. Verify the Image is Downloaded** 📸

Once the image is pulled, check if the image has been downloaded by running:

```bash
docker images
```

This will display all Docker images you have on your system. You should see **Nginx** listed among them.

Example output:

```bash
REPOSITORY          TAG       IMAGE ID       CREATED         SIZE
nginx               latest    abc12345abc9    2 weeks ago     133MB
```

---

#### **3. Run Your First Docker Container** 🚀

Next, let’s run your first container using the Nginx image. Run the following command:

```bash
docker run -dt -p 8080:80 --name my_nginx_container nginx
```

Explanation:

* **`-dt`**: Runs the container in **detached mode** (background).
* **`-p 8080:80`**: Maps **port 8080** on your host machine to **port 80** inside the container.
* **`--name my_nginx_container`**: Assigns a custom **name** to your container for easy reference.

After running this command, your Nginx container will be up and running!

---

#### **4. Check Running Containers** 📊

To verify the container is running, use the following command:

```bash
docker container ps
```

This will list all **currently running containers**.

Example output:

```bash
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                  NAMES
abc12345abcd   nginx     "/docker-entrypoint.…"   1 minute ago    Up 1 minute    0.0.0.0:8080->80/tcp   my_nginx_container
```

* **PORTS**: The `0.0.0.0:8080->80/tcp` means you can access the Nginx server via `http://localhost:8080`.

---

#### **5. Verify the Nginx Server is Running** 🌍

To check if your Nginx container is working, open a browser and visit:

```
http://localhost:8080
```

If the container is running correctly, you’ll see the default **Nginx Welcome Page**. 🎉

---

#### **6. Check the Container’s Network Interface** 🌐

If you want to view the network interfaces of your container (such as `docker0`), you can run:

```bash
ifconfig
```

Look for the **docker0** interface. This shows the **internal IP** of your Docker container.

---

#### **7. Stop the Container** 🛑

To stop your container gracefully, run:

```bash
docker container stop my_nginx_container
```

This will stop the container from running.

---

#### **8. Verify the Stopped Container** 🧐

You can check the status of your stopped container by running:

```bash
docker container ps -a
```

This will show all containers (including stopped ones).

Example output:

```bash
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS                     PORTS                  NAMES
abc12345abcd   nginx     "/docker-entrypoint.…"   1 minute ago    Exited (0) 2 minutes ago     0.0.0.0:8080->80/tcp   my_nginx_container
```

* **`Exited (0)`**: Indicates the container stopped without errors.

---

#### **9. Clean Up the Container (Optional)** 🧹

If you’re done and want to **remove** the container, use:

```bash
docker container rm my_nginx_container
```

To also remove the **image**, you can run:

```bash
docker rmi nginx
```

---

### **📝 Basic Docker Commands Summary**

Here’s a quick reference table with all the Docker commands you’ve used so far:

| **Command**                         | **Explanation**                                               |
| ----------------------------------- | ------------------------------------------------------------- |
| `docker pull <image>`               | Pull an image from Docker Hub (e.g., `docker pull nginx`).    |
| `docker images`                     | View the list of all Docker images on your system.            |
| `docker run <options> <image>`      | Run a container from an image (e.g., `docker run -dt nginx`). |
| `docker container ps`               | List all running containers.                                  |
| `docker container ps -a`            | List all containers (running and stopped).                    |
| `docker container stop <container>` | Stop a running container.                                     |
| `docker container rm <container>`   | Remove a stopped container.                                   |
| `docker rmi <image>`                | Remove a Docker image from your system.                       |

---

### **🔚 Wrap Up**

You’ve just pulled your first Docker image (Nginx), created your first Docker container, and explored some basic Docker commands to manage it. 🎉

* **Next steps**: You can explore adding custom content to your Nginx container, adjusting configurations, or deploying more complex Docker setups.
