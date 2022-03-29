# lab-02

# PART_1
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
cat > "Hello world.cpp" <<EOF

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
10) 
![image](https://user-images.githubusercontent.com/91633974/160619526-683cca93-7ca1-4eed-a6b8-35328601269d.png)

# PART_2
1) В локальной копии репозитория создайте локальную ветку patch1.
```
git checkout -b patch
```
![image](https://user-images.githubusercontent.com/91633974/160619905-601283f4-ea39-4aa2-8503-0e38bbf35e2b.png)

2) Внесите изменения в ветке patch1 по исправлению кода и избавления от using namespace std;
```
#include <iostream>
#include <string>

int main(int argc, char** argv){
	string name;
	std::cin>>name;
	std::cout << "Hello world from " << name <<endl;
}
EOF
```
![image](https://user-images.githubusercontent.com/91633974/160619999-4680bc26-bdd8-4118-93f1-43e513d0f44d.png)

3) commit, push локальную ветку в удалённый репозиторий.
```
git commit -a -m "Twice fixed cpp file"
git push -u origin master
```
![image](https://user-images.githubusercontent.com/91633974/160621840-acd047b4-93f4-4140-8359-de58f476ac77.png)
![image](https://user-images.githubusercontent.com/91633974/160621947-c00a51c1-a605-4339-aed4-f1b24de26bf3.png)

4) Проверьте, что ветка patch1 доступна в удалёный репозитории.
5) Создайте pull-request patch1 -> master
6) В локальной копии в ветке patch1 добавьте в исходный код комментарии.
```
#include <string>
int main(int argc, char** argv){
string name; \\User name
	std::cin>>name; \\Input user name
	std::cout << "Hello world from " << name <<std::endl;
}
```
7) commit, push
```
git commit -a -m "Added comments"
git push -u origin master 
```
![image](https://user-images.githubusercontent.com/91633974/160622372-bf716c4c-8e8b-45b4-85bb-1df5773d918a.png)

8) Проверьте, что новые изменения есть в созданном на шаге 5 pull-request
9) В удалённый репозитории выполните слияние PR patch1 -> master и удалите ветку patch1 в удаленном репозитории
10) Локально выполните pull
```
git pull origin 
```
![image](https://user-images.githubusercontent.com/91633974/160623431-b9d76e48-668e-42cf-8741-aa4cc1078a8b.png)

11) С помощью команды git log просмотрите историю в локальной версии ветки master
```
git log
```
![image](https://user-images.githubusercontent.com/91633974/160623143-48073fb4-4ec7-429a-8ec9-c596fac72f18.png)
![image](https://user-images.githubusercontent.com/91633974/160623182-133df125-d382-4eff-beb3-db947bf0d226.png)
![image](https://user-images.githubusercontent.com/91633974/160623275-978891ba-4824-410c-ab35-6c7f8286cbcf.png)

12) Удалите локальную ветку patch1
```
git branch -d patch1
```
#PART_3
1) Создайте новую локальную ветку patch2
```
git checkout -b patch2

```
2) Измените code style с помощью утилиты clang-format. Например, используя опцию -style=Mozilla
```
clang-format -i -style=Mozilla "Hello world.cpp"
```
3) commit, push, создайте pull-request patch2 -> master
```
git commit -a -m "Changed code style in cpp
git push -u origin patch2
```
4) В ветке master в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.
```
#include <string>
int main(int argc, char** argv){
string name; \\User name.
	std::cin>>name; \\Введите имя
	std::cout << "Hello world from " << name <<std::endl;
}
```
5) Убедитесь, что в pull-request появились конфликтны
6) Для этого локально выполните pull + rebase (точную последовательность команд, следует узнать самостоятельно). Исправьте конфликты
```
git pull --rebase origin master
subl "Hello world.cpp"
git add "Hello world.cpp"
git rebase --continue
```
![image](https://user-images.githubusercontent.com/91633974/160625928-a0be190c-c113-4899-b5e1-eacb7d5b7a58.png)

7) Сделайте force push в ветку patch2
```
git push -f origin patch2
```
![image](https://user-images.githubusercontent.com/91633974/160627091-2638fc00-b271-43b3-9270-c426285ca2c0.png)

8) Убедитель, что в pull-request пропали конфликтны
9) Вмержите pull-request patch2 -> master
![image](https://user-images.githubusercontent.com/91633974/160626885-455db0e3-6afd-4247-b3a5-c95c1d8026a7.png)

