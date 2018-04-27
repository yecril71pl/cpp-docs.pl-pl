---
title: '&lt;nowe&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
caps.latest.revision: 8
manager: ghogen
ms.openlocfilehash: c993f62ef0bf65da36ba507938354877ba59d165
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltnewgt-operators"></a>&lt;nowe&gt; operatory

||||
|-|-|-|
|[Usuwanie operatora](#op_delete)|[Usuwanie operatora]](#op_delete_arr)|[nowy operator](#op_new)|
|[nowy operator]](#op_new_arr)|

## <a name="op_delete"></a>  Usuwanie operatora

Funkcja wywoływana przez wyrażenie usunięcia, należy cofnąć magazynu dla poszczególnych obiektów.

```cpp
void operator delete(void* ptr) throw();

void operator delete(void *,
    void*) throw();

void operator delete(void* ptr,
    const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parametry

`ptr` Wskaźnik, którego wartość ma być renderowany nieprawidłowy przez usunięcie.

### <a name="remarks"></a>Uwagi

Pierwszy funkcja jest wywoływana przez wyrażenie delete do renderowania wartości `ptr` nieprawidłowy. Program można zdefiniować funkcję podpisem tej funkcji, który zastępuje domyślnej wersji zdefiniowany przez standardowa biblioteka C++. Wymagane jest aby zaakceptować wartości `ptr` oznacza to null lub którego został zwrócony przez wywołanie wcześniejszych [nowy operator](../standard-library/new-operators.md#op_new)( **size_t**).

Domyślne zachowanie dla wartości równej null `ptr` ma nic nie rób. Każda inna wartość `ptr` musi być wartością wcześniej zwrócony przez wywołanie opisana powyżej. Domyślnym zachowaniem takich wartość inną niż null z `ptr` jest, aby odzyskać miejsce do magazynowania przydzielone przez wywołanie wcześniej. Jest nieokreślony, pod jakimi warunkami części lub całości tych regeneracji magazynu został przydzielony przez kolejne wywołanie `operator new`( **size_t**), lub dowolnych `calloc`( **size_t**), `malloc`( **size_t**), lub `realloc`( **void\***, **size_t**).

Druga funkcja jest wywoływana przez odpowiadający nowe wyrażenie w postaci wyrażenia usuwania umieszczania **nowe**( **std::size_t**). Nie działają.

Trzeci funkcja jest wywoływana przez odpowiadający nowe wyrażenie w postaci wyrażenia usuwania umieszczania **nowe**( **std::size_t**, **conststd::nothrow_t &**). Program można zdefiniować funkcję podpisem tej funkcji, który zastępuje domyślnej wersji zdefiniowany przez standardowa biblioteka C++. Wymagane jest aby zaakceptować wartości `ptr` oznacza to null lub którego został zwrócony przez wywołanie wcześniejszych `operator new`( **size_t**). Domyślnym zachowaniem jest ocena **usunąć**( `ptr`).

### <a name="example"></a>Przykład

Zobacz [nowy operator](../standard-library/new-operators.md#op_new) przykład używanego `operator delete`.

## <a name="op_delete_arr"></a>  Usuwanie operatora]

Funkcja wywoływana przez wyrażenie usuwania można cofnąć alokacji pamięci masowej dla tablicy obiektów.

```cpp
void operator delete[](void* ptr) throw();

void operator delete[](void *,
    void*) throw();

void operator delete[](void* ptr,
    const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parametry

`ptr` Wskaźnik, którego wartość ma być renderowany nieprawidłowy przez usunięcie.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja jest wywoływana przez `delete[]` wyrażenia do renderowania wartości `ptr` nieprawidłowy. Funkcja jest wymienne, ponieważ program można zdefiniować funkcję podpisem tej funkcji, który zastępuje domyślnej wersji zdefiniowany przez standardowa biblioteka C++. Wymagane jest aby zaakceptować wartości `ptr` oznacza to null lub którego został zwrócony przez wywołanie wcześniejszych [nowy operator&#91;&#93;](../standard-library/new-operators.md#op_new_arr)( **size_t**). Domyślne zachowanie dla wartości równej null `ptr` ma nic nie rób. Każda inna wartość `ptr` musi być wartością wcześniej zwrócony przez wywołanie opisana powyżej. Domyślnym zachowaniem takich wartość inną niż null z `ptr` jest, aby odzyskać miejsce do magazynowania przydzielone przez wywołanie wcześniej. Jest nieokreślony, pod jakimi warunkami części lub całości tych regeneracji magazynu został przydzielony przez kolejne wywołanie [nowy operator](../standard-library/new-operators.md#op_new)( **size_t**), lub dowolnych `calloc`( **size_t**), `malloc`( **size_t**), lub `realloc`( **void\***, **size_t**).

Druga funkcja jest wywoływana przez położenia `delete[]` wyrażenie odpowiadające `new[]` wyrażenie w postaci `new[]`( **std::size_t**). Nie działają.

Trzeci funkcja jest wywoływana przez umieszczania delete wyrażenie odpowiadające `new[]` wyrażenie w postaci `new[]`( **std::size_t**, **const std::nothrow_t &**). Program można zdefiniować funkcję podpisem tej funkcji, który zastępuje domyślnej wersji zdefiniowany przez standardowa biblioteka C++. Wymagane jest aby zaakceptować wartości `ptr` oznacza to wartość null lub którego został zwrócony przez wywołanie wcześniejszych operator `new[]`( **size_t**). Domyślnym zachowaniem jest ocena `delete[]`( `ptr`).

### <a name="example"></a>Przykład

Zobacz [nowy operator&#91; &#93; ](../standard-library/new-operators.md#op_new_arr) przykłady stosowania `operator delete[]`.

## <a name="op_new"></a>  nowy operator

Funkcja wywoływana przez nowe wyrażenie można przydzielić magazynu dla poszczególnych obiektów.

```cpp
void* operator new(std::size_t count) throw(bad_alloc);

void* operator new(std::size_t count,
    const std::nothrow_t&) throw();

void* operator new(std::size_t count,
    void* ptr) throw();
```

### <a name="parameters"></a>Parametry

`count` Liczba bajtów magazynu do przydzielenia.

`ptr` Wskaźnik do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do najniższym adresem bajtów pamięci nowo przydzielone. Or `ptr.`

### <a name="remarks"></a>Uwagi

Pierwsza funkcja jest wywoływana przez nowe wyrażenie przydzielić `count` bajtów pamięci odpowiednio wyrównane do reprezentowania dowolnego obiektu tego rozmiaru. Program można zdefiniować alternatywny funkcja podpisem tej funkcji, który zastępuje domyślnej wersji zdefiniowany przez standardowa biblioteka C++ i dlatego jest wymienne.

Wymagane jest do zwrócenia niepuste wskaźnika tylko wtedy, gdy mogą być przydzielone magazynu, zgodnie z żądaniem. Każdy taki przydział daje wskaźnik do magazynu odłączony od innych magazynów przydzielone. Kolejność i contiguity miejsce do magazynowania przydzielone przez kolejne wywołania jest nieokreślony. Wartość początkowa przechowywanych jest nieokreślony. Zwrócony wskaźnik wskazuje początek Magazyn przydzielony (najniższym adresem bajtów). Jeśli liczba jest równa zero, wartość zwracana porównuje inne wartości zwracane przez funkcję.

Domyślnym zachowaniem jest wykonanie pętli. W pętli funkcja najpierw próbuje przydzielić żądanej magazynu. Czy próba polega na wywołanie `malloc`( **size_t**) jest nieokreślony. Jeśli próba powiedzie się, funkcja zwraca wskaźnik do Magazyn przydzielony. W przeciwnym razie wyznaczone wywołuje funkcji [nowy program obsługi](../standard-library/new-typedefs.md#new_handler). Jeśli wywołana funkcja zwraca, powtarza pętli. Pętla kończy się po pomyślnym zakończeniu operacji próba przydzielenie żądanego magazynu lub gdy wywołana funkcja nie może zwracać.

Wymagane zachowanie nowy program obsługi jest wykonać jedną z następujących czynności:

- Udostępnij więcej pamięci masowej do przydzielenia, a następnie wróć.

- Wywołaj albo **przerwać** lub **zakończyć**( `int`).

- Throw typu obiektu **bad_alloc —.**

Domyślne zachowanie [nowy program obsługi](../standard-library/new-typedefs.md#new_handler) ma throw typu obiektu `bad_alloc`. Wskaźnik null Określa nowy domyślny program obsługi.

Kolejność i contiguity miejsce do magazynowania przydzielone przez kolejne wywołania `operator new`( **size_t**) nie jest określona, są przechowywane wartości początkowe.

Drugi funkcja jest wywoływana przez nowe wyrażenie umieszczania można przydzielić `count` bajtów pamięci odpowiednio wyrównane do reprezentowania dowolnego obiektu tego rozmiaru. Program można zdefiniować alternatywny funkcja podpisem tej funkcji, który zastępuje domyślnej wersji zdefiniowany przez standardowa biblioteka C++ i dlatego jest wymienne.

Domyślnym zachowaniem jest zwracany `operator new`( `count`) Jeśli ta funkcja zakończy się powodzeniem. W przeciwnym razie zwraca wartość wskaźnika o wartości null.

Trzeci funkcja jest wywoływana przez położenia **nowe** wyrażenie w postaci **nowe** ( *argumentów*) T. W tym miejscu *argumentów* składa się z wskaźnik pojedynczego obiektu. Może to być przydatne podczas konstruowania obiektu pod adresem znane. Funkcja zwraca *ptr*.

Aby zwolnić miejsce do magazynowania przydzielone przez `operator new`, wywołaj [operatora delete](../standard-library/new-operators.md#op_delete).

Aby uzyskać informacje o zgłaszaniu lub nonthrowing zachowania nowe, zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md).

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

Funkcja alokacji, wywoływana przez nowe wyrażenie, aby przydzielić magazyn na tablicę obiektów.

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);

void* operator new[](std::size_t count,
    const std::nothrow_t&) throw();

void* operator new[](std::size_t count,
    void* ptr) throw();
```

### <a name="parameters"></a>Parametry

`count` Liczba bajtów magazynu do przydzielenia dla obiekt array.

`ptr` Wskaźnik do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do najniższym adresem bajtów pamięci nowo przydzielone. Or `ptr.`

### <a name="remarks"></a>Uwagi

Pierwsza funkcja jest wywoływana przez `new[]` wyrażenie przydzielić `count` bajtów pamięci odpowiednio wyrównany do reprezentowania dowolnego obiektu tego rozmiaru tablicy lub mniejszy. Program można zdefiniować funkcję podpisem tej funkcji, który zastępuje domyślnej wersji zdefiniowany przez standardowa biblioteka C++. Wymagane zachowanie jest takie samo, jak w przypadku [nowy operator](../standard-library/new-operators.md#op_new)( **size_t**). Domyślnym zachowaniem jest zwracany `operator new`( `count`).

Druga funkcja jest wywoływana przez położenia `new[]` wyrażenie przydzielić `count` bajtów pamięci odpowiednio wyrównane do reprezentowania dowolnego obiektu tego rozmiaru tablicy. Program można zdefiniować funkcję podpisem tej funkcji, który zastępuje domyślnej wersji zdefiniowany przez standardowa biblioteka C++. Domyślnym zachowaniem jest zwracany **operatornew**( `count`) Jeśli ta funkcja zakończy się powodzeniem. W przeciwnym razie zwraca wartość wskaźnika o wartości null.

Trzeci funkcja jest wywoływana przez położenia `new[]` wyrażenie w postaci **nowe** ( *argumentów*) **T**[ **N**]. W tym miejscu *argumentów* składa się z wskaźnik pojedynczego obiektu. Funkcja zwraca `ptr`.

Aby zwolnić miejsce do magazynowania przydzielone przez `operator new[]`, wywołaj [operatora delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr).

Aby uzyskać informacje o zgłaszaniu lub nonthrowing zachowania nowe, zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md).

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
