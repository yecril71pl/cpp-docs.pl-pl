---
title: Tablice (C + +/ CLI i C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 29f84515bfa802af8d6463d34de9b6717c8df044
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061329"
---
# <a name="arrays-ccli-and-ccx"></a>Tablice (C + +/ CLI i C + +/ CX)

`Platform::Array<T>` Typ w języku C + +/ CX lub **tablicy** — słowo kluczowe w języku C + +/ CLI, deklaruje tablicę określonego typu i wartości początkowej.

## <a name="all-platforms"></a>Wszystkie platformy

Tablica musi być zadeklarowany za pomocą modyfikatora uchwytu do obiektu (^) po zamykającego nawiasu ostrego (>) w deklaracji.
Liczba elementów w tablicy nie jest częścią tego typu. Jednej zmiennej tablicy mogą odwoływać się do tablic o różnych rozmiarach.

W przeciwieństwie do standardowego języka C++ Tworzenie indeksów dolnych nie jest synonimem arytmetyka wskaźnika i nie jest przemiennego.

Aby uzyskać więcej informacji na temat tablic zobacz:

- [Instrukcje: korzystanie z tablic w języku C++/interfejsie wiersza polecenia](../dotnet/how-to-use-arrays-in-cpp-cli.md)

- [Listy zmiennych argumentów (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Tablice są elementami członkowskimi `Platform` przestrzeni nazw. Tablice mogą być tylko jednowymiarowa.

### <a name="syntax"></a>Składnia

W pierwszym przykładzie składni użyto **ref nowe** agregacji — słowo kluczowe do przydzielania tablicy. Drugi przykład deklaruje lokalnej tablicy.

```cpp
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]

[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*Kwalifikatory*<br/>
(Opcjonalnie) Co najmniej jeden z tych specyfikatory klasy magazynowania: [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [statyczne](../cpp/static-members-cpp.md).

*Typ tablicy*<br/>
Typ zmiennej tablicowej. Prawidłowe typy to klasy środowiska wykonawczego Windows i typów podstawowych, klasy ref i struktury, klasy wartości i struktury i natywnymi wskaźnikami (`type*`).

*Ranga*<br/>
(Opcjonalnie) Liczba wymiarów tablicy. Musi mieć wartość 1.

*Identyfikator*<br/>
Nazwa zmiennej tablicy.

*typ inicjalizacji*<br/>
Typ wartości, które inicjalizacji tablicy. Zazwyczaj *typ tablicy* i *typ inicjalizacji* tego samego typu. Jednak może być inny, jeśli istnieje konwersja z typów *typ inicjalizacji* do *typ tablicy*— na przykład, jeśli *typ inicjalizacji* jest tworzony na podstawie *typ tablicy*.

*listy inicjowania*<br/>
(Opcjonalnie) Rozdzielana przecinkami lista wartości w nawiasach klamrowych, które zainicjować elementy tablicy. Na przykład jeśli *ranga rozmiar listy* zostały `(3)`, która deklaruje tablicę jednowymiarową 3 elementów *listy inicjowania* może być `{1,2,3}`.

### <a name="remarks"></a>Uwagi

Można wykrywać w czasie kompilacji, czy typ jest tablicą zliczonych odwołań z `__is_ref_array(type)`. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

### <a name="examples"></a>Przykłady

Poniższy przykład tworzy jednowymiarową tablicę, która zawiera 100 elementów.

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

W pierwszym przykładzie składni użyto **gcnew** — słowo kluczowe do przydzielania tablicy. Drugi przykład deklaruje lokalnej tablicy.

```cpp
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]

[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*Kwalifikatory*<br/>
(Opcjonalnie) Co najmniej jeden z tych specyfikatory klasy magazynowania: [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [statyczne](../cpp/static-members-cpp.md).

*Typ tablicy*<br/>
Typ zmiennej tablicowej. Prawidłowe typy to klasy środowiska wykonawczego Windows i typów podstawowych, klasy i struktury, klasy wartości i struktury odwołania, natywnymi wskaźnikami (`type*`) i natywnych typów POD (zwykłe stare dane).

*Ranga*<br/>
(Opcjonalnie) Liczba wymiarów tablicy. Wartość domyślna to 1; wartość maksymalna to 32. Każdy wymiar tablicy jest tablicą.

*Identyfikator*<br/>
Nazwa zmiennej tablicy.

*typ inicjalizacji*<br/>
Typ wartości, które inicjalizacji tablicy. Zazwyczaj *typ tablicy* i *typ inicjalizacji* tego samego typu. Jednak może być inny, jeśli istnieje konwersja z typów *typ inicjalizacji* do *typ tablicy*— na przykład, jeśli *typ inicjalizacji* jest tworzony na podstawie *typ tablicy*.

*Ranga rozmiar listy*<br/>
Rozdzielana przecinkami lista rozmiar każdego wymiaru tablicy. Alternatywnie Jeśli *listy inicjowania* parametr jest określony, kompilator może wywnioskować rozmiaru każdego wymiaru i *ranga rozmiar listy* można pominąć.

*listy inicjowania*<br/>
(Opcjonalnie) Rozdzielana przecinkami lista wartości w nawiasach klamrowych, które zainicjować elementy tablicy. Lub rozdzielaną przecinkami listę zagnieżdżonych *listy inicjowania* elementy, które inicjowania elementów w tablicy wielowymiarowej.

Na przykład jeśli *ranga rozmiar listy* zostały `(3)`, która deklaruje tablicę jednowymiarową 3 elementów *listy inicjowania* może być `{1,2,3}`. Jeśli *ranga rozmiar listy* zostały `(3,2,4)`, która deklaruje tablicę trójwymiarową 3 elementy pierwszego wymiaru, 2 elementów w drugim i 4 elementy w trzecim *listy inicjowania* może to być `{{1,2,3},{0,0},{-5,10,-21,99}}`.)

### <a name="remarks"></a>Uwagi

**Tablica** znajduje się w [platformy, domyślna i cli przestrzenie nazw](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) przestrzeni nazw.

Np. standard C++ indeksy tablicy zaczynają się od zera, a tablica jest indeksowanych przy użyciu nawiasy kwadratowe ([]). W przeciwieństwie do standardowego języka C++ indeksy tablicy wielowymiarowej są określone na liście indeksów dla każdego wymiaru zamiast zestawu operatorów kwadratowym ([]) dla każdego wymiaru. Na przykład *identyfikator*[*index1*, *index2*] zamiast *identyfikator*[*index1*] [ *index2*].

Dziedzicz wszystkich zarządzanych tablic `System::Array`. Wszelkie metody lub właściwości `System::Array` mogą być stosowane bezpośrednio do zmiennej tablicowej.

Podczas przydzielania tablicy którego typ elementu to wskaźnik-do zarządzanej klasy elementy są inicjowane przez 0.

Podczas przydzielania tablicy którego typ elementu to typ wartości `V`, domyślnego konstruktora dla `V` jest stosowana do każdego elementu tablicy. Aby uzyskać więcej informacji, zobacz [.NET Framework odpowiedniki typów natywnych języka C++ (C + +/ CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md).

W czasie kompilacji może wykryć, czy typ jest wspólnej tablicy środowiska uruchomieniowego (języka wspólnego CLR) języka przy użyciu `__is_ref_array(type)`. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład tworzy jednowymiarową tablicę, która zawiera 100 elementów i trójwymiarowej tablicy, która ma 3 elementy w pierwszym wymiarze, 5 elementów, w drugim i 6 elementów w trzecim.

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

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](../windows/component-extensions-for-runtime-platforms.md)