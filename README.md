# Описание решения

## Задача:
Написать программу, которая из имеющегося массива строк формирует новый массив из строк, длина которых меньше, либо равна 3 символам. Первоначальный массив можно ввести с клавиатуры, либо задать на старте выполнения алгоритма. При решении не рекомендуется пользоваться коллекциями, лучше обойтись исключительно массивами.

## Алгоритм

![Блок схема](pictures\Final_work_s1.jpg)

## Реализация
Исходный проект программы располагается в папке program

```c
//функция генерации массива
string[] ArrayGenerator(){
    Dictionary<int, string> dict = new Dictionary<int, string>();

    Console.WriteLine("Водите строки, для выхода введите 'exit'");

    bool repeatRead = true;
    int key = 0;

    while(repeatRead){
        string enter = Console.ReadLine()??"";

        if(enter == "exit"){
            repeatRead = false;
        }else{
            dict.Add(key, enter);
            key++;
        }
    }

    string[] resArr = new string[dict.Count];

    foreach(var item in dict){
        resArr[item.Key] = item.Value;
    }

    return resArr;
}

//функция создания нового массива из исходного, где длинна строки меньше или равна 3 символам
string[] ArrayWithLength3Simbols(string[] arr){
    Dictionary<int, string> dict = new Dictionary<int, string>();

    for(int i = 0; i<arr.Length; i++){
        if(arr[i].Length<=3){
            dict.Add(i,arr[i]);
        }
    }

    string[] resArr = new string[dict.Count];

    int index = 0;
    foreach (var item in dict)
    {
       resArr[index] = item.Value;
       index++; 
    }

    return resArr;
}

//Вывод массива
void PrintArray(string[] arr, string message){
    Console.WriteLine();
    Console.WriteLine(message);
    
    Console.WriteLine($"[{String.Join(",", arr)}]");    
}

//Тело программы

string[] inputArray = ArrayGenerator();
PrintArray(inputArray, "Исходный массив");
string[] resultArray = ArrayWithLength3Simbols(inputArray);
PrintArray(resultArray, "Массив - результат");
```