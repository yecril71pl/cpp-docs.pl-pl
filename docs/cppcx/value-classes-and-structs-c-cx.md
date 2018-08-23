---
title: Klasy i struktury wartości (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
helpviewer_keywords:
- value struct
- value class
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 226198c35dc0b7e7e1c7fab4ce81fc4782b5ca38
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589059"
---
# <a name="value-classes-and-structs-ccx"></a>Klasy i struktury wartości (C + +/ CX)
A *struktury wartości* lub *klasę wartości* jest Windows ZASOBNIKA zgodnego środowiska uruchomieniowego ("zwykłe stare dane strukturę"). Ma stały rozmiar i składa się z pól. w odróżnieniu od klasy ref go nie ma właściwości.  
  
 Poniższe przykłady pokazują, jak zadeklarować i zainicjować strukturach wartości.  
  
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
  
 Gdy zmienna typu wartości jest przypisany do innej zmiennej, wartość jest kopiowana, tak, aby każdy z dwóch zmiennych ma własną kopię danych. A *struktury wartości* to struktura stałym rozmiarze, który zawiera tylko pola publiczne danych i jest zadeklarowana za pomocą `value struct` — słowo kluczowe.  
  
 A *klasę wartości* jest podobnie jak `value struct` z tą różnicą, że jej pola muszą jawnie otrzymać powszechnej dostępności. Jest zadeklarowana za pomocą `value class` — słowo kluczowe.  
  
 Wartość struktury lub klasy wartości mogą zawierać jako pola tylko podstawowe typy liczbowe, Wylicz klasy `Platform::String^`, lub [Platform::IBox \<T > ^](../cppcx/platform-ibox-interface.md) , gdzie T jest liczbowe klasy typu lub wyliczenia lub wartość klasy lub struktury. `IBox<T>^` Pole może mieć wartość `nullptr`— jest to, jak C++ implementuje koncepcji *typy o wartości zerowalnej*.  
  
 Wartość klasy lub struktury wartość, która zawiera `Platform::String^` lub `IBox<T>^` typu, ponieważ nie jest członkiem `memcpy`-stanie.  
  
 Ponieważ wszystkie elementy członkowskie `value class` lub `value struct` są publiczne i jest emitowany do metadanych, standard C++ typy nie są dozwolone jako elementy członkowskie. To różni się od klasy ref, które mogą zawierać `private` lub `internal` standardowych typów C++...  
  
 Poniższy fragment kodu deklaruje `Coordinates` i `City` typy jako strukturach wartości. Powiadomienie, że jedna z `City` elementy członkowskie danych jest `GeoCoordinates` typu. Element `value struct` może zawierać innych strukturach wartości jako elementy członkowskie.  
  
 [!code-cpp[cx_classes#07](../cppcx/codesnippet/CPP/classesstructs/class1.h#07)]  
  
## <a name="parameter-passing-for-value-types"></a>Przekazywanie dla typów wartości parametru  
 W przypadku wartości typu jako parametru funkcji lub metody normalnie jest przekazywany przez wartość. W przypadku większych obiektów może to spowodować problemy z wydajnością. W Visual Studio2013 i starszych wartość typów w języku C + +/ CX zawsze były przekazywane przez wartość. W programie Visual Studio 2015 i nowszych możesz przekazać typów wartości przez odwołanie, lub według wartości.  
  
 Aby zadeklarować parametr, który przekazuje typ wartości przez wartość, należy użyć kodu, jak pokazano poniżej:  
  
```  
void Method1(MyValueType obj);  
```  
  
 Aby zadeklarować parametr, który przekazuje typ wartości przez odwołanie, należy użyć symbolu odwołanie (&), co przedstawiono poniżej:  
  
```  
void Method2(MyValueType& obj);  
```  
  
 Typ wewnątrz Method2 jest odwołaniem do MyValueType i działa tak samo jak typ odwołania w standardzie języka C++.  
  
 Gdy wywołujesz metoda1 z innego języka, takich jak C#, nie trzeba używać `ref` lub `out` — słowo kluczowe. Po wywołaniu Method2 użyj `ref` — słowo kluczowe.  
  
```  
Method2(ref obj);  
```  
  
 Symbol wskaźnika (*) umożliwia również przekazać typ wartości przez odwołanie. Zachowanie w odniesieniu do obiektów wywołujących w innych językach jest taka sama (obiekty wywołujące w języku C# użyj `ref` — słowo kluczowe), ale w metodzie tego typu jest wskaźnikiem do typu wartości.  
  
## <a name="nullable-value-types"></a>Typy o wartości zerowalnej  
 Jak wspomniano wcześniej, klasą wartości lub wartości struktury mogą mieć pola typu [Platform::IBox\<T > ^](../cppcx/platform-ibox-interface.md)— na przykład `IBox<int>^`. Takie pole może mieć wartość liczbowa, która jest prawidłowa dla `int` typu lub go może mieć wartość `nullptr`. Pola typu dopuszczającego wartość NULL można przekazać jako argument do metody, w której parametr jest zadeklarowana jako opcjonalna lub dowolnej innej lokalizacji, która nie jest typem wartości musi mieć wartość.  
  
 Poniższy przykład pokazuje, jak zainicjować struktury, która zawiera pole dopuszczającego wartość null.  
  
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
  
 Sama struktura wartość może być typem dopuszczającym w taki sam sposób, jak pokazano poniżej:  
  
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