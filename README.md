# projet-todoliste
aire un code javascript de todolist le projet consist à realiser une liste de tâches donnant les possibilités suivantes : lister les tâches ,ajouter une tache depuis un formulaire,supprimer une tache, modifier une tâche.
<!DOCTYPE html>
<html lang="fr">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ma TodoList</title>
    <style>
        /* Styles CSS */

        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
            background-image: linear-gradient(rgba(135, 206, 235, 0.3), rgba(69, 90, 98, 0.9)),url('images/hands-on-desk-at-meeting.jpg');
            background-repeat: no-repeat;
            background-size: cover;
            background-position: center;
        }

        .container {
            display: flex;
            flex-direction: column;
            min-height: 100vh;
            background-image: linear-gradient(rgba(135, 206, 235, 0.3), rgba(0, 0, 0, 0.9)),url('images/wrtiting-tools.jpg');
        }

        header {
            background-color: #0693E3;
            padding: 25px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            color: #FFFFFF;
            animation: headerAnimation 1s infinite alternate;
        }

        /* @keyframes headerAnimation {
            from {
                background-color: #5898bd;
            }

            to {
                background-color: #eac894;
            }
        }*/

        main {
            flex: 1;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 20px;
        }

        .logo {
            font-size: 24px;
            font-weight: bold;
            animation: logoAnimation 2s infinite linear;
        }

        @keyframes logoAnimation {
            0% {
                color: #FFFFFF;
            }

            50% {
                color: #FFCC00;
            }

            100% {
                color: #FFFFFF;
            }
        }

        nav ul {
            list-style-type: none;
            margin: 0;
            padding: 0;
            display: flex;
        }

        nav ul li {
            margin-right: 10px;
            animation: menuAnimation 1s infinite alternate;
        }

        @keyframes menuAnimation {
            from {
                transform: translateX(0);
            }

            to {
                transform: translateX(5px);
            }
        }

        nav ul li a {
            border-radius: 50px;
            border: 1px solid rgb(10, 5, 5);
            padding: 8px 16px;
            color: #FFFFFF;
            text-decoration: none;
            transition: color 0.3s;
        }

        nav ul li a:hover {
            color: #FFCC00;
        }

        .container {
            width: 80%;
            margin: 50px auto;
            background-color: #FFFFFF/ 68%;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        h1 {
            font-size: 24px;
            color: #333333;
            margin-bottom: 20px;
        }

        p {
            font-size: 16px;
            color: #ffffff;
        }

        #newtask {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        #newtask input {
            width: 75%;
            height: 45px;
            padding: 12px;
            color: #111111;
            font-weight: 500;
            border-radius: 5px;
            font-family: 'Poppins', sans-serif;
            font-size: 15px;
            border: 2px solid #d1d3d4;
        }

        #newtask input:focus {
            outline: none;
            border-color: #0d75ec;
        }

        #newtask button {
            font-weight: 500;
            font-size: 16px;
            background-color: #0d75ec;
            border: none;
            color: #ffffff;
            cursor: pointer;
            outline: none;
            width: 20%;
            height: 66px;
            border-radius: 5px;
            font-family: 'Poppins', sans-serif;
        }

        #tasks {
            background-color: #ffffff;
            padding: 20px;
            border-radius: 10px;
        }

        .task {
            display: flex;
            align-items: center;
            justify-content: space-between;
            border: 1px solid #939697;
            cursor: pointer;
            background-color: #c5e1e6;
            height: 50px;
            margin-bottom: 10px;
            padding: 5px 10px;
            border-radius: 5px;
        }

        .task span {
            font-family: 'Poppins', sans-serif;
            font-size: 15px;
            font-weight: 400;
        }

        .task button {
            background-color: #0a2ea4;
            color: #ffffff;
            border: none;
            cursor: pointer;
            outline: none;
            height: 100%;
            width: 75px;
            border-radius: 5px;
            margin-left: 10px;
        }

        footer {
            background-color: #000000;
            padding: 20px;
            color: #FFFFFF;
            text-align: center;
            background-size: cover;
        }

        footer .footer-left,
        footer .footer-right {
            display: inline-block;
            color: #FFFFFF;
        }

        footer .footer-left {
            text-align: left;
            width: 50%;
            right:300px;
            position: relative;
        }

        footer .footer-right {
            text-align: right;
            width: 50%;
            position: relative;
            left: 300px;
        }

        footer .footer-left ol {
            margin: 0;
            padding: 0;
            list-style-type: upper-alpha;
        }

        footer .footer-bottom {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-top: 10px;
        }

        footer .footer-bottom img {
            width: 60px;
            height: 30px;
            margin-right: 10px;
            border: 1px solid rgb(255, 254, 254);
            border-radius: 10%;
            background-color: #f2f2f2;
        }  
    </style>
</head>

<header>
    <div class="logo">Todoliste</div>
    <nav>
        <ul>
            <li><a href="#">Bienvenue</a></li>
            <li><a href="#">Projet</a></li>
            <li><a href="#">Groupe 8</a></li>
        </ul>
    </nav>
</header>

<body>

    <div class="container">
        <main>
            <div class="container">
                <div id="newtask">
                    <input type="text" placeholder="Tâche à réaliser...">
                    <button id="push">Ajouter</button>
                </div>
                <div id="tasks"></div>
            </div>
        </main>
    </div>
    
    <script>
        document.querySelector('#push').onclick = function () {
            const taskInput = document.querySelector('#newtask input');
            const taskText = taskInput.value.trim();

            if (taskText === "") {
                alert("Veuillez entrer une tâche");
            } else {
                const taskElement = document.createElement("div");
                taskElement.classList.add("task");
                taskElement.innerHTML = `
                    <span>${taskText}</span>
                    <button class="delete">Supprimer</button>
                    <button class="edit">Modifier</button>
                `;
                document.querySelector('#tasks').appendChild(taskElement);
                taskInput.value = "";

                const currentTasks = document.querySelectorAll(".delete");
                for (let i = 0; i < currentTasks.length; i++) {
                    currentTasks[i].onclick = function () {
                        this.parentNode.remove();
                    }
                }

                const currentEdits = document.querySelectorAll(".edit");
                for (let i = 0; i < currentEdits.length; i++) {
                    currentEdits[i].onclick = function () {
                        const taskSpan = this.parentNode.querySelector("span");
                        const newTaskText = prompt("Modifier la tâche", taskSpan.textContent.trim());
                        if (newTaskText !== null) {
                            taskSpan.textContent = newTaskText;
                        }
                    }
                }
            }
        }
    </script>
</body>

<footer>
    <div class="footer-left">
        <ol>
            <h3>Membre du groupe 8:</h3>
            <ul>EKLOU ESDRAS Josias</ul>
            <ul>NZENGUI MOUSSAMBI Regis</ul>
            <ul>MEYO ALLOGHE Clement</ul>
        </ol>
    </div>
    <div class="footer-right">
        <p>Projet du Groupe 8 sur un site de todoliste.</p>
    </div>
    <div class="footer-bottom">
        <img src="images/logoinptic.png" alt="Logo" />
        <p>© Tous droits réservés à ce site de Josias, Clement, Regis.</p>
    </div>
</footer>

</html>
