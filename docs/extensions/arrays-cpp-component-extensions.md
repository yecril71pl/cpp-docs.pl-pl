---
title: Tablice (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
helpviewer_keywords:
- array keyword [C++]
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
ms.openlocfilehash: 814be57caafed117a1403105d46326ac53682578
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500888"
---
# <a name="arrays-ccli-and-ccx"></a>Tablice (C++/CLI i C++/CX)

`Platform::Array<T>`Typ w języku c++/CX lub słowo kluczowe **Array** w c++/CLI, deklaruje tablicę określonego typu i wartość początkową.

## <a name="all-platforms"></a>Wszystkie platformy

Tablica musi być zadeklarowana przy użyciu modyfikatora dojścia do obiektu (^) po zamykającym nawiasie ostrym (>) w deklaracji.
Liczba elementów tablicy nie jest częścią typu. Jedna zmienna tablicowa może odwoływać się do tablic o różnych rozmiarach.

W przeciwieństwie do standardowego języka C++, indeksy dolne nie są synonimem dla operacji arytmetycznych wskaźnika i nie są komutatywna.

Aby uzyskać więcej informacji na temat tablic, zobacz:

- [Instrukcje: korzystanie z tablic w języku C++/CLI](../dotnet/how-to-use-arrays-in-cpp-cli.md)

- [Listy zmiennych argumentów (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Tablice są elementami członkowskimi `Platform` przestrzeni nazw. Tablice mogą być tylko jednowymiarowe.

### <a name="syntax"></a>Składnia

Pierwszy przykład składni używa **ref new** Aggregate słowo kluczowe do przydzielenia tablicy. Drugi przykład deklaruje tablicę lokalną.

```cpp
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]

[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*kwalifikatory*<br/>
Obowiązkowe Co najmniej jeden specyfikator klasy magazynu: [modyfikowalny](../cpp/mutable-data-members-cpp.md), [nietrwały](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/extern-cpp.md), [statyczny](../cpp/static-members-cpp.md).

*typ tablicy*<br/>
Typ zmiennej tablicowej. Prawidłowe typy to klasy środowisko wykonawcze systemu Windows i typy podstawowe, klasy referencyjne i struktury, klasy wartości i struktury oraz wskaźniki natywne ( `type*` ).

*stopni*<br/>
Obowiązkowe Liczba wymiarów tablicy. Musi mieć 1.

*identyfikatora*<br/>
Nazwa zmiennej tablicowej.

*Typ inicjalizacji*<br/>
Typ wartości, które inicjują tablicę. Typowo, typ *tablicy* i *Typ inicjalizacji* są tego samego typu. Jednak typy mogą być różne, jeśli istnieje konwersja z *typu inicjalizacji* na *typ Array*— na przykład, jeśli *Typ inicjalizacji* jest pochodną *typu Array*.

*Lista inicjowania*<br/>
Obowiązkowe Rozdzielana przecinkami lista wartości w nawiasach klamrowych, które inicjują elementy tablicy. Na przykład, jeśli określono *rangę size-list* `(3)` , która deklaruje tablicę jednowymiarową zawierającą 3 elementy, *Lista inicjowania* może być `{1,2,3}` .

### <a name="remarks"></a>Uwagi

Możesz wykryć w czasie kompilacji, niezależnie od tego, czy typ jest tablicą zliczaną z odwołania `__is_ref_array(type)` . Aby uzyskać więcej informacji, zobacz [Obsługa kompilatora dla cech typu](compiler-support-for-type-traits-cpp-component-extensions.md).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

### <a name="examples"></a>Przykłady

Poniższy przykład tworzy tablicę jednowymiarową, która ma elementy 100.

```cpp
// cwr_array.cpp
// compile with: /ZW
using namespace Platform;
ref class MyClass {};
int main() {
   // one-dimensional array
   Array<MyClass^>^ My1DArray = ref new Array<MyClass^>(100);
   My1DArray[99] = ref new MyClass();
}
```

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="syntax"></a>Składnia

Pierwszy przykład składni używa słowa kluczowego **gcnew** , aby przydzielić tablicę. Drugi przykład deklaruje tablicę lokalną.

```cpp
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]

[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*kwalifikatory*<br/>
Obowiązkowe Co najmniej jeden specyfikator klasy magazynu: [modyfikowalny](../cpp/mutable-data-members-cpp.md), [nietrwały](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/extern-cpp.md), [statyczny](../cpp/static-members-cpp.md).

*typ tablicy*<br/>
Typ zmiennej tablicowej. Prawidłowe typy to środowisko wykonawcze systemu Windows klas i typy podstawowe, klasy referencyjne i struktury, klasy wartości i struktury, wskaźniki natywne ( `type*` ) i natywne (zwykłe stare dane).

*stopni*<br/>
Obowiązkowe Liczba wymiarów tablicy. Wartość domyślna to 1; wartość maksymalna to 32. Każdy wymiar tablicy jest samym tablicą.

*identyfikatora*<br/>
Nazwa zmiennej tablicowej.

*Typ inicjalizacji*<br/>
Typ wartości, które inicjują tablicę. Typowo, typ *tablicy* i *Typ inicjalizacji* są tego samego typu. Jednak typy mogą być różne, jeśli istnieje konwersja z *typu inicjalizacji* na *typ Array*— na przykład, jeśli *Typ inicjalizacji* jest pochodną *typu Array*.

*Ranga-rozmiar-lista*<br/>
Rozdzielana przecinkami lista rozmiarów każdego wymiaru w tablicy. Alternatywnie, jeśli określono parametr z *listą inicjalizacji* , kompilator może wywnioskować rozmiar każdego wymiaru, a *Lista rangi o rozmiarze* może zostać pominięta.

*Lista inicjowania*<br/>
Obowiązkowe Rozdzielana przecinkami lista wartości w nawiasach klamrowych, które inicjują elementy tablicy. Lub rozdzielana przecinkami lista zagnieżdżonych elementów *listy inicjalizacji* , które inicjują elementy w tablicy wielowymiarowej.

Na przykład, jeśli określono *rangę size-list* `(3)` , która deklaruje tablicę jednowymiarową zawierającą 3 elementy, *Lista inicjowania* może być `{1,2,3}` . Jeśli określono *rangę size* -list `(3,2,4)` , która deklaruje trójwymiarową tablicę 3 elementów w pierwszym wymiarze, dwa elementy w drugim, a 4 elementów z trzeciego, może być na *liście inicjalizacji* `{{1,2,3},{0,0},{-5,10,-21,99}}` .

### <a name="remarks"></a>Uwagi

**Tablica** znajduje się w przestrzeni nazw [platform, Default i CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md) .

Podobnie jak w przypadku standardowego języka C++, indeksy tablicy są zależne od zera, a tablica jest poddana indeksem za pomocą nawiasów kwadratowych ([]). W przeciwieństwie do standardowego języka C++, indeksy wielowymiarowej tablicy są określone na liście indeksów dla każdego wymiaru zamiast zestawu operatorów kwadratowych ([]) dla każdego wymiaru. Na przykład *Identyfikator*[*index1*, *index2*] zamiast *identyfikatora*[*index1*] [ *index2*].

Wszystkie zarządzane tablice dziedziczą z `System::Array` . Każdą metodę lub właściwość `System::Array` można zastosować bezpośrednio do zmiennej tablicowej.

Po przydzieleniu tablicy, której typ elementu jest wskaźnikiem do klasy zarządzanej, elementy są zainicjowane przez 0.

Po przydzieleniu tablicy, której typ elementu jest typem wartości `V` , Konstruktor domyślny `V` jest stosowany do każdego elementu tablicy. Aby uzyskać więcej informacji, zobacz [.NET Framework odpowiedników typów natywnych języka c++ (c++/CLI)](../dotnet/managed-types-cpp-cli.md#dotnet).

W czasie kompilacji można wykryć, czy typ jest tablicą środowiska uruchomieniowego języka wspólnego (CLR) za pomocą `__is_ref_array(type)` . Aby uzyskać więcej informacji, zobacz [Obsługa kompilatora dla cech typu](compiler-support-for-type-traits-cpp-component-extensions.md).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład tworzy tablicę jednowymiarową, która ma elementy 100 i trójwymiarową tablicę, która ma 3 elementy w pierwszym wymiarze, 5 elementów w drugim i 6 elementów w trzecim.

```cpp
// clr_array.cpp
// compile with: /clr
ref class MyClass {};
int main() {
   // one-dimensional array
   array<MyClass ^> ^ My1DArray = gcnew array<MyClass ^>(100);
   My1DArray[99] = gcnew MyClass();

   // three-dimensional array
   array<MyClass ^, 3> ^ My3DArray = gcnew array<MyClass ^, 3>(3, 5, 6);
   My3DArray[0,0,0] = gcnew MyClass();
}
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)
