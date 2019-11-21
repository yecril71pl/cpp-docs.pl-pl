---
title: C++ type system
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
ms.openlocfilehash: 1f12f7505438dc995aaf8a045fd903488e9ff092
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246605"
---
# <a name="c-type-system"></a>C++ type system

The concept of *type* is very important in C++. Zwracana wartość każdej zmiennej, argumentu funkcji oraz funkcji musi mieć typ, aby mogła zostać skompilowana. Ponadto, kompilator niejawnie nadaje typ każdemu wyrażeniu (w tym wartości literału), zanim zostanie on oceniony. Some examples of types include **int** to store integral values, **double** to store floating-point values (also known as *scalar* data types), or the Standard Library class [std::basic_string](../standard-library/basic-string-class.md) to store text. You can create your own type by defining a **class** or **struct**. Typ określa wielkość pamięci, która zostanie zaalokowana dla zmiennej (lub wyniku wyrażenia), rodzaje wartości, które mogą być przechowywane w tej zmiennej, sposób interpretacji tych wartości (jako wzorców bajtów) oraz operacje, jakie mogą zostać na nich wykonane. Ten artykuł zawiera nieformalny przegląd głównych funkcji systemu typów C++.

## <a name="terminology"></a>Terminologia

**Variable**: The symbolic name of a quantity of data so that the name can be used to access the data it refers to throughout the scope of the code where it is defined. In C++, *variable* is generally used to refer to instances of scalar data types, whereas instances of other types are usually called *objects*.

**Object**: For simplicity and consistency, this article uses the term *object* to refer to any instance of a class or structure, and when it is used in the general sense includes all types, even scalar variables.

**POD type** (plain old data): This informal category of data types in C++ refers to types that are scalar (see the Fundamental types section) or are *POD classes*. Klasa POD nie ma żadnych statycznych składowych danych, które nie są również POD, i nie ma zdefiniowanych przez użytkownika konstruktorów, zdefiniowanych przez użytkownika destruktorów ani zdefiniowanych przez użytkownika operatorów przypisania. Klasa POD nie ma też żadnych funkcji wirtualnych, nie ma klasy podstawowej ani żadnych prywatnych lub chronionych niestatycznych składowych danych. Typy POD są często używane do wymiany danych zewnętrznych, na przykład przy użyciu modułu napisanego w języku C (który ma tylko typy POD).

## <a name="specifying-variable-and-function-types"></a>Określanie typów zmiennych i funkcji

C++ is a *strongly typed* language and it is also *statically-typed*; every object has a type and that type never changes (not to be confused with static data objects).
**When you declare a variable** in your code, you must either specify its type explicitly, or use the **auto** keyword to instruct the compiler to deduce the type from the initializer.
**When you declare a function** in your code, you must specify the type of each argument and its return value, or **void** if no value is returned by the function. Wyjątek występuje podczas korzystania z szablonów funkcji, które pozwalają na argumenty dowolnego typu.

Po pierwszym zdeklarowaniu zmiennej nie można później zmienić jej typu. Możesz jednak skopiować wartość zmiennej lub wartość zwracaną przez funkcję do innej zmiennej innego typu. Such operations are called *type conversions*, which are sometimes necessary but are also potential sources of data loss or incorrectness.

Kiedy deklarujesz zmienną typu POD, stanowczo zalecamy jej inicjalizację, co oznacza nadanie jej początkowej wartości. Dopóki zmienna nie zostanie zainicjalizowana, ma ona wartość „śmieciową”, składającą się z bitów, które poprzednio znajdowały się w tej lokalizacji pamięci. Jest to ważny aspekt C++ warty zapamiętania, szczególnie jeżeli praca odbywała się wcześniej w innym języku, który automatycznie obsługuje inicjalizację. Gdy deklarujesz zmienną typu innego niż klasa POD, konstruktor obsługuje inicjalizację.

Poniższy przykład pokazuje kilka prostych deklaracji zmiennych z opisami każdej z nich. W przykładzie pokazano również, jak kompilator używa informacji o typie, aby umożliwiać lub uniemożliwiać pewne kolejne operacje na zmiennej.

```cpp
int result = 0;              // Declare and initialize an integer.
double coefficient = 10.8;   // Declare and initialize a floating
                             // point value.
auto name = "Lady G.";       // Declare a variable and let compiler
                             // deduce the type.
auto address;                // error. Compiler cannot deduce a type
                             // without an intializing value.
age = 12;                    // error. Variable declaration must
                             // specify a type or use auto!
result = "Kenny G.";         // error. Can’t assign text to an int.
string result = "zero";      // error. Can’t redefine a variable with
                             // new type.
int maxValue;                // Not recommended! maxValue contains
                             // garbage bits until it is initialized.
```

## <a name="fundamental-built-in-types"></a>Podstawowe (wbudowane) typy

W odróżnieniu do innych języków, C++ nie ma uniwersalnego typu bazowego, z którego wywodzą się wszystkie inne typy. The language includes many *fundamental types*, also known as *built-in types*. This includes numeric types such as **int**, **double**, **long**, **bool**, plus the **char** and **wchar_t** types for ASCII and UNICODE characters, respectively. Most fundamental types (except **bool**, **double**, **wchar_t** and related types) all have unsigned versions, which modify the range of values that the variable can store. For example, an **int**, which stores a 32-bit signed integer, can represent a value from -2,147,483,648 to 2,147,483,647. An **unsigned int**, which is also stored as 32-bits, can store a value from 0 to 4,294,967,295. Całkowita liczba możliwych wartości w każdym przypadku jest taka sama, zmienia się tylko zakres.

Podstawowe typy są rozpoznawane przez kompilator, który posiada wbudowane reguły rządzące tym, jakie operacje można na nich wykonywać i jak mogą być konwertowane na inne typy podstawowe. For a complete list of built-in types and their size and numeric limits, see [Fundamental Types](../cpp/fundamental-types-cpp.md).

Na poniższej ilustracji przedstawiono względne wielkości typów wbudowanych:

![Size in bytes of built&#45;in types](../cpp/media/built-intypesizes.png "Size in bytes of built&#45;in types")

Poniższa tabela wymienia najczęściej używane typy podstawowe:

|Typ|Rozmiar|Komentarz|
|----------|----------|-------------|
|int|4 bajty|Wybór domyślny dla wartości całkowitych.|
|double|8 bytes|Wybór domyślny dla wartości zmiennopozycyjnych.|
|bool|1 bajt|Przedstawia wartości, które mogą być prawdziwe lub fałszywe.|
|char|1 bajt|Używaj dla znaków ASCII w starszych ciągach typu C lub obiektach std::string, które nigdy nie będą musiały zostać skonwertowane na UNICODE.|
|wchar_t|2 bytes|Przedstawia wartości znaku „szerokiego”, które mogą być zakodowane w formacie UNICODE (UTF-16 w systemie Windows, inne systemy operacyjne mogą się różnić). This is the character type that is used in strings of type `std::wstring`.|
|unsigned&nbsp;char|1 bajt|C++ has no built-in `byte` type.  Używaj unsigned char, aby reprezentować wartość bajtową.|
|unsigned int|4 bajty|Wybór domyślny dla flag bitowych.|
|long long|8 bytes|Przedstawia bardzo duże wartości całkowitoliczbowe.|

## <a name="the-void-type"></a>Typ void (pusty).

The **void** type is a special type; you cannot declare a variable of type **void**, but you can declare a variable of type __void \*__ (pointer to **void**), which is sometimes necessary when allocating raw (un-typed) memory. However, pointers to **void** are not type-safe and generally their use is strongly discouraged in modern C++. In a function declaration, a **void** return value means that the function does not return a value; this is a common and acceptable use of **void**. While the C language required functions that have zero parameters to declare **void** in the parameter list, for example, `fou(void)`, this practice is discouraged in modern C++ and should be declared `fou()`. For more information, see [Type Conversions and Type Safety](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="const-type-qualifier"></a>kwalifikator typu const

Dowolny wbudowany lub zdefiniowany przez użytkownika typ może być zakwalifikowany według słowa kluczowego const. Additionally, member functions may be **const**-qualified and even **const**-overloaded. The value of a **const** type cannot be modified after it is initialized.

```cpp

const double PI = 3.1415;
PI = .75 //Error. Cannot modify const variable.
```

The **const** qualifier is used extensively in function and variable declarations and "const correctness" is an important concept in C++; essentially it means to use **const** to guarantee, at compile time, that values are not modified unintentionally. For more information, see [const](../cpp/const-cpp.md).

A **const** type is distinct from its non-const version; for example, **const int** is a distinct type from **int**. You can use the C++ **const_cast** operator on those rare occasions when you must remove *const-ness* from a variable. For more information, see [Type Conversions and Type Safety](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="string-types"></a>Typy ciągu

Strictly speaking, the C++ language has no built-in string type; **char** and **wchar_t** store single characters - you must declare an array of these types to approximate a string, adding a terminating null value (for example, ASCII `'\0'`) to the array element one past the last valid character (also called a *C-style string*). Ciągi stylu C wymagały znacznie więcej kodu lub korzystania z funkcji zewnętrznej biblioteki obsługującej ciągi. But in modern C++, we have the Standard Library types `std::string` (for 8-bit **char**-type character strings) or `std::wstring` (for 16-bit **wchar_t**-type character strings). These C++ Standard Library containers can be thought of as native string types because they are part of the standard libraries that are included in any compliant C++ build environment. Simply use the `#include <string>` directive to make these types available in your program. (If you are using MFC or ATL, the CString class is also available, but is not part of the C++ standard.) The use of null-terminated character arrays (the C-style strings previously mentioned) is strongly discouraged in modern C++.

## <a name="user-defined-types"></a>Typy definiowane przez użytkownika

When you define a **class**, **struct**, **union**, or **enum**, that construct is used in the rest of your code as if it were a fundamental type. Zajmuje znany obszar w pamięci, a niektóre zasady sposobu, w jaki można go używać, dotyczą sprawdzania w czasie kompilacji i w trakcie uruchomienia, przez cały okres istnienia programu. Główne różnice między głównymi wbudowanymi typami a typami definiowanymi przez użytkownika są następujące:

- Kompilator nie ma wbudowanej wiedzy o typie zdefiniowanym przez użytkownika. It learns of the type when it first encounters the definition during the compilation process.

- Ty określasz, jakie operacje mogą zostać przeprowadzone na typie i jak może on zostać przekonwertowany do innych typów, definiując (przez przeciążenie) odpowiednie operatory, albo jako funkcje składowych, albo jako funkcje, które nie są składowymi. For more information, see [Function Overloading](function-overloading.md)

## <a name="pointer-types"></a>Typy wskaźnika

Dating back to the earliest versions of the C language, C++ continues to let you declare a variable of a pointer type by using the special declarator `*` (asterisk). Typ wskaźnika przechowuje adres lokalizacji w pamięci, gdzie jest przechowywana rzeczywista wartość danych. In modern C++, these are referred to as *raw pointers*, and are accessed in your code through special operators `*` (asterisk) or `->` (dash with greater-than). This is called *dereferencing*, and which one that you use depends on whether you are dereferencing a pointer to a scalar or a pointer to a member in an object. Praca z typami wskaźników od dawna jest jednym z najtrudniejszych i najbardziej dezorientujących aspektów tworzenia programów w C i C++. This section outlines some facts and practices to help use raw pointers if you want to, but in modern C++ it’s no longer required (or recommended) to use raw pointers for object ownership at all, due to the evolution of the [smart pointer](../cpp/smart-pointers-modern-cpp.md) (discussed more at the end of this section). Nadal jest użyteczne i bezpieczne używanie surowych wskaźników do obserwacji obiektów, ale jeśli musisz użyć ich do własności obiektu, należy to zrobić z ostrożnością i po bardzo starannym rozważeniu sposobu, w jaki obiekty przez nie posiadane są tworzone i niszczone.

Pierwszą rzeczą, którą należy wiedzieć przy deklarowaniu zmiennej surowego wskaźnika, jest to, że zmienna przydzieli tylko pamięć, która jest niezbędna do przechowania adresu lokalizacji pamięci, do którego odwoła się wskaźnik po wyłuskaniu. Allocation of the memory for the data value itself (also called *backing store*) is not yet allocated. Innymi słowy, przez zadeklarowanie zmiennej surowego wskaźnika tworzysz zmienną adresu pamięci, a nie zmienną rzeczywistych danych. \Wyłuskanie zmiennej wskaźnika przed upewnieniem się, że zawiera ona prawidłowy adres magazynu zapasowego, spowoduje niezdefiniowane zachowanie (zwykle błąd krytyczny) w programie. Poniższy przykład przedstawia ten rodzaj błędu:

```cpp
int* pNumber;       // Declare a pointer-to-int variable.
*pNumber = 10;      // error. Although this may compile, it is
                    // a serious error. We are dereferencing an
                    // uninitialized pointer variable with no
                    // allocated memory to point to.
```

Przykład wyłuskuje typ wskaźnika, bez przydzielania pamięci na przechowywanie rzeczywistych danych całkowitoliczbowych lub prawidłowego przypisanego adresu pamięci. Poniższy kod poprawia te błędy:

```cpp
    int number = 10;          // Declare and initialize a local integer
                              // variable for data backing store.
    int* pNumber = &number;   // Declare and initialize a local integer
                              // pointer variable to a valid memory
                              // address to that backing store.
...
    *pNumber = 41;            // Dereference and store a new value in
                              // the memory pointed to by
                              // pNumber, the integer variable called
                              // "number". Note "number" was changed, not
                              // "pNumber".
```

The corrected code example uses local stack memory to create the backing store that `pNumber` points to. Dla uproszczenia używamy podstawowego typu. In practice, the backing store for pointers are most often user-defined types that are dynamically-allocated in an area of memory called the *heap* (or *free store*) by using a **new** keyword expression (in C-style programming, the older `malloc()` C runtime library function was used). Once allocated, these variables are usually referred to as objects, especially if they are based on a class definition. Memory that is allocated with **new** must be deleted by a corresponding **delete** statement (or, if you used the `malloc()` function to allocate it, the C runtime function `free()`).

However, it is easy to forget to delete a dynamically-allocated object- especially in complex code, which causes a resource bug called a *memory leak*. Z tego powodu zdecydowanie odradza się stosowanie surowych wskaźników w nowoczesnym języku C++. It is almost always better to wrap a raw pointer in a [smart pointer](../cpp/smart-pointers-modern-cpp.md), which will automatically release the memory when its destructor is invoked (when the code goes out of scope for the smart pointer); by using smart pointers you virtually eliminate a whole class of bugs in your C++ programs. In the following example, assume `MyClass` is a user-defined type that has a public method `DoSomeWork();`

```cpp
void someFunction() {
    unique_ptr<MyClass> pMc(new MyClass);
    pMc->DoSomeWork();
}
  // No memory leak. Out-of-scope automatically calls the destructor
  // for the unique_ptr, freeing the resource.
```

For more information about smart pointers, see [Smart Pointers](../cpp/smart-pointers-modern-cpp.md).

For more information about pointer conversions, see [Type Conversions and Type Safety](../cpp/type-conversions-and-type-safety-modern-cpp.md).

For more information about pointers in general, see [Pointers](../cpp/pointers-cpp.md).

## <a name="windows-data-types"></a>Typy danych Windows

In classic Win32 programming for C and C++, most functions use Windows-specific typedefs and #define macros (defined in `windef.h`) to specify the types of parameters and return values. These Windows data types are mostly just special names (aliases) given to C/C++ built-in types. For a complete list of these typedefs and preprocessor definitions, see [Windows Data Types](/windows/win32/WinProg/windows-data-types). Niektóre z tych definicji typów, takie jak HRESULT i LCID, są użyteczne i opisowe. Inne, takie jak INT, nie mają specjalnego znaczenia i są po prostu aliasami dla podstawowych typów C++. Inne typy danych systemu Windows mają nazwy pochodzące z czasów programowania w C i procesorów 16-bitowych. Nie mają one żadnego celu ani znaczenia w przypadku nowoczesnego sprzętu lub systemu operacyjnego. There are also special data types associated with the Windows Runtime Library, listed as [Windows Runtime base data types](/windows/win32/WinRT/base-data-types). W nowoczesnym C++, ogólną wytyczną jest preferowanie typów podstawowych języka C++, chyba że typ Windows komunikuje jakieś dodatkowe znaczenie o sposobie interpretowania wartości.

## <a name="more-information"></a>Więcej informacji

Aby uzyskać więcej informacji dotyczących typu systemu C++, zobacz następujące tematy.

|||
|-|-|
|[Typy wartości](../cpp/value-types-modern-cpp.md)|Describes *value types* along with issues relating to their use.|
|[Type Conversions and Type Safety](../cpp/type-conversions-and-type-safety-modern-cpp.md)|Opisuje typowe problemy przy konwersji typu i pokazuje, jak ich unikać.|

## <a name="see-also"></a>Zobacz także

[Welcome back to C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
