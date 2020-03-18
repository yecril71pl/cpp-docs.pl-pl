---
title: '&lt;nowe operatory&gt; i wyliczenia'
ms.date: 11/04/2016
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
ms.openlocfilehash: a3fd5b825fe1eaf3a07d9d001f03b9d0c64ffa31
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419792"
---
# <a name="ltnewgt-operators-and-enums"></a>&lt;nowe operatory&gt; i wyliczenia

## <a name="op_align_val_t"></a>align_val_t enum

```cpp
enum class align_val_t : size_t {};
```

## <a name="op_delete"></a>Usuwanie operatora

Funkcja wywołana przez wyrażenie delete do cofnięcia przydziału magazynu dla poszczególnych obiektów.

```cpp
void operator delete(void* ptr) throw();
void operator delete(void *, void*) throw();
void operator delete(void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parametry

\ *PTR*
Wskaźnik, którego wartość ma być renderowana nieprawidłowa przez operację usuwania.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja jest wywoływana przez wyrażenie delete w celu renderowania wartości *PTR* jest nieprawidłowy. Program może zdefiniować funkcję z tą sygnaturą funkcji, która zastępuje domyślną wersję zdefiniowaną przez bibliotekę C++ standardową. Wymaganym zachowaniem jest zaakceptowanie wartości *PTR* o wartości null lub zwróconej przez wcześniejsze wywołanie [operatora new](../standard-library/new-operators.md#op_new)(**size_t**).

Domyślnym zachowaniem dla wartości null *PTR* jest brak. Każda inna wartość *PTR* musi być wartością zwracaną wcześniej przez wywołanie opisane wcześniej. Domyślnym zachowaniem dla takiej wartości niezerowej *PTR* jest odproszenie magazynu przydzielonego przez poprzednie wywołanie. Nie jest on określony w sekcji jakie warunki lub wszystkie odzyskiwane magazyny są przydzielone przez kolejne wywołanie do `operator new`(**size_t**) lub do dowolnej `calloc`( **size_t**), `malloc`( **size_t**) lub `realloc`( **void** <strong>\*</strong>, **size_t**).

Druga funkcja jest wywoływana przez wyrażenie usuwania umieszczania odpowiadające nowemu wyrażeniu formularza **New**( **std:: size_t**). Nic nie robi.

Trzecia funkcja jest wywoływana przez wyrażenie usuwania umieszczania odpowiadające nowemu wyrażeniu formularza **New**( **std:: size_t**, **conststd:: nothrow_t &** ). Program może zdefiniować funkcję z tą sygnaturą funkcji, która zastępuje domyślną wersję zdefiniowaną przez bibliotekę C++ standardową. Wymagane zachowanie polega na zaakceptowaniu wartości `ptr`, która ma wartość null lub która została zwrócona przez wcześniejsze wywołanie do `operator new`( **size_t**). Domyślnym zachowaniem jest oszacowanie **usuwania**(`ptr`).

### <a name="example"></a>Przykład

Zobacz [operator new](../standard-library/new-operators.md#op_new) dla przykładu, który używa **operatora delete**.

## <a name="op_delete_arr"></a>Usuwanie operatora []

Funkcja wywołana przez wyrażenie delete do dealokacji magazynu dla tablicy obiektów.

```cpp
void operator delete[](void* ptr) throw();
void operator delete[](void *, void*) throw();
void operator delete[](void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parametry

\ *PTR*
Wskaźnik, którego wartość ma być renderowana nieprawidłowa przez operację usuwania.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja jest wywoływana przez wyrażenie `delete[]`, aby renderować wartość *PTR* jest nieprawidłowa. Funkcja jest przemieszczenia, ponieważ program może zdefiniować funkcję z tą sygnaturą funkcji, która zastępuje domyślną wersję zdefiniowaną przez bibliotekę C++ standardową. Wymaganym zachowaniem jest zaakceptowanie wartości *PTR* o wartości null lub zwróconej przez wcześniejsze wywołanie [operatora new&#91;](../standard-library/new-operators.md#op_new_arr)(**size_t**). Domyślnym zachowaniem dla wartości null *PTR* jest brak. Każda inna wartość *PTR* musi być wartością zwracaną wcześniej przez wywołanie opisane wcześniej. Zachowanie domyślne dla takiej wartości, która *nie jest wartością null, ma* na celu odproszenie magazynu przydzielonego przez poprzednie wywołanie. Nie jest on określony w sekcji jakie warunki lub wszystkie odzyskiwane magazyny są przypisywane przez kolejne wywołanie [operatora new](../standard-library/new-operators.md#op_new)(**size_t**) lub do dowolnego `calloc`(**size_t**), `malloc`(**size_t**) lub `realloc`( **void** <strong>\*</strong>, **size_t**).

Druga funkcja jest wywoływana przez wyrażenie `delete[]` umieszczania odpowiadające wyrażeniu `new[]` formularza `new[]`(**std:: size_t**). Nic nie robi.

Trzecia funkcja jest wywoływana przez wyrażenie usuwania umieszczania odpowiadające wyrażeniem `new[]` formularza `new[]`( **std:: size_t**, **const std:: nothrow_t &** ). Program może zdefiniować funkcję z tą sygnaturą funkcji, która zastępuje domyślną wersję zdefiniowaną przez bibliotekę C++ standardową. Wymaganym zachowaniem jest zaakceptowanie wartości *PTR* o wartości null lub zwróconej przez wcześniejsze wywołanie operatora `new[]`(**size_t**). Domyślnym zachowaniem jest oszacowanie `delete[]`(`ptr`).

### <a name="example"></a>Przykład

Zobacz [operator new&#91; ](../standard-library/new-operators.md#op_new_arr) for przykłady użycia `operator delete[]`.

## <a name="op_new"></a>Nowy operator

Funkcja wywołana przez nowe wyrażenie do przydzielania pamięci dla pojedynczych obiektów.

```cpp
void* operator new(std::size_t count) throw(bad_alloc);
void* operator new(std::size_t count, const std::nothrow_t&) throw();
void* operator new(std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>Parametry

*liczba*\
Liczba bajtów magazynu do przydzielenia.

\ *PTR*
Wskaźnik, który ma zostać zwrócony.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do najmniejszego bajtu nowo przydzielonych magazynów. Lub *PTR*.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja jest wywoływana przez nowe wyrażenie, aby przydzielić `count` bajty magazynu odpowiednio wyrównane do reprezentowania dowolnego obiektu tego rozmiaru. Program może zdefiniować alternatywną funkcję za pomocą tej sygnatury funkcji, która zastępuje domyślną wersję zdefiniowaną C++ przez bibliotekę standardową, więc można ją przemieścić.

Wymagane zachowanie ma zwrócić wskaźnik o wartości niezerowej tylko wtedy, gdy magazyn może być przydzielony zgodnie z żądaniem. Każda taka alokacja daje wskaźnik do odłączenia magazynu z dowolnego innego przydzielonego magazynu. Kolejność i contiguity magazynu przydzielonego przez kolejne wywołania nie są określone. Początkowa przechowywana wartość jest nieokreślona. Zwrócony wskaźnik wskazuje początkową (najmniejszą liczbę bajtów) przydzieloną pamięć masową. Jeśli liczba jest równa zero, zwracana wartość nie jest porównywana z żadną inną wartością zwracaną przez funkcję.

Zachowaniem domyślnym jest wykonanie pętli. W obrębie pętli funkcja najpierw próbuje przydzielić żądany magazyn. Czy próba dotyczy wywołania `malloc`( **size_t**) nie została określona. Jeśli próba zakończy się pomyślnie, funkcja zwraca wskaźnik do przydzielonych magazynów. W przeciwnym razie funkcja wywołuje wydaną [nową procedurę obsługi](../standard-library/new-typedefs.md#new_handler). Jeśli wywołana funkcja zwraca, pętla powtarza się. Pętla kończy się, gdy próba przydzielenia żądanego magazynu zakończy się pomyślnie lub gdy wywołana funkcja nie zwraca.

Wymaganym zachowaniem nowego programu obsługi jest wykonanie jednej z następujących operacji:

- Udostępnienie większej ilości miejsca do magazynowania w celu przydzielenia, a następnie zwrócenia.

- Wywołaj metodę **Abort** lub **Exit**(`int`).

- Zgłoś obiekt typu **bad_alloc.**

Domyślnym zachowaniem [nowego programu obsługi](../standard-library/new-typedefs.md#new_handler) jest wygenerowanie obiektu typu `bad_alloc`. Wskaźnik o wartości null oznacza domyślny nowy program obsługi.

Kolejność i contiguity magazynu przydzielonego przez kolejne wywołania do `operator new`(**size_t**) nie są określone, ponieważ są to wartości początkowe przechowywane w tym miejscu.

Druga funkcja jest wywoływana przez nowe wyrażenie umieszczania, aby przydzielić `count` bajty magazynu odpowiednio wyrównane do reprezentowania dowolnego obiektu tego rozmiaru. Program może zdefiniować alternatywną funkcję za pomocą tej sygnatury funkcji, która zastępuje domyślną wersję zdefiniowaną C++ przez bibliotekę standardową, więc można ją przemieścić.

Domyślnym zachowaniem jest zwrócenie `operator new`(`count`), jeśli ta funkcja się powiedzie. W przeciwnym razie zwraca wskaźnik o wartości null.

Trzecia funkcja jest wywoływana przez **nowe** wyrażenie umieszczania w formularzu **New** ( *args*) T. W tym miejscu *argumenty* składają się z pojedynczego wskaźnika obiektu. Może to być przydatne w przypadku konstruowania obiektu pod znanym adresem. Funkcja zwraca wartość *PTR*.

Aby zwolnić magazyn przydzielony przez **operator new**, [operator wywołania Delete](../standard-library/new-operators.md#op_delete).

Aby uzyskać informacje o zgłaszaniu lub nierzucaniu zachowań nowych, zobacz [Operatory New i DELETE](../cpp/new-and-delete-operators.md).

### <a name="example"></a>Przykład

```cpp
// new_op_new.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;

class MyClass
{
public:
   MyClass( )
   {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass( )
   {
      imember = 0; cout << "Destructing MyClass." << this << endl;
   };
   int imember;
};

int main( )
{
   // The first form of new delete
   MyClass* fPtr = new MyClass;
   delete fPtr;

   // The second form of new delete
   MyClass* fPtr2 = new( nothrow ) MyClass;
   delete fPtr2;

   // The third form of new delete
   char x[sizeof( MyClass )];
   MyClass* fPtr3 = new( &x[0] ) MyClass;
   fPtr3 -> ~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;
}
```

## <a name="op_new_arr"></a>operator new []

Funkcja alokacji wywołana przez nowe wyrażenie do przydzielenia magazynu dla tablicy obiektów.

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);
void* operator new[](std::size_t count, const std::nothrow_t&) throw();
void* operator new[](std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>Parametry

*liczba*\
Liczba bajtów magazynu do przydzielenia dla obiektu Array.

\ *PTR*
Wskaźnik, który ma zostać zwrócony.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do najmniejszego bajtu nowo przydzielonych magazynów. Lub *PTR*.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja jest wywoływana przez wyrażenie `new[]`, aby przydzielić `count` bajty magazynu odpowiednio wyrównane do reprezentowania dowolnego obiektu tablicy o tym rozmiarze lub mniejszej. Program może zdefiniować funkcję z tą sygnaturą funkcji, która zastępuje domyślną wersję zdefiniowaną przez bibliotekę C++ standardową. Wymagane zachowanie jest takie samo jak dla [operatora new](../standard-library/new-operators.md#op_new)(**size_t**). Domyślnym zachowaniem jest zwrócenie `operator new`(`count`).

Druga funkcja jest wywoływana przez wyrażenie `new[]` umieszczania, aby alokować `count` bajty magazynu odpowiednio wyrównane do reprezentowania dowolnego obiektu tablicy tego rozmiaru. Program może zdefiniować funkcję z tą sygnaturą funkcji, która zastępuje domyślną wersję zdefiniowaną przez bibliotekę C++ standardową. Domyślnym zachowaniem jest zwrócenie **operatornew**(`count`), jeśli ta funkcja się powiedzie. W przeciwnym razie zwraca wskaźnik o wartości null.

Trzecia funkcja jest wywoływana przez wyrażenie `new[]` umieszczania w postaci **New** ( *args*) **t**[ **N**]. W tym miejscu *argumenty* składają się z pojedynczego wskaźnika obiektu. Funkcja zwraca `ptr`.

Aby zwolnić magazyn przydzielony przez `operator new[]`, należy [usunąć&#91;operatora](../standard-library/new-operators.md#op_delete_arr)wywołań.

Aby uzyskać informacje o wyrzucaniu lub niezgłaszaniu zachowania nowych, zobacz [Operatory New i DELETE](../cpp/new-and-delete-operators.md).

### <a name="example"></a>Przykład

```cpp
// new_op_alloc.cpp
// compile with: /EHsc
#include <new>
#include <iostream>

using namespace std;

class MyClass {
public:
   MyClass() {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass() {
      imember = 0; cout << "Destructing MyClass." << this << endl;
      };
   int imember;
};

int main() {
   // The first form of new delete
   MyClass* fPtr = new MyClass[2];
   delete[ ] fPtr;

   // The second form of new delete
   char x[2 * sizeof( MyClass ) + sizeof(int)];

   MyClass* fPtr2 = new( &x[0] ) MyClass[2];
   fPtr2[1].~MyClass();
   fPtr2[0].~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;

   // The third form of new delete
   MyClass* fPtr3 = new( nothrow ) MyClass[2];
   delete[ ] fPtr3;
}
```
