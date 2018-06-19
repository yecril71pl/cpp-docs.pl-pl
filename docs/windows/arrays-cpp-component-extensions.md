---
title: Tablice (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
- declaring arrays, about declaring arrays
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a17649402fa6ebe9c98d768badcf36e5700f5b75
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862725"
---
# <a name="arrays-c-component-extensions"></a>Tablice (C++ Component Extensions)
`Platform::Array<T>` Typu w języku C + +/ CX, lub `array` słów kluczowych w języku C + +/ CLI, deklaruje tablicę określonego typu i wartości początkowej.  
  
## <a name="all-platforms"></a>Wszystkie platformy  
 Tablica musi być zadeklarowany za pomocą modyfikatora uchwyt do obiektu (^) po zamykającego nawiasu ostrego (>) w deklaracji.  
 Liczba elementów w tablicy nie jest częścią typu. Jednej zmiennej tablicy mogą odwoływać się do tablic o różnych rozmiarach.  
  
 W przeciwieństwie do standardu C++ Tworzenie indeksów dolnych synonimem arytmetyka wskaźnika nie jest i nie jest przemienne.  
  
 Aby uzyskać więcej informacji dotyczących tablic zobacz:  
  
-   [Instrukcje: korzystanie z tablic w języku C++/interfejsie wiersza polecenia](../dotnet/how-to-use-arrays-in-cpp-cli.md)  
    
-   [Listy zmiennych argumentów (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Tablice są elementami członkowskimi `Platform` przestrzeni nazw. Tablice mogą być tylko jednowymiarowa.  
  
### <a name="syntax"></a>Składnia  
  
 W pierwszym przykładzie składni `ref new` agregacji — słowo kluczowe można przydzielić tablicy. Drugi przykład deklaruje lokalnej tablicy.  
  
```  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]  
  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *Kwalifikatory* [opcjonalnie]  
 Co najmniej jeden z tych specyfikatory klas magazynu: [modyfikowalną](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [static](../cpp/static-members-cpp.md).  
  
 `array-type`  
 Typ zmiennej tablicy. Prawidłowe typy to klasy środowiska wykonawczego systemu Windows i typów podstawowych, klas referencyjnych i struktury wartość klasy i struktury i wskaźników natywnych (`type*`).  
  
 `rank` [opcjonalnie]  
 Liczba wymiarów tablicy. Musi mieć wartość 1.  
  
 `identifier`  
 Nazwa zmiennej tablicy.  
  
 `initialization-type`  
 Typ wartości, które inicjowanie tablicy. Zazwyczaj `array-type` i `initialization-type` są tego samego typu. Jednak typy mogą być różne, jeśli brak konwersji z `initialization-type` do `array-type`— na przykład, jeśli `initialization-type` jest pochodną `array-type`.  
  
 `initialization-list` [opcjonalnie]  
 Rozdzielana przecinkami lista wartości w nawiasach klamrowych, które zainicjować elementów tablicy. Na przykład jeśli `rank-size-list` zostały `(3)`, który deklaruje tablicą jednowymiarową 3 elementy `initialization list` może być `{1,2,3}`.  
  
### <a name="remarks"></a>Uwagi  
  
 Można wykrywać w czasie kompilacji, czy typ jest tablicą zliczane odwołanie z `__is_ref_array(type)`. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
### <a name="examples"></a>Przykłady  
 Poniższy przykład tworzy Jednowymiarowa tablica, która zawiera 100 elementów.  
  
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
  
 W pierwszym przykładzie składni `gcnew` — słowo kluczowe można przydzielić tablicy. Drugi przykład deklaruje lokalnej tablicy.  
  
```  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]  
  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *Kwalifikatory* [opcjonalnie]  
 Co najmniej jeden z tych specyfikatory klas magazynu: [modyfikowalną](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [static](../cpp/static-members-cpp.md).  
  
 `array-type`  
 Typ zmiennej tablicy. Prawidłowe typy to klasy środowiska wykonawczego systemu Windows i typów podstawowych, klas referencyjnych i struktur, wartość klasy i struktury, wskaźników natywnych (`type*`), a natywnych typów POD (zwykły starych danych).  
  
 `rank` [opcjonalnie]  
 Liczba wymiarów tablicy. Wartość domyślna to 1; wartość maksymalna to 32. Każdego wymiaru tablicy jest tablicą.  
  
 `identifier`  
 Nazwa zmiennej tablicy.  
  
 `initialization-type`  
 Typ wartości, które inicjowanie tablicy. Zazwyczaj `array-type` i `initialization-type` są tego samego typu. Jednak typy mogą być różne, jeśli brak konwersji z `initialization-type` do `array-type`— na przykład, jeśli `initialization-type` jest pochodną `array-type`.  
  
 `rank-size-list`  
 Rozdzielana przecinkami lista rozmiar każdego wymiaru tablicy. Alternatywnie Jeśli `initialization-list` parametr jest określony, kompilator może wywnioskować rozmiar każdego wymiaru i `rank-size-list` można pominąć. 
  
 `initialization-list` [opcjonalnie]  
 Rozdzielana przecinkami lista wartości w nawiasach klamrowych, które zainicjować elementów tablicy. Lub zagnieżdżone rozdzielana przecinkami lista *listy inicjowania* elementy, które zainicjować elementów w tablicy wielowymiarowej.  
  
 Na przykład jeśli `rank-size-list` zostały `(3)`, który deklaruje tablicą jednowymiarową 3 elementy `initialization list` może być `{1,2,3}`. Jeśli `rank-size-list` zostały `(3,2,4)`, który deklaruje jest tablicą trójwymiarową 3 elementów w pierwszym wymiarze, 2 elementy w ciągu sekundy i 4 w trzecim polu `initialization-list` może być `{{1,2,3},{0,0},{-5,10,-21,99}}`.)  
  
### <a name="remarks"></a>Uwagi  
  
 `array` Trwa [platformy, domyślna i cli przestrzenie nazw](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) przestrzeni nazw.  
  
 Podobnie jak standard C++ indeksy tablicy są liczony od zera, a jako jest tablicą przy użyciu nawiasy kwadratowe ([]). W przeciwieństwie do standardu C++ indeksy tablicy wielowymiarowej są określone w postaci listy indeksów dla każdego wymiaru zamiast zestaw operatorów kwadratowym ([]) dla każdego wymiaru. Na przykład *identyfikator*[*indeks1*, *index2*] zamiast *identyfikator*[*indeks1*] [ *index2*].  
  
 Wszystkie tablice zarządzane dziedziczyć `System::Array`. Wszystkie metody lub właściwości `System::Array` można zastosować bezpośrednio do zmiennej tablicy.  
  
 Gdy przydzielić tablicy o typie elementu jest wskaźnik-do zarządzanej klasy elementy są inicjowane przez 0.  
  
 Gdy przydzielić tablicy o typie elementu jest typem wartości `V`, domyślnego konstruktora dla `V` jest stosowana do każdego elementu tablicy. Aby uzyskać więcej informacji, zobacz [.NET Framework odpowiedniki typów natywnych języka C++ (C + +/ CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md).  
  
 W czasie kompilacji może wykryć, czy typ jest wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) tablicą zawierającą `__is_ref_array(type)`. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 Poniższy przykład tworzy Jednowymiarowa tablica, która zawiera 100 elementów i jest tablicą trójwymiarową zawierający 3 elementy w pierwszym wymiarze, 5 elementów w ciągu sekundy i 6 w trzecim polu.  
  
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
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)