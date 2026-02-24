# Docker

## 𝙒𝙝𝙖𝙩 𝙞𝙨 𝘿𝙤𝙘𝙠𝙚𝙧?

𝐃𝐨𝐜𝐤𝐞𝐫 is a containerization platform that allows developers to package their applications into a single container that includes everything the application needs to run, including the application code, libraries, and dependencies. Docker provides an easy way to create, deploy, and run applications in a portable and isolated environment, making it easier to ensure consistency between development and production environments.


## 𝙃𝙤𝙬 𝘿𝙤𝙘𝙠𝙚𝙧 𝙒𝙤𝙧𝙠?

𝟭. 𝗗𝗲𝘃𝗲𝗹𝗼𝗽: Write your application code and create a Dockerfile with build instructions.

𝟮. 𝗕𝘂𝗶𝗹𝗱 𝗜𝗺𝗮𝗴𝗲:

𝚍𝚘𝚌𝚔𝚎𝚛 𝚋𝚞𝚒𝚕𝚍 -𝚝 𝚖𝚢𝚊𝚙𝚙:𝚕𝚊𝚝𝚎𝚜𝚝 .

This command builds an image named myapp from the Dockerfile in the current directory.

𝟯. 𝗥𝘂𝗻 𝗖𝗼𝗻𝘁𝗮𝗶𝗻𝗲𝗿𝘀:

𝚍𝚘𝚌𝚔𝚎𝚛 𝚌𝚘𝚗𝚝𝚊𝚒𝚗𝚎𝚛 𝚛𝚞𝚗 -𝚍 -𝚙 𝟾𝟶𝟾𝟶:𝟾𝟶 𝚖𝚢𝚊𝚙𝚙:𝚕𝚊𝚝𝚎𝚜𝚝

This starts a container from the myapp:latest image, mapping port 8080 on your host to port 80 in the container.

𝟰. 𝗠𝗮𝗻𝗮𝗴𝗲:

𝚍𝚘𝚌𝚔𝚎𝚛 𝚙𝚜             # 𝚅𝚒𝚎𝚠 𝚛𝚞𝚗𝚗𝚒𝚗𝚐 𝚌𝚘𝚗𝚝𝚊𝚒𝚗𝚎𝚛𝚜
𝚍𝚘𝚌𝚔𝚎𝚛 𝚙𝚜 -𝚊          # 𝙻𝚒𝚜𝚝 𝚊𝚕𝚕 𝚌𝚘𝚗𝚝𝚊𝚒𝚗𝚎𝚛𝚜 (𝚛𝚞𝚗𝚗𝚒𝚗𝚐 𝚊𝚗𝚍 𝚜𝚝𝚘𝚙𝚙𝚎𝚍)
𝚍𝚘𝚌𝚔𝚎𝚛 𝚜𝚝𝚘𝚙 <𝚌𝚘𝚗𝚝𝚊𝚒𝚗𝚎𝚛_𝚒𝚍>   # 𝚂𝚝𝚘𝚙 𝚊 𝚛𝚞𝚗𝚗𝚒𝚗𝚐 𝚌𝚘𝚗𝚝𝚊𝚒𝚗𝚎𝚛
𝚍𝚘𝚌𝚔𝚎𝚛 𝚜𝚝𝚊𝚛𝚝 <𝚌𝚘𝚗𝚝𝚊𝚒𝚗𝚎𝚛_𝚒𝚍>  # 𝚂𝚝𝚊𝚛𝚝 𝚊 𝚜𝚝𝚘𝚙𝚙𝚎𝚍 𝚌𝚘𝚗𝚝𝚊𝚒𝚗𝚎𝚛
𝚍𝚘𝚌𝚔𝚎𝚛 𝚛𝚖 <𝚌𝚘𝚗𝚝𝚊𝚒𝚗𝚎𝚛_𝚒𝚍>     # 𝚁𝚎𝚖𝚘𝚟𝚎 𝚊 𝚌𝚘𝚗𝚝𝚊𝚒𝚗𝚎𝚛

𝟱. 𝗖𝗼𝗺𝗽𝗼𝘀𝗲: Use Docker Compose to manage multi-container apps.

