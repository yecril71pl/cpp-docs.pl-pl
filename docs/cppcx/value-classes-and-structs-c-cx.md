---
title: Klasy i struktury wartości (C++/CX)
ms.date: 12/30/2016
helpviewer_keywords:
- value struct
- value class
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
ms.openlocfilehash: 4a4897f0a3b5c95ffb58e5c9666a2d764d71b3ec
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752897"
---
# <a name="value-classes-and-structs-ccx"></a>Klasy i struktury wartości (C++/CX)

Struktura *wartości* lub *klasa wartości* jest pod zgodny ze środowiska wykonawczego systemu Windows ("zwykły starej struktury danych"). Ma stały rozmiar i składa się tylko z pól; w przeciwieństwie do klasy ref, nie ma żadnych właściwości.

Poniższe przykłady pokazują, jak zadeklarować i zainicjować struktury wartości.

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

Gdy zmienna typu wartości jest przypisana do innej zmiennej, wartość jest kopiowana, dzięki czemu każda z dwóch zmiennych ma własną kopię danych. *Struktura wartości* jest strukturą o stałym rozmiarze, która zawiera tylko `value struct` pola danych publicznych i jest zadeklarowana przy użyciu słowa kluczowego.

*Klasa wartości* jest tak `value struct` samo jak, z tą różnicą, że jej pola muszą być jawnie podane dostępności publicznej. Jest zadeklarowany przy `value class` użyciu słowa kluczowego.

Struktura wartości lub klasa wartości może zawierać jako pola tylko podstawowe `Platform::String^`typy liczbowe, klasy wyliczenia lub [Platform::IBox \<T>^](../cppcx/platform-ibox-interface.md) gdzie T jest typem liczbowym lub klasą wyliczenia lub klasą wartości lub strukturą. Pole `IBox<T>^` może mieć wartość `nullptr`—tak C++ implementuje pojęcie *typów wartości nullable*.

Struktura klasy wartości lub wartości, `Platform::String^` `IBox<T>^` która zawiera lub `memcpy`typ jako element członkowski, nie jest w stanie.

Ponieważ wszystkie elementy `value class` `value struct` członkowskie lub są publiczne i są emitowane do metadanych, standardowe typy C++ nie są dozwolone jako elementy członkowskie. Różni się to od klas `private` ref, które mogą zawierać lub `internal` standardowe typy C++..

Poniższy fragment kodu `Coordinates` deklaruje `City` i typów jako struktury wartości. Należy zauważyć, `City` że jeden `GeoCoordinates` z elementów członkowskich danych jest typem. A `value struct` może zawierać inne struktury wartości jako elementy członkowskie.

[!code-cpp[cx_classes#07](../cppcx/codesnippet/CPP/classesstructs/class1.h#07)]

## <a name="parameter-passing-for-value-types"></a>Przekazywanie parametrów dla typów wartości

Jeśli typ wartości jest parametrem funkcji lub metody, zwykle jest on przekazywany przez wartość. W przypadku większych obiektów może to spowodować problem z wydajnością. W programie Visual Studio2013 i wcześniejszych typy wartości w języku C++/CX były zawsze przekazywane przez wartość. W programie Visual Studio 2015 i nowszych można przekazać typy wartości przez odwołanie lub wartość.

Aby zadeklarować parametr, który przekazuje typ wartości według wartości, należy użyć kodu następującego:

```cpp
void Method1(MyValueType obj);
```

Aby zadeklarować parametr, który przekazuje typ wartości przez odwołanie, należy użyć symbolu odwołania (&), jak w następujący sposób:

```cpp
void Method2(MyValueType& obj);
```

Typ wewnątrz Method2 jest odwołaniem do MyValueType i działa w taki sam sposób jak typ odwołania w standardzie C++.

Podczas wywoływania Metody1 z innego języka, takiego jak C#, nie trzeba używać `ref` lub `out` słowa kluczowego. Po wywołaniu Metody2 `ref` użyj słowa kluczowego.

```
Method2(ref obj);
```

Można również użyć symbolu wskaźnika (*), aby przekazać typ wartości przez odwołanie. Zachowanie w odniesieniu do osób wywołujących w innych językach jest `ref` taka sama (wywołujących w języku C# używać słowa kluczowego), ale w metodzie, typ jest wskaźnikiem do typu wartości.

## <a name="nullable-value-types"></a>Typy wartości dopuszczające wartość null

Jak wspomniano wcześniej, klasa wartości lub struktura wartości może mieć pole typu [Platform::IBox\<T>^](../cppcx/platform-ibox-interface.md)— na przykład . `IBox<int>^` Takie pole może mieć dowolną wartość liczbową, która jest prawidłowa `int` `nullptr`dla typu lub może mieć wartość . Pole można przekazać z do wartości null jako argument do metody, której parametr jest zadeklarowany jako opcjonalny, lub w innym miejscu, w których typ wartości nie musi mieć wartości.

W poniższym przykładzie pokazano, jak zainicjować strukturę, która ma pole nullable.

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

Sama struktura wartości może być nullable w taki sam sposób, jak pokazano poniżej:

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

[System typów (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Odwołanie do języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)<br/>
[Klasy i struktury odwołania (C++/CX)](../cppcx/ref-classes-and-structs-c-cx.md)
