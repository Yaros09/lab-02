# lab-02

# Part_1
1) Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).
2) Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге
# echo "# lab-02" >> README.md
```
git init	
git add README.md
git commit -m "first commit"
git branch -M master
git remote add origin https://github.com/Yaros09/lab-02
git push -u origin main
```
3) Создайте файл hello_world.cpp в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу Hello world на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку using namespace std;
```
touch Hello world.cpp

#include <iostream>
using namespace std;
int main(int argc, char** argv){
cout << "Hello world" << endl;
}
EOF
```
4) Добавьте этот файл в локальную копию репозитория.
```
git add Hello world.cpp
```
5) Закоммитьте изменения с осмысленным сообщением.
```
git commit -a -m "Added new cpp file"
```
6) Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.
```
subl "Hello world.cpp"

#include <iostream>
#include <string>

using namespace std;
int main(int argc, char** argv){
cout << "Hello world" << endl;
	string name;
	cin>>name;
	cout << "Hello world from " << name << endl;
}
EOF
```
7) Закоммитьте новую версию программы. Почему не надо добавлять файл повторно git add?
```
git commit -a -m "Changed cpp file"
```
8) Запуште изменения в удалёный репозиторий.
```
git push -u origin master
```
9) Проверьте, что история коммитов доступна в удалёный репозитории.
![image](https://user-images.githubusercontent.com/91633974/160619526-683cca93-7ca1-4eed-a6b8-35328601269d.png)