𝟲. 𝗣𝘂𝗯𝗹𝗶𝘀𝗵:

𝚍𝚘𝚌𝚔𝚎𝚛 𝚙𝚞𝚜𝚑 𝚖𝚢𝚛𝚎𝚐𝚒𝚜𝚝𝚛𝚢/𝚖𝚢𝚊𝚙𝚙:𝚕𝚊𝚝𝚎𝚜𝚝

Push your image to a registry like Docker Hub.

𝟳. 𝗨𝗽𝗱𝗮𝘁𝗲: Modify the Dockerfile, rebuild the image, and distribute new versions.

-------------------------------------------------------------------------------

## 𝘾𝙝𝙤𝙤𝙨𝙚 𝘿𝙤𝙘𝙠𝙚𝙧 𝙬𝙝𝙚𝙣:

✅ You want to containerize an application or service for easier deployment and isolation.
✅ You want to ensure that the application runs the same way in different environments, including development, testing, and production.
✅ You want to package an application and its dependencies in a portable, self-contained format.
✅ You want to run a single container on a single host without the need for orchestration.

## Docker 

Docker has become a ubiquitous tool in the world of software development and deployment due to its numerous benefits and ease of use. Here are some scenarios in which Docker is commonly used:
1. **Containerization of Applications**: Docker is primarily used to containerize applications or services. This means encapsulating an application along with its dependencies into a Docker container. This container is a lightweight, standalone, and executable package that can run consistently across different environments. This is especially useful in cases where applications have complex dependencies or where consistency between development and production environments is crucial.

2. **Consistency Across Environments**: Docker ensures that applications run consistently in various environments, including development, testing, and production. Developers can build and test their applications in a Docker container locally and then deploy the exact same container in a production environment. This minimizes "it works on my machine" issues and improves software reliability.

3. **Portability**: Docker containers are highly portable. You can create a Docker container on your local machine and run it on any host that supports Docker, regardless of the underlying operating system. This portability is advantageous for developers working on different platforms and for deploying applications in multi-cloud or hybrid cloud environments.

4. **Isolation**: Docker containers provide process isolation, which means that applications running in separate containers are isolated from each other. This isolation prevents conflicts between different applications and allows you to run multiple containers on the same host without interference.

5. **Single-Host Deployment**: Docker is suitable for scenarios where you want to run a single container on a single host without the need for complex orchestration tools like Kubernetes. It simplifies the process of deploying and managing individual containers.

6. **Development and Testing**: Docker is valuable during the development and testing phases of the software development lifecycle. Developers can create Docker containers that mimic the production environment, ensuring that their code behaves consistently from development through testing to production.

7. **Continuous Integration and Continuous Deployment (CI/CD)**: Docker is often used in CI/CD pipelines to build, test, and deploy applications automatically. Containers can be easily integrated into CI/CD workflows to ensure smooth and consistent application delivery.

8. **Microservices Architecture**: Docker is commonly used in microservices-based architectures where different components of an application are containerized. This allows for scalability, easy updates, and independent management of individual services.

9. **Scaling Applications**: Docker makes it easy to scale applications horizontally by creating multiple instances of containers to handle increased loads. Docker Swarm and Kubernetes are commonly used for container orchestration and scaling.

10. **Third-Party Software Distribution**: Some software vendors distribute their applications in Docker containers, making it easy for customers to deploy and manage their software.

