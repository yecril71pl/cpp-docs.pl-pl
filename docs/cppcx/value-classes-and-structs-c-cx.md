---
title: "Wartość klas i struktur (C + +/ CX) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- value struct
- value class
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
caps.latest.revision: "12"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4392125d1834f31b02e4087644f8b8a06ad238f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="value-classes-and-structs-ccx"></a>Wartość klas i struktur (C + +/ CX)
A *struktury wartość* lub *klasę wartości* jest systemu Windows POD zgodnego środowiska uruchomieniowego ("zwykły starych danych struktury"). Ma stały rozmiar i składa się z pól. w odróżnieniu od klasy ref go nie ma właściwości.  
  
 Poniższe przykłady przedstawiają sposób zadeklarować i zainicjować struktury wartości.  
  
```  
  
// in mainpage.xaml.h:  
    value struct TestStruct  
    {  
        Platform::String^ str;  
        int i;  
    };  
  
    value struct TestStruct2  
    {  
        TestStruct ts;  
        Platform::String^ str;  
        int i;  
    };  
  
// in mainpage.cpp:  
    // Initialize a value struct with an int and String  
    TestStruct ts = {"I am a TestStruct", 1};  
  
    // Initialize a value struct that contains  
    // another value struct, an int and a String  
    TestStruct2 ts2 = {{"I am a TestStruct", 1}, "I am a TestStruct2", 2};  
  
    // Initialize value struct members individually.  
    TestStruct ts3;   
    ts3.i = 108;  
    ts3.str = "Another way to init a value struct.";  
  
```  
  
 Gdy zmienna typu wartości jest przypisany do innej zmiennej, wartość jest kopiowana, dzięki czemu każdy z dwie zmienne ma własną kopię danych. A *struktury wartość* jest strukturą stałym rozmiarze, która zawiera tylko pola publiczne danych i jest zadeklarowany za pomocą `value struct` — słowo kluczowe.  
  
 A *klasę wartości* jest tak jak `value struct` z tą różnicą, że jego pól muszą jawnie otrzymać powszechnej dostępności. Jest on zadeklarowany za pomocą `value class` — słowo kluczowe.  
  
 Wartość struktury lub klasy wartości mogą zawierać jako pola tylko podstawowe typy liczbowe, Wylicz klasy `Platform::String^`, lub [Platform::IBox \<T > ^](../cppcx/platform-ibox-interface.md) , gdzie T jest liczbowych klasy typu lub wyliczenia lub wartość lub struktury. `IBox<T>^` Pole może mieć wartość `nullptr`— jest to, jak C++ implementuje pojęcie *typy o wartości zerowalnej*.  
  
 Wartość klasie lub strukturze wartość, która zawiera `Platform::String^` lub `IBox<T>^` typu, ponieważ nie jest elementem członkowskim `memcpy`-stanie.  
  
 Ponieważ wszystkie elementy członkowskie `value class` lub `value struct` są publiczne oraz czy wydane do metadanych, standard C++ typy nie są dozwolone jako elementy członkowskie. Różni się to od klasy ref, które mogą zawierać `private` lub `internal` standardowych typów języka C++.  
  
 Deklaruje następującego fragmentu kodu `Coordinates` i `City` typy jako wartość struktury. Powiadomienie, że jedna z `City` elementy członkowskie danych jest `GeoCoordinates` typu. A `value struct` może zawierać inne struktury wartość jako elementy członkowskie.  
  
 [!code-cpp[cx_classes#07](../cppcx/codesnippet/CPP/classesstructs/class1.h#07)]  
  
## <a name="parameter-passing-for-value-types"></a>Przekazywanie dla typów wartości parametru  
 Jeśli masz wartość typu jako parametr metody lub funkcji, zwykle jest przekazywany przez wartość. Dla większych obiektów może to spowodować problemy z wydajnością. W Visual Studio2013 lub starszej wartości typów w języku C + +/ CX zawsze były przekazywane przez wartość. W programie Visual Studio 2015 i nowszych można przekazać typów wartości przez odwołanie lub wartość.  
  
 Aby zadeklarować parametr przekazywany przez wartość typu wartości, należy użyć kodu podobne do poniższych:  
  
```  
void Method1(MyValueType obj);  
```  
  
 Aby zadeklarować parametr przekazywany przez odwołanie do typu wartości, należy użyć symbolu odwołania (&), co przedstawiono poniżej:  
  
```  
void Method2(MyValueType& obj);  
```  
  
 Typ wewnątrz metoda2 jest odwołaniem do MyValueType i działa tak samo, jak typ referencyjny w standardu C++.  
  
 Podczas wywoływania metoda1 w innym języku, takich jak C#, nie trzeba używać `ref` lub `out` — słowo kluczowe. Podczas wywoływania metoda2, użyj `ref` — słowo kluczowe.  
  
```  
Method2(ref obj);  
```  
  
 Umożliwia także symbol wskaźnika (*) do przekazania typu wartości przez odwołanie. Zachowanie względem wywołań w innych językach jest takie samo (wywołań w języku C# użyj `ref` — słowo kluczowe), ale w metodzie typu jest wskaźnikiem do typu wartość.  
  
## <a name="nullable-value-types"></a>typy dopuszczające wartości zerowe wartości  
 Jak wspomniano wcześniej, wartość klasie lub strukturze wartość może mieć pola typu [Platform::IBox\<T > ^](../cppcx/platform-ibox-interface.md)— na przykład `IBox<int>^`. Takie pole może mieć wartość liczbową, który jest prawidłowy dla `int` typu, albo może mieć wartość `nullptr`. Pole wartości null jako argument można przekazać do metody, których parametr jest zadeklarowany jako opcjonalny lub dowolnego miejsca, która nie jest typem wartości musi mieć wartość.  
  
 Poniższy przykład pokazuje, jak zainicjować struktury zawierającej pole wartości null.  
  
```  
public value struct Student  
{  
    Platform::String^ Name;  
    int EnrollmentYear;  
    Platform::IBox<int>^ GraduationYear; // Null if not yet graduated.   
};  
//To create a Student struct, one must populate the nullable type.   
MainPage::MainPage()  
{  
    InitializeComponent();  
  
    Student A;  
    A.Name = "Alice";  
    A.EnrollmentYear = 2008;  
    A.GraduationYear = ref new Platform::Box<int>(2012);  
  
    Student B;  
    B.Name = "Bob";  
    B.EnrollmentYear = 2011;  
    B.GraduationYear = nullptr;  
  
    IsCurrentlyEnrolled(A);  
    IsCurrentlyEnrolled(B);  
}  
bool MainPage::IsCurrentlyEnrolled(Student s)  
{  
    if (s.GraduationYear == nullptr)  
    {  
        return true;  
    }  
    return false;  
}  
  
```  
  
 Struktury wartość sam może dopuszczać wartości null w taki sam sposób, jak pokazano poniżej:  
  
```  
  
public value struct MyStruct  
{  
public:  
    int i;  
    Platform::String^ s;  
};  
  
public ref class MyClass sealed  
{  
public:  
    property Platform::IBox<MyStruct>^ myNullableStruct;  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [System typów (C + +/ CX)](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)   
 [Klasy i struktury odwołania (C++/CX)](../cppcx/ref-classes-and-structs-c-cx.md)