---
title: '&lt;nowe&gt; operatorów'
ms.date: 11/04/2016
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
ms.openlocfilehash: 87f7b6cfd6a06ab03b27ebe6aa4dd41b0b900673
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570537"
---
# <a name="ltnewgt-operators"></a>&lt;nowe&gt; operatorów

||||
|-|-|-|
|[Usuwanie operatora](#op_delete)|[usuwanie operatora[]](#op_delete_arr)|[nowy operator](#op_new)|
|[nowy operator[]](#op_new_arr)|

## <a name="op_delete"></a>  Usuwanie operatora

Funkcja wywoływana przez wyrażenie delete, aby cofnięcie przydziału magazynu dla poszczególnych obiektów.

```cpp
void operator delete(void* ptr) throw();

void operator delete(void *,
    void*) throw();

void operator delete(void* ptr,
    const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Wskaźnik, którego wartość ma być renderowany przez usunięcie nieprawidłowy.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja jest wywoływana przez wyrażenie delete do renderowania wartości *ptr* nieprawidłowy. Program można zdefiniować funkcję podpisem tej funkcji, która zastępuje domyślną wersję definicją standardowej biblioteki języka C++. Wymagane zachowanie ma akceptować wartości *ptr* oznacza to wartość null lub który został zwrócony przez wcześniejsze wywołanie [nowy operator](../standard-library/new-operators.md#op_new)(**size_t**).

Domyślne zachowanie dla wartości null *ptr* się nic nie rób. Każda inna wartość *ptr* musi być wartością wcześniej zwracany przez wywołanie, jak opisano wcześniej. Domyślne zachowanie dla wartości innej niż null wartości elementu *ptr* się odzyskać Magazyn przydzielony przez wcześniejsze wywołanie elementu. Jest nieokreślony, pod jakimi warunkami część lub całość takiego odzyskiwanego magazynu jest przydzielany przez kolejne wywołanie `operator new`(**size_t**), lub dowolnych `calloc`( **size_t**), `malloc`( **size_t**), lub `realloc`( **void**<strong>\*</strong>, **size_t**).

Druga funkcja jest wywoływana przez wyrażenie usunięcia położenia odpowiadający nowe wyrażenie w formie **nowe**( **std::size_t**). Nic nie robi.

Trzecia funkcja jest wywoływana przez wyrażenie usunięcia położenia odpowiadający nowe wyrażenie w formie **nowe**( **std::size_t**, **conststd::nothrow_t &**). Program można zdefiniować funkcję podpisem tej funkcji, która zastępuje domyślną wersję definicją standardowej biblioteki języka C++. Wymagane zachowanie ma akceptować wartości `ptr` oznacza to wartość null lub który został zwrócony przez wcześniejsze wywołanie `operator new`( **size_t**). Domyślne zachowanie to można obliczyć **Usuń**(`ptr`).

### <a name="example"></a>Przykład

Zobacz [nowy operator](../standard-library/new-operators.md#op_new) przykład używanego przez **operatora delete**.

## <a name="op_delete_arr"></a>  Usuwanie operatora]

Funkcja wywoływana przez wyrażenie usunięcia można cofnąć alokacji pamięci masowej na tablicę obiektów.

```cpp
void operator delete[](void* ptr) throw();

void operator delete[](void *,
    void*) throw();

void operator delete[](void* ptr,
    const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Wskaźnik, którego wartość ma być renderowany przez usunięcie nieprawidłowy.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja jest wywoływana przez `delete[]` wyrażenia do renderowania wartości *ptr* nieprawidłowy. Funkcja jest wymienny, ponieważ program można zdefiniować funkcję podpisem tej funkcji, która zastępuje domyślną wersję definicją standardowej biblioteki C++. Wymagane zachowanie ma akceptować wartości *ptr* oznacza to wartość null lub który został zwrócony przez wcześniejsze wywołanie [nowy operator&#91;&#93;](../standard-library/new-operators.md#op_new_arr)(**size_t**). Domyślne zachowanie dla wartości null *ptr* się nic nie rób. Każda inna wartość *ptr* musi być wartością wcześniej zwracany przez wywołanie, jak opisano wcześniej. Domyślne zachowanie dla tych innych niż null wartość *ptr* się odzyskać Magazyn przydzielony przez wcześniejsze wywołanie elementu. Jest nieokreślony, pod jakimi warunkami część lub całość takiego odzyskiwanego magazynu jest przydzielany przez kolejne wywołanie [nowy operator](../standard-library/new-operators.md#op_new)(**size_t**), lub dowolnych `calloc`(**size_t**), `malloc`(**size_t**), lub `realloc`( **void**<strong>\*</strong>, **size_t**) .

Druga funkcja jest wywoływana przez umieszczania `delete[]` wyrażenie odpowiadające `new[]` wyrażenie w formie `new[]`(**std::size_t**). Nic nie robi.

Trzecia funkcja jest wywoływana przez umieszczania Usuń wyrażenie odpowiadające `new[]` wyrażenie w formie `new[]`( **std::size_t**, **const std::nothrow_t &**). Program można zdefiniować funkcję podpisem tej funkcji, która zastępuje domyślną wersję definicją standardowej biblioteki języka C++. Wymagane zachowanie ma akceptować wartości *ptr* oznacza to wartość null lub który zwrócił podczas wcześniejszego wywołania do operatora `new[]`(**size_t**). Domyślne zachowanie to można obliczyć `delete[]`( `ptr`).

### <a name="example"></a>Przykład

Zobacz [nowy operator&#91; &#93; ](../standard-library/new-operators.md#op_new_arr) przykłady stosowania `operator delete[]`.

## <a name="op_new"></a>  nowy operator

Funkcja wywoływana przez nowe wyrażenie do przydzielania pamięci dla poszczególnych obiektów.

```cpp
void* operator new(std::size_t count) throw(bad_alloc);

void* operator new(std::size_t count,
    const std::nothrow_t&) throw();

void* operator new(std::size_t count,
    void* ptr) throw();
```

### <a name="parameters"></a>Parametry

*Liczba*<br/>
Liczba bajtów magazynu do przydzielenia.

*ptr*<br/>
Wskaźnik, który ma zostać zwrócona.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do najniższym adresem bajtów magazynu nowo przydzielone. Lub *ptr*.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja jest wywoływana przez nowe wyrażenie można przydzielić `count` bajtów magazynu odpowiednio wyrównaną do do reprezentowania dowolnego obiektu tego rozmiaru. Program można zdefiniować funkcję alternatywne podpisem tej funkcji, która zastępuje domyślną wersję definicją standardowej biblioteki C++, a więc jest wymienny.

Wymagane zachowanie ma zwrócić wskaźnik o wartości innej niż NULL tylko wtedy, gdy można przydzielić magazynu zgodnie z żądaniem. Każdy taki przydział daje wskaźnik do magazynu odłączonego od innych magazynów przydzielone. Kolejność i contiguity pamięci przydzielonej przez kolejnych wywołań jest nieokreślona. Początkowa wartość przechowywana jest nieokreślony. Zwrócony wskaźnik wskazuje początek (najniższy adres bajtów) przydzielenia pamięci. Jeśli liczba jest równa zero, wartość zwracana nie są sobie równe jakąkolwiek wartość zwrócona przez funkcję.

Domyślnym zachowaniem jest wykonywanie pętli. W pętli funkcja najpierw próbuje przydzielić żądanego magazynu. Czy próba polega na wywołaniu `malloc`( **size_t**) jest nieokreślona. Jeśli próba zakończy się pomyślnie, funkcja zwraca wskaźnik do przydzielenia pamięci. W przeciwnym razie funkcja wywołuje wyznaczonej [nowy program obsługi](../standard-library/new-typedefs.md#new_handler). Jeśli wywołana funkcja zwróci wartość, powtórzeniu pętli. Pętla kończy, gdy próba przydzielanie magazynu do żądanej zakończy się pomyślnie lub wywołana funkcja nie zwraca.

Wymagane działanie nowy program obsługi jest wykonaj jedną z następujących czynności:

- Udostępnij więcej pamięci masowej do alokacji, a następnie powrócić.

- Wywołaj opcję **przerwać** lub **wyjść**(`int`).

- Obiekt typu throw **bad_alloc —.**

Domyślne zachowanie [nowy program obsługi](../standard-library/new-typedefs.md#new_handler) to zgłosić obiektu typu `bad_alloc`. Wskaźnik zerowy wyznacza nowy domyślny program obsługi.

Kolejność i contiguity pamięci przydzielonej przez kolejne wywołania `operator new`(**size_t**) jest nieokreślony, ponieważ są tam przechowywane wartości początkowe.

Druga funkcja jest wywoływana przez nowe wyrażenie umieszczania można przydzielić `count` bajtów magazynu odpowiednio wyrównaną do do reprezentowania dowolnego obiektu tego rozmiaru. Program można zdefiniować funkcję alternatywne podpisem tej funkcji, która zastępuje domyślną wersję definicją standardowej biblioteki C++, a więc jest wymienny.

Zachowanie domyślne ma zwracać `operator new`(`count`) Jeśli ta funkcja zakończy się powodzeniem. W przeciwnym razie zwraca pusty wskaźnik.

Trzecia funkcja jest wywoływana przez umieszczania **nowe** wyrażenie w formie **nowe** ( *args*) T. W tym miejscu *args* składa się z wskaźnika pojedynczego obiektu. Może to być przydatne przy konstruowaniu obiektu pod znanymi adresami. Funkcja zwraca *ptr*.

Aby zwolnić Magazyn przydzielony przez **nowy operator**, wywołaj [operatora delete](../standard-library/new-operators.md#op_delete).

Aby uzyskać informacje o zgłaszaniu lub nonthrowing zachowaniem nowe, zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md).

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

## <a name="op_new_arr"></a>  nowy operator]

Funkcja alokacji, wywoływana przez nowe wyrażenie do przydzielania pamięci dla tablicy obiektów.

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);

void* operator new[](std::size_t count,
    const std::nothrow_t&) throw();

void* operator new[](std::size_t count,
    void* ptr) throw();
```

### <a name="parameters"></a>Parametry

*Liczba*<br/>
Liczba bajtów magazynu do przydzielenia dla obiektu array.

*ptr*<br/>
Wskaźnik, który ma zostać zwrócona.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do najniższym adresem bajtów magazynu nowo przydzielone. Lub *ptr*.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja jest wywoływana przez `new[]` wyrażenie, aby przydzielić `count` bajtów magazynu odpowiednio wyrównany do reprezentowania dowolnego obiektu array tego rozmiaru lub mniejszy. Program można zdefiniować funkcję podpisem tej funkcji, która zastępuje domyślną wersję definicją standardowej biblioteki języka C++. Wymagane zachowanie jest taka sama, jak w przypadku [nowy operator](../standard-library/new-operators.md#op_new)(**size_t**). Zachowanie domyślne ma zwracać `operator new`( `count`).

Druga funkcja jest wywoływana przez umieszczania `new[]` wyrażenie, aby przydzielić `count` bajtów magazynu odpowiednio wyrównaną do do reprezentowania dowolnego obiektu array tego rozmiaru. Program można zdefiniować funkcję podpisem tej funkcji, która zastępuje domyślną wersję definicją standardowej biblioteki języka C++. Zachowanie domyślne ma zwracać **operatornew**(`count`) Jeśli ta funkcja zakończy się powodzeniem. W przeciwnym razie zwraca pusty wskaźnik.

Trzecia funkcja jest wywoływana przez umieszczania `new[]` wyrażenie w formie **nowe** ( *args*) **T**[ **N**]. W tym miejscu *args* składa się z wskaźnika pojedynczego obiektu. Funkcja zwraca `ptr`.

Aby zwolnić Magazyn przydzielony przez `operator new[]`, wywołaj [operatora delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr).

Aby uzyskać informacje o zgłaszaniu lub nonthrowing zachowaniem nowe, zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md).

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

## <a name="see-also"></a>Zobacz także

[\<new>](../standard-library/new.md)<br/>