In summary, Docker is a versatile tool that offers a range of benefits, including application containerization, consistency, portability, isolation, and ease of deployment. It is widely adopted across various industries and use cases to simplify software development and deployment processes.
## Videos

 * [100+ Docker Concepts you Need to Know](https://www.youtube.com/watch?v=rIrNIzy6U_g)
	> [<img src="https://img.youtube.com/vi/rIrNIzy6U_g/0.jpg" width="200">](https://www.youtube.com/watch?v=rIrNIzy6U_g "100+ Docker Concepts you Need to Know by Fireship 612,408 views 8 minutes, 28 seconds")
 * [Is it time to switch from Docker to Podman?](https://www.youtube.com/watch?v=7-qo6tTPdTM)
	> [<img src="https://img.youtube.com/vi/7-qo6tTPdTM/0.jpg" width="200">](https://www.youtube.com/watch?v=7-qo6tTPdTM "Is it time to switch from Docker to Podman? by Christian Lempa 195,833 views 16 minutes")
 * [Intro to Deploying WebLogic using Docker](https://www.youtube.com/watch?v=4EkvlyPVGRc)
	> [<img src="https://img.youtube.com/vi/4EkvlyPVGRc/0.jpg" width="200">](https://www.youtube.com/watch?v=4EkvlyPVGRc "Intro to Deploying WebLogic using Docker by Learn Oracle WebLogic Online 1,900 views 6 minutes, 23 seconds")
 * [Unbound in Docker with PiHole - Regain Your Privacy - Cybersecurity at Home](https://www.youtube.com/watch?v=Y3nm519xHfw)
	> [<img src="https://img.youtube.com/vi/Y3nm519xHfw/0.jpg" width="200">](https://www.youtube.com/watch?v=Y3nm519xHfw "Unbound in Docker with PiHole - Regain Your Privacy - Cybersecurity at Home by Jim&#39;s Garage 13,838 views 18 minutes")
 * [2-Docker-Django-PostgreSQL](https://www.youtube.com/watch?v=pQr54nYQi5k)
	> [<img src="https://img.youtube.com/vi/pQr54nYQi5k/0.jpg" width="200">](https://www.youtube.com/watch?v=pQr54nYQi5k "2-Docker-Django-PostgreSQL by Code Platoon 142 views 1 hour, 1 minute")
 * [Efficient Queue Management with Laravel, Redis, and Docker | Complete Guide](https://www.youtube.com/watch?v=puBOaV0tQbQ)
	> [<img src="https://img.youtube.com/vi/puBOaV0tQbQ/0.jpg" width="200">](https://www.youtube.com/watch?v=puBOaV0tQbQ "Efficient Queue Management with Laravel, Redis, and Docker | Complete Guide by Hanie Asemi  1,248 views 15 minutes")
 * [Using Containers without Docker Desktop](https://www.youtube.com/watch?v=i7i4vZBOpWM)
	> [<img src="https://img.youtube.com/vi/i7i4vZBOpWM/0.jpg" width="200">](https://www.youtube.com/watch?v=i7i4vZBOpWM "Using Containers without Docker Desktop by The Pragmatic Programmer 6,779 views 20 minutes")
 * [Docker Crash Course for Absolute Beginners [NEW]](https://www.youtube.com/watch?v=pg19Z8LL06w)
	> [<img src="https://img.youtube.com/vi/pg19Z8LL06w/0.jpg" width="200">](https://www.youtube.com/watch?v=pg19Z8LL06w "Docker Crash Course for Absolute Beginners [NEW] by TechWorld with Nana 1,270,495 views 1 hour, 7 minutes")
 * [How to deploy Web app in Wildfly Dockerfile Alpine](https://www.youtube.com/watch?v=OTECoH05nHU)
	> [<img src="https://img.youtube.com/vi/OTECoH05nHU/0.jpg" width="200">](https://www.youtube.com/watch?v=OTECoH05nHU "How to deploy Web app in Wildfly Dockerfile Alpine by Zariga Tongy 2,709 views 2 minutes, 30 seconds")
 * [PostgreSQL y Wildfly sobre Docker | Docker para programadores # 02](https://www.youtube.com/watch?v=l6IC84nc4VQ)
	> [<img src="https://img.youtube.com/vi/l6IC84nc4VQ/0.jpg" width="200">](https://www.youtube.com/watch?v=l6IC84nc4VQ "PostgreSQL y Wildfly sobre Docker | Docker para programadores # 02 by Julio Mejia 957 views 11 minutes, 31 seconds")
 * [Containerizing your Java EE Application using Docker](https://www.youtube.com/watch?v=_ePq5oeUl60)
	> [<img src="https://img.youtube.com/vi/_ePq5oeUl60/0.jpg" width="200">](https://www.youtube.com/watch?v=_ePq5oeUl60 "Containerizing your Java EE Application using Docker by Oracle Developers 12,792 views 4 minutes, 1 second")
	> [<img src="https://img.youtube.com/vi/orZ3OvEIMT0/0.jpg" width="200">](https://www.youtube.com/watch?v=orZ3OvEIMT0 "Java and JBoss in Containers. One .war File Per Container? by Bret Fisher Docker and DevOps 1,750 views 5 minutes, 56 seconds")
 * [Installing jboss wildfly as a docker container](https://www.youtube.com/watch?v=KgXpHXN2aLM)
	> [<img src="https://img.youtube.com/vi/KgXpHXN2aLM/0.jpg" width="200">](https://www.youtube.com/watch?v=KgXpHXN2aLM "Installing jboss wildfly as a docker container by CodeWis Technologies 8,713 views 4 minutes, 19 seconds")
 * [Docker с 0 до 100%. Всё, что нужно знать.](https://www.youtube.com/watch?v=O8N1lvkIjig)
	> [<img src="https://img.youtube.com/vi/O8N1lvkIjig/0.jpg" width="200">](https://www.youtube.com/watch?v=O8N1lvkIjig "Docker с 0 до 100%. Всё, что нужно знать. by RomNero 349,614 views 5 hours, 8 minutes")
 * [Dockge: The New Docker Manager You Need To See!](https://www.youtube.com/watch?v=E805XcbTzgY)
	> [<img src="https://img.youtube.com/vi/E805XcbTzgY/0.jpg" width="200">](https://www.youtube.com/watch?v=E805XcbTzgY "Dockge: The New Docker Manager You Need To See! by DB Tech 75,895 views 22 minutes")
 * [Docker 101 - Completely Hands-on](https://www.youtube.com/watch?v=8CiXiOjIXfk)
	> [<img src="https://img.youtube.com/vi/8CiXiOjIXfk/0.jpg" width="200">](https://www.youtube.com/watch?v=8CiXiOjIXfk "Docker 101 - Completely Hands-on by CloudYuga 4,269 views 1 hour, 11 minutes")

 * [Portainer e Traefik Proxy Reverso Docker Rodando Varios Containers no Mesmo Servidor](https://www.youtube.com/watch?v=E3phHnASkV4)
	> [<img src="https://img.youtube.com/vi/E3phHnASkV4/0.jpg" width="200">](https://www.youtube.com/watch?v=E3phHnASkV4 "Portainer e Traefik Proxy Reverso Docker Rodando Varios Containers no Mesmo Servidor by Fabricando Sua Ideia - Tutoriais 8,485 views 29 minutes")
 * [Chapter 102 || Demystifying Docker operations](https://www.youtube.com/watch?v=SmJvRgr2LMU)
	> [<img src="https://img.youtube.com/vi/SmJvRgr2LMU/0.jpg" width="200">](https://www.youtube.com/watch?v=SmJvRgr2LMU "Chapter 102 || Demystifying Docker operations by TechInsightInnovate 72 views 11 minutes, 23 seconds")
 * [Learning Docker // Getting started!](https://www.youtube.com/watch?v=Nm1tfmZDqo8)
	> [<img src="https://img.youtube.com/vi/Nm1tfmZDqo8/0.jpg" width="200">](https://www.youtube.com/watch?v=Nm1tfmZDqo8 "Learning Docker // Getting started! by Christian Lempa 91,781 views 35 minutes")
 * [DockerCon 2023 New Tools Announcement](https://www.youtube.com/watch?v=l1g5hoNx7yc)
	> [<img src="https://img.youtube.com/vi/l1g5hoNx7yc/0.jpg" width="200">](https://www.youtube.com/watch?v=l1g5hoNx7yc "DockerCon 2023 New Tools Announcement by Bret Fisher Docker and DevOps 4,384 views 16 minutes")
 * [DockerCon 2023 Announcements Live Show (Ep 237)](https://www.youtube.com/watch?v=NCwzV3J8Op0)
	> [<img src="https://img.youtube.com/vi/NCwzV3J8Op0/0.jpg" width="200">](https://www.youtube.com/watch?v=NCwzV3J8Op0 "DockerCon 2023 Announcements Live Show (Ep 237) by Bret Fisher Docker and DevOps 1,408 views 1 hour, 6 minutes")
 * [Docker networking is CRAZY!! (you NEED to learn it)](https://www.youtube.com/watch?v=bKFMS5C4CG0)
	> [<img src="https://img.youtube.com/vi/bKFMS5C4CG0/0.jpg" width="200">](https://www.youtube.com/watch?v=bKFMS5C4CG0 "Docker networking is CRAZY!! (you NEED to learn it) by NetworkChuck 1,538,833 views 39 minutes")
 * [What&#39;s New in Docker Build](https://www.youtube.com/watch?v=mgW61S7izcc)
	> [<img src="https://img.youtube.com/vi/mgW61S7izcc/0.jpg" width="200">](https://www.youtube.com/watch?v=mgW61S7izcc "What&#39;s New in Docker Build by Docker 1,777 views 27 minutes")
 * [Docker Crash Course for Absolute Beginners [NEW]](https://www.youtube.com/watch?v=pg19Z8LL06w)
	> [<img src="https://img.youtube.com/vi/pg19Z8LL06w/0.jpg" width="200">](https://www.youtube.com/watch?v=pg19Z8LL06w "Docker Crash Course for Absolute Beginners [NEW] by TechWorld with Nana 1,270,495 views 1 hour, 7 minutes")
 * [Docker Desktop for Windows 10/11 Setup and Tips](https://www.youtube.com/watch?v=rATNU0Fr8zs)
	> [<img src="https://img.youtube.com/vi/rATNU0Fr8zs/0.jpg" width="200">](https://www.youtube.com/watch?v=rATNU0Fr8zs "Docker Desktop for Windows 10/11 Setup and Tips by Bret Fisher Docker and DevOps 41,166 views 17 minutes")
 * [Docker Compose will BLOW your MIND!! (a tutorial)](https://www.youtube.com/watch?v=DM65_JyGxCo)
	> [<img src="https://img.youtube.com/vi/DM65_JyGxCo/0.jpg" width="200">](https://www.youtube.com/watch?v=DM65_JyGxCo "Docker Compose will BLOW your MIND!! (a tutorial) by NetworkChuck 583,032 views 16 minutes")
 * [you need to learn Docker RIGHT NOW!! // Docker Containers 101](https://www.youtube.com/watch?v=eGz9DS-aIeY)
	> [<img src="https://img.youtube.com/vi/eGz9DS-aIeY/0.jpg" width="200">](https://www.youtube.com/watch?v=eGz9DS-aIeY "you need to learn Docker RIGHT NOW!! // Docker Containers 101 by NetworkChuck 2,556,956 views 23 minutes")
 * [Docker Crash Course for Absolute Beginners [NEW]](https://www.youtube.com/watch?v=pg19Z8LL06w)
	> [<img src="https://img.youtube.com/vi/pg19Z8LL06w/0.jpg" width="200">](https://www.youtube.com/watch?v=pg19Z8LL06w "Docker Crash Course for Absolute Beginners [NEW] by TechWorld with Nana 1,270,495 views 1 hour, 7 minutes")
 * [Deploy war file on Tomcat Docker Container](https://www.youtube.com/watch?v=KCcrHMB3AAQ)
	> [<img src="https://img.youtube.com/vi/KCcrHMB3AAQ/0.jpg" width="200">](https://www.youtube.com/watch?v=KCcrHMB3AAQ "Deploy war file on Tomcat Docker Container by Hi-Tech Yuga 13,003 views 10 minutes, 49 seconds")
 * [Deploy java web application in Docker using Tomcat](https://www.youtube.com/watch?v=pGVCrOW8Ai4)
	> [<img src="https://img.youtube.com/vi/pGVCrOW8Ai4/0.jpg" width="200">](https://www.youtube.com/watch?v=pGVCrOW8Ai4 "Deploy java web application in Docker using Tomcat by Aveti Tutorials 10,500 views 5 minutes, 48 seconds")
 * [Docker Crash Course for Absolute Beginners [NEW]](https://www.youtube.com/watch?v=pg19Z8LL06w)
	> [<img src="https://img.youtube.com/vi/pg19Z8LL06w/0.jpg" width="200">](https://www.youtube.com/watch?v=pg19Z8LL06w "Docker Crash Course for Absolute Beginners [NEW] by TechWorld with Nana 1,270,495 views 1 hour, 7 minutes")
 * [MacOS Docker](https://www.youtube.com/watch?v=XWo2gnNbeGQ)
	> [<img src="https://img.youtube.com/vi/XWo2gnNbeGQ/0.jpg" width="200">](https://www.youtube.com/watch?v=XWo2gnNbeGQ "MacOS Docker by Chris Titus Tech 86,643 views 10 minutes, 54 seconds")
 * [Docker Desktop for Windows 10/11 Setup and Tips](https://www.youtube.com/watch?v=rATNU0Fr8zs)
	> [<img src="https://img.youtube.com/vi/rATNU0Fr8zs/0.jpg" width="200">](https://www.youtube.com/watch?v=rATNU0Fr8zs "Docker Desktop for Windows 10/11 Setup and Tips by Bret Fisher Docker and DevOps 41,166 views 17 minutes")
 * [Docker networking is CRAZY!! (you NEED to learn it)](https://www.youtube.com/watch?v=bKFMS5C4CG0)
	> [<img src="https://img.youtube.com/vi/bKFMS5C4CG0/0.jpg" width="200">](https://www.youtube.com/watch?v=bKFMS5C4CG0 "Docker networking is CRAZY!! (you NEED to learn it) by NetworkChuck 1,538,833 views 39 minutes")
 * [Docker Desktop for Windows 10/11 Setup and Tips](https://www.youtube.com/watch?v=rATNU0Fr8zs)
	> [<img src="https://img.youtube.com/vi/rATNU0Fr8zs/0.jpg" width="200">](https://www.youtube.com/watch?v=rATNU0Fr8zs "Docker Desktop for Windows 10/11 Setup and Tips by Bret Fisher Docker and DevOps 41,166 views 17 minutes")
 * [Docker networking is CRAZY!! (you NEED to learn it)](https://www.youtube.com/watch?v=bKFMS5C4CG0)
	> [<img src="https://img.youtube.com/vi/bKFMS5C4CG0/0.jpg" width="200">](https://www.youtube.com/watch?v=bKFMS5C4CG0 "Docker networking is CRAZY!! (you NEED to learn it) by NetworkChuck 1,538,833 views 39 minutes")
 * [What&#39;s New in Docker Build](https://www.youtube.com/watch?v=mgW61S7izcc)
	> [<img src="https://img.youtube.com/vi/mgW61S7izcc/0.jpg" width="200">](https://www.youtube.com/watch?v=mgW61S7izcc "What&#39;s New in Docker Build by Docker 1,777 views 27 minutes")
 * [DockerCon 2023 Announcements Live Show (Ep 237)](https://www.youtube.com/watch?v=NCwzV3J8Op0)
	> [<img src="https://img.youtube.com/vi/NCwzV3J8Op0/0.jpg" width="200">](https://www.youtube.com/watch?v=NCwzV3J8Op0 "DockerCon 2023 Announcements Live Show (Ep 237) by Bret Fisher Docker and DevOps 1,408 views 1 hour, 6 minutes")
 * [DockerCon 2021: Scott Johnston Keynote](https://www.youtube.com/watch?v=o9PuYHGljp8)
	> [<img src="https://img.youtube.com/vi/o9PuYHGljp8/0.jpg" width="200">](https://www.youtube.com/watch?v=o9PuYHGljp8 "DockerCon 2021: Scott Johnston Keynote by Docker 1,142 views 16 minutes")
 * [Hitler uses Docker](https://www.youtube.com/watch?v=PivpCKEiQOQ)
	> [<img src="https://img.youtube.com/vi/PivpCKEiQOQ/0.jpg" width="200">](https://www.youtube.com/watch?v=PivpCKEiQOQ "Hitler uses Docker by nukemtube 1,124,256 views 3 minutes, 50 seconds")
 * [Configurando um pipeline de uma aplicação docker no git](https://www.youtube.com/watch?v=68PYLqDIenk)
	> [<img src="https://img.youtube.com/vi/68PYLqDIenk/0.jpg" width="200">](https://www.youtube.com/watch?v=68PYLqDIenk "Configurando um pipeline de uma aplicação docker no git by Trilha Tecnológica 40 views 16 minutes")
 * [Virtual Machine (VM) vs Docker](https://www.youtube.com/watch?v=a1M_thDTqmU)
	> [<img src="https://img.youtube.com/vi/a1M_thDTqmU/0.jpg" width="200">](https://www.youtube.com/watch?v=a1M_thDTqmU "Virtual Machine (VM) vs Docker by IBM Technology 159,449 views 8 minutes, 52 seconds")
 * [Mastering Docker: Learn How to Build and Deploy Your Applications](https://www.youtube.com/watch?v=hzVqdoo-toQ)
	> [<img src="https://img.youtube.com/vi/hzVqdoo-toQ/0.jpg" width="200">](https://www.youtube.com/watch?v=hzVqdoo-toQ "Mastering Docker: Learn How to Build and Deploy Your Applications by Enterprise DevOps 834 views 1 hour, 31 minutes")
 * [DOCKER - COMO DEFINIR O USO DE CPU E MEMÓRIA DOS SEUS CONTAINERS!](https://www.youtube.com/watch?v=P52LyX9Nb5w)
	> [<img src="https://img.youtube.com/vi/P52LyX9Nb5w/0.jpg" width="200">](https://www.youtube.com/watch?v=P52LyX9Nb5w "DOCKER - COMO DEFINIR O USO DE CPU E MEMÓRIA DOS SEUS CONTAINERS! by Espaço Digital 1,237 views 13 minutes, 54 seconds")
 * [Mastering Docker with Ease: A Guide to GUI Tools for Docker Management](https://www.youtube.com/watch?v=w6zKHEAFwIE)
	> [<img src="https://img.youtube.com/vi/w6zKHEAFwIE/0.jpg" width="200">](https://www.youtube.com/watch?v=w6zKHEAFwIE "Mastering Docker with Ease: A Guide to GUI Tools for Docker Management by Hatam Danesh 165 views 12 minutes, 8 seconds")
 * [Jenkins Tutorial – How to Deploy a Test Server with Docker + Linux (Full Course)](https://www.youtube.com/watch?v=f4idgaq2VqA)
	> [<img src="https://img.youtube.com/vi/f4idgaq2VqA/0.jpg" width="200">](https://www.youtube.com/watch?v=f4idgaq2VqA "Jenkins Tutorial – How to Deploy a Test Server with Docker + Linux (Full Course) by freeCodeCamp.org 219,099 views 1 hour, 3 minutes")
 * [Docker Tutorial for Beginners - A Full DevOps Course on How to Run Applications in Containers](https://www.youtube.com/watch?v=fqMOX6JJhGo)
	> [<img src="https://img.youtube.com/vi/fqMOX6JJhGo/0.jpg" width="200">](https://www.youtube.com/watch?v=fqMOX6JJhGo "Docker Tutorial for Beginners - A Full DevOps Course on How to Run Applications in Containers by freeCodeCamp.org 2,589,711 views 2 hours, 10 minutes")
 * [GitHub Actions Tutorial - Basic Concepts and CI/CD Pipeline with Docker](https://www.youtube.com/watch?v=R8_veQiYBjI)
	> [<img src="https://img.youtube.com/vi/R8_veQiYBjI/0.jpg" width="200">](https://www.youtube.com/watch?v=R8_veQiYBjI "GitHub Actions Tutorial - Basic Concepts and CI/CD Pipeline with Docker by TechWorld with Nana 1,342,469 views 32 minutes")
 * [Jenkins Tutorial – How to Deploy a Test Server with Docker + Linux (Full Course)](https://www.youtube.com/watch?v=f4idgaq2VqA)
	> [<img src="https://img.youtube.com/vi/f4idgaq2VqA/0.jpg" width="200">](https://www.youtube.com/watch?v=f4idgaq2VqA "Jenkins Tutorial – How to Deploy a Test Server with Docker + Linux (Full Course) by freeCodeCamp.org 219,099 views 1 hour, 3 minutes")
