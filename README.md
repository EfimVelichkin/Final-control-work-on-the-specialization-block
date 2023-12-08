# Задание №1
### Используя команду cat в терминале операционной системы Linux, создать два файла Домашние животные (заполнив файл собаками, кошками, хомяками) и Вьючные животными заполнив файл Лошадьми, верблюдами и ослы), а затем объединить их. Просмотреть содержимое созданного файла. Переименовать файл, дав ему новое имя (Друзья человека).
---
echo "собаки, кошки, хомяки" > "Домашние животные"
echo "Лошади, верблюды, ослы" > "Вьючные животными"
cat "Домашние животные" "Вьючные животными" > "Объединенный файл"
cat "Объединенный файл"
mv "Объединенный файл" "Друзья человека"
---
# Задание №2
### Создать директорию, переместить файл туда.
---
mkdir "newDir"
mv "Друзья человека" "newDir"
---
# Задание №3
### Подключить дополнительный репозиторий MySQL. Установить любой пакет из этого репозитория.
---
sudo apt-get update
sudo apt-get install mysql-server
---
# Задание №4
### Установить и удалить deb-пакет с помощью dpkg.
---
sudo dpkg --install google-chrome-stable_current_amd64.deb
sudo dpkg --remove google-chrome-stable
---
# Задание №5
### Выложить историю команд в терминале ubuntu
---
echo "собаки, кошки, хомяки" > "Домашние животные"
echo "лошади, верблюды, ослы" > "Вьючные животные"
cat "Домашние животные" "Вьючные животные" > "Объединенный файл"
cat "Объединенный файл"
mv "Объединенный файл" "Друзья человека"
mkdir "newDir"
mv "Друзья человека" "newDir"
sudo add-apt-repository 'deb http;//archive.ubuntu.com/ubuntu trusty universe'
sudo apt-get update
sudo apt-get install mysql-server
sudo dpkg -i package_name.deb
cd Загрузки
sudo dpkg --install google-chrome-stable_current_amd64.deb 
sudo dpkg --remove google-chrome-stable
cd ../
history
---
# Задание №6
###  Нарисовать диаграмму, в которой есть класс родительский класс, домашние животные и вьючные животные, в составы которых в случае домашних животных войдут классы: собаки, кошки, хомяки, а в класс вьючные животные войдут: Лошади, верблюды и ослы).
![Diagramm](https://github.com/EfimVelichkin/Final-control-work-on-the-specialization-block/assets/120294162/857d7d99-4bc6-40c6-a1dd-508a129d4162)
# Задание №7
### В подключенном MySQL репозитории создать базу данных “Друзья человека”
<pre>
CREATE DATABASE Human_friends;
</pre>
# Задание №8
###  Создать таблицы с иерархией из диаграммы в БД
<pre>
USE Human_friends;
CREATE TABLE animal_classes
(
	Id INT AUTO_INCREMENT PRIMARY KEY, 
	Class_name VARCHAR(20)
);

INSERT INTO animal_classes (Class_name)
VALUES ('вьючные'),
('домашние');  


CREATE TABLE packed_animals
(
	  Id INT AUTO_INCREMENT PRIMARY KEY,
    Genus_name VARCHAR (20),
    Class_id INT,
    FOREIGN KEY (Class_id) REFERENCES animal_classes (Id) ON DELETE CASCADE ON UPDATE CASCADE
);

INSERT INTO packed_animals (Genus_name, Class_id)
VALUES ('Лошади', 1),
('Ослы', 1),  
('Верблюды', 1); 
    
CREATE TABLE home_animals
(
	  Id INT AUTO_INCREMENT PRIMARY KEY,
    Genus_name VARCHAR (20),
    Class_id INT,
    FOREIGN KEY (Class_id) REFERENCES animal_classes (Id) ON DELETE CASCADE ON UPDATE CASCADE
);

INSERT INTO home_animals (Genus_name, Class_id)
VALUES ('Кошки', 2),
('Собаки', 2),  
('Хомяки', 2); 

CREATE TABLE cats 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthday DATE,
    Commands VARCHAR(50),
    Genus_id int,
    Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
</pre>
