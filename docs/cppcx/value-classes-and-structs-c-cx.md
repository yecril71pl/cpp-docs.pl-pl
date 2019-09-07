---
title: Klasy wartości i struktury (C++/CX)
ms.date: 12/30/2016
helpviewer_keywords:
- value struct
- value class
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
ms.openlocfilehash: 3340c5e387dc58ddcb5348cdc041a58840463995
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740930"
---
# <a name="value-classes-and-structs-ccx"></a>Klasy wartości i struktury (C++/CX)

*Struktura wartości* lub *klasa wartości* to środowisko wykonawcze systemu Windows zgodna ze standardem ("zwykła Stara struktura danych"). Ma stały rozmiar i składa się tylko z pól; w przeciwieństwie do klasy ref nie ma właściwości.

W poniższych przykładach pokazano, jak zadeklarować i zainicjować struktury wartości.

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

Gdy zmienna typu wartości jest przypisana do innej zmiennej, wartość jest kopiowana, dzięki czemu każda z dwóch zmiennych ma własną kopię danych. Struktura *wartości* jest strukturą o stałym rozmiarze, która zawiera tylko publiczne pola danych i jest zadeklarowana za `value struct` pomocą słowa kluczowego.

*Klasa wartości* jest tak samo jak, `value struct` z tą różnicą, że jej pola muszą być jawnie dostępne do publicznego ułatwienia dostępu. Jest on zadeklarowany za pomocą `value class` słowa kluczowego.

Struktura wartości lub Klasa wartości może zawierać jako pola tylko podstawowe typy liczbowe, klasy `Platform::String^`wyliczeniowe lub [platform:: IBox \<T > ^](../cppcx/platform-ibox-interface.md) , gdzie T jest typem liczbowym lub klasą wartości lub strukturą. Pole może mieć `nullptr`wartość — to C++ jak implementuje koncepcję *typów wartości null.* `IBox<T>^`

Klasa wartości lub struktura wartości, która zawiera `Platform::String^` lub `IBox<T>^` typ jako element członkowski, nie `memcpy`jest możliwa.

Ponieważ wszystkie składowe `value class` lub `value struct` są publiczne i są emitowane do metadanych, typy standardowe C++ nie są dozwolone jako elementy członkowskie. Różni się to od klas referencyjnych, które mogą `private` zawierać `internal` lub C++ standardowe typy..

Poniższy fragment kodu deklaruje `Coordinates` typy i `City` jako struktury wartości. Zwróć uwagę, że jeden `City` z elementów członkowskich danych `GeoCoordinates` jest typem. Element `value struct` może zawierać inne struktury wartości jako elementy członkowskie.

[!code-cpp[cx_classes#07](../cppcx/codesnippet/CPP/classesstructs/class1.h#07)]

## <a name="parameter-passing-for-value-types"></a>Przekazywanie parametrów dla typów wartości

Jeśli masz typ wartości jako parametr funkcji lub metody, jest on zwykle przenoszona przez wartość. W przypadku większych obiektów może to spowodować problem z wydajnością. W programie Visual Studio2013 i starszych typy wartości w C++/CX były zawsze przesyłane przez wartość. W programie Visual Studio 2015 i nowszych można przekazać typy wartości według odwołania lub wartości.

Aby zadeklarować parametr, który przekazuje typ wartości według wartości, należy użyć następującego kodu:

```
void Method1(MyValueType obj);
```

Aby zadeklarować parametr, który przekazuje typ wartości przez odwołanie, Użyj symbolu odwołania (&), jak w następujących przypadkach:

```
void Method2(MyValueType& obj);
```

Typ wewnątrz Method2 jest odwołaniem do wartości i działa tak samo jak typ referencyjny w standardowym C++.

Gdy wywołasz Metoda1 z innego języka, na C#przykład, nie musisz używać `ref` słowa kluczowego or. `out` Gdy wywołasz Method2, użyj `ref` słowa kluczowego.

```
Method2(ref obj);
```

Można również użyć symbolu wskaźnika (*), aby przekazać typ wartości według odwołania. Zachowanie w odniesieniu do obiektów wywołujących w innych językach jest takie samo (obiekty C# wywołujące `ref` w użyciu słowa kluczowego), ale w metodzie typ jest wskaźnikiem do typu wartości.

## <a name="nullable-value-types"></a>Typy wartości null

Jak wspomniano wcześniej, klasą wartości lub strukturą wartości może być pole typu [platform:: IBox\<T > ^](../cppcx/platform-ibox-interface.md) `IBox<int>^`— na przykład. Takie pole może mieć dowolną wartość liczbową, która jest prawidłowa dla `int` typu, lub może mieć `nullptr`wartość. Pole dopuszczające wartość null można przekazać jako argument do metody, której parametr jest zadeklarowany jako opcjonalny, lub w innym miejscu, w którym typ wartości nie jest wymagany.

Poniższy przykład pokazuje, jak zainicjować strukturę, która ma pole dopuszczające wartość null.

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

Sama struktura wartości może wprowadzać wartości null w taki sam sposób, jak pokazano poniżej:

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

## <a name="see-also"></a>Zobacz także

[System typów (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)<br/>
[Klasy i struktury odwołania (C++/CX)](../cppcx/ref-classes-and-structs-c-cx.md)
