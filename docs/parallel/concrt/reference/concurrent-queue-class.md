---
title: "concurrent_queue — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::clear
- CONCURRENT_QUEUE/concurrency::concurrent_queue::empty
- CONCURRENT_QUEUE/concurrency::concurrent_queue::get_allocator
- CONCURRENT_QUEUE/concurrency::concurrent_queue::push
- CONCURRENT_QUEUE/concurrency::concurrent_queue::try_pop
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_begin
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_end
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_size
dev_langs: C++
helpviewer_keywords: concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6e2e572574bfd8313106dbdda64b63077d5d2e7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="concurrentqueue-class"></a>concurrent_queue — Klasa
`concurrent_queue` Klasa jest sekwencji kontenera klasy, która umożliwia w pierwszej, FIFO dostęp do swoich elementów. Umożliwia ona ograniczony zestaw operacji bezpieczne współbieżności, takich jak `push` i `try_pop`.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych elementów, które mają być przechowywane w kolejce.  
  
 `_Ax`  
 Typ reprezentujący obiekt alokatora przechowywane, który hermetyzuje szczegółowe informacje dotyczące alokacji i cofania alokacji pamięci dla tej kolejki współbieżnych. Ten argument jest opcjonalny, a wartość domyślna to `allocator<T>`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`allocator_type`|Typ, który reprezentuje klasę alokatora równoczesnych kolejki.|  
|`const_iterator`|Typ reprezentujący z systemem innym niż wątkowo `const` iteratora za pośrednictwem elementów w kolejce współbieżnych.|  
|`const_reference`|Typ, który zawiera odwołanie do `const` element przechowywane w kolejce równoczesnych do odczytu i wykonywania `const` operacji.|  
|`difference_type`|Typ, który udostępnia podpisem odległość między dwóch elementów w kolejce współbieżnych.|  
|`iterator`|Typ, który reprezentuje iteratora z systemem innym niż wątkowo za pośrednictwem elementów w kolejce współbieżnych.|  
|`reference`|Typ, który zawiera odwołanie do elementu przechowywane w kolejce współbieżnych.|  
|`size_type`|Typ, który oblicza liczbę elementów w kolejce współbieżnych.|  
|`value_type`|Typ, który reprezentuje typ danych przechowywanych w kolejce współbieżnych.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[concurrent_queue —](#ctor)|Przeciążone. Tworzy kolejkę współbieżnych.|  
|[~ concurrent_queue — destruktor](#dtor)|Niszczy równoczesnych kolejki.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Wyczyść](#clear)|Czyści równoczesnych kolejki niszczenie żadnego obecnie elementów umieszczonych w kolejce. Ta metoda nie jest bezpieczne współbieżności.|  
|[pusty](#empty)|Testy, jeśli równoczesnych kolejka jest pusta w tej chwili ta metoda jest wywoływana. Ta metoda jest bezpieczne współbieżności.|  
|[get_allocator](#get_allocator)|Zwraca kopię alokatora użyta do skonstruowania równoczesnych kolejki. Ta metoda jest bezpieczne współbieżności.|  
|[push](#push)|Przeciążone. Enqueues element na końcu tail równoczesnych kolejki. Ta metoda jest bezpieczne współbieżności.|  
|[try_pop](#try_pop)|Dequeues element z kolejki, jeśli jest dostępny. Ta metoda jest bezpieczne współbieżności.|  
|[unsafe_begin](#unsafe_begin)|Przeciążone. Zwraca iteratora typu `iterator` lub `const_iterator` na początek kolejki współbieżnych. Ta metoda nie jest bezpieczne współbieżności.|  
|[unsafe_end](#unsafe_end)|Przeciążone. Zwraca iteratora typu `iterator` lub `const_iterator` na końcu równoczesnych kolejki. Ta metoda nie jest bezpieczne współbieżności.|  
|[unsafe_size](#unsafe_size)|Zwraca liczbę elementów w kolejce. Ta metoda nie jest bezpieczne współbieżności.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `concurrent_queue`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concurrent_queue.h  
  
 **Namespace:** współbieżności  
  
##  <a name="clear"></a>Wyczyść 

 Czyści równoczesnych kolejki niszczenie żadnego obecnie elementów umieszczonych w kolejce. Ta metoda nie jest bezpieczne współbieżności.  
  
```
void clear();
```  
  
##  <a name="ctor"></a>concurrent_queue — 

 Tworzy kolejkę współbieżnych.  
  
```
explicit concurrent_queue(
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    const concurrent_queue& _OtherQ,
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    concurrent_queue&& _OtherQ,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_queue(_InputIterator _Begin,
    _InputIterator _End);
```  
  
### <a name="parameters"></a>Parametry  
 `_InputIterator`  
 Typ iteratora wejściowego, która określa zakres wartości.  
  
 `_Al`  
 Klasa alokatora do wykorzystania z tym obiektem.  
  
 `_OtherQ`  
 Źródło `concurrent_queue` obiekt, aby skopiować lub przenieść elementy z.  
  
 `_Begin`  
 Pozycja pierwszego elementu w zakresie elementów do skopiowania.  
  
 `_End`  
 Pozycja pierwszego elementu poza zakres elementów do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie konstruktory zapisania obiektu alokatora `_Al` i zainicjuj kolejki.  
  
 Pierwszy Konstruktor określa pustej kolejce początkowej i jawnie określa typ alokatora ma być używany.  
  
 Drugi Konstruktor Określa kopię równoczesnych kolejki `_OtherQ`.  
  
 Trzeci konstruktora określa przenoszenia równoczesnych kolejki `_OtherQ`.  
  
 Konstruktor czwarty określa wartości dostarczone przez zakres iteratora [ `_Begin`, `_End`).  
  
##  <a name="dtor"></a>~ concurrent_queue — 

 Niszczy równoczesnych kolejki.  
  
```
~concurrent_queue();
```  
  
##  <a name="empty"></a>pusty 

 Testy, jeśli równoczesnych kolejka jest pusta w tej chwili ta metoda jest wywoływana. Ta metoda jest bezpieczne współbieżności.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli równoczesnych kolejka jest pusta w tej chwili analizujemy, `false` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Gdy ta metoda jest bezpieczne współbieżności względem wywołaniami metod `push`, `try_pop`, i `empty`, do czasu jej jest kontrolowane przez wątek wywołujący wartość zwracana może być nieprawidłowy.  
  
##  <a name="get_allocator"></a>get_allocator 

 Zwraca kopię alokatora użyta do skonstruowania równoczesnych kolejki. Ta metoda jest bezpieczne współbieżności.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kopia alokatora użyta do skonstruowania równoczesnych kolejki.  
  
##  <a name="push"></a>wypychania 

 Enqueues element na końcu tail równoczesnych kolejki. Ta metoda jest bezpieczne współbieżności.  
  
```
void push(const T& _Src);

void push(T&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
 Element, który ma zostać dodana do kolejki.  
  
### <a name="remarks"></a>Uwagi  
 `push`Współbieżność palety względem wywołaniami metod `push`, `try_pop`, i `empty`.  
  
##  <a name="try_pop"></a>try_pop 

 Dequeues element z kolejki, jeśli jest dostępny. Ta metoda jest bezpieczne współbieżności.  
  
```
bool try_pop(T& _Dest);
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Odwołanie do lokalizację do przechowywania dequeued elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli element został pomyślnie dequeued `false` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli element został pomyślnie dequeued parametr `_Dest` otrzymuje wartość dequeued zostanie zniszczony oryginalnej wartości przechowywane w kolejce, a ta funkcja zwraca `true`. Jeśli nie było żadnych elementów do usuwania z kolejki, funkcja zwraca `false` bez blokowania i zawartość `_Dest` parametru jest nieokreślona.  
  
 `try_pop`Współbieżność palety względem wywołaniami metod `push`, `try_pop`, i `empty`.  
  
##  <a name="unsafe_begin"></a>unsafe_begin 

 Zwraca iteratora typu `iterator` lub `const_iterator` na początek kolejki współbieżnych. Ta metoda nie jest bezpieczne współbieżności.  
  
```
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora typu `iterator` lub `const_iterator` na początku obiekt równoczesnych kolejki.  
  
### <a name="remarks"></a>Uwagi  
 Iteratory dla `concurrent_queue` klasy są przeznaczone głównie dla debugowania, jak są one powolne i iteracji nie jest bezpieczną współbieżność w odniesieniu do innych operacji kolejki.  
  
##  <a name="unsafe_end"></a>unsafe_end 

 Zwraca iteratora typu `iterator` lub `const_iterator` na końcu równoczesnych kolejki. Ta metoda nie jest bezpieczne współbieżności.  
  
```
iterator unsafe_end();

const_iterator unsafe_end() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora typu `iterator` lub `const_iterator` na końcu równoczesnych kolejki.  
  
### <a name="remarks"></a>Uwagi  
 Iteratory dla `concurrent_queue` klasy są przeznaczone głównie dla debugowania, jak są one powolne i iteracji nie jest bezpieczną współbieżność w odniesieniu do innych operacji kolejki.  
  
##  <a name="unsafe_size"></a>unsafe_size 

 Zwraca liczbę elementów w kolejce. Ta metoda nie jest bezpieczne współbieżności.  
  
```
size_type unsafe_size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar kolejki współbieżnych.  
  
### <a name="remarks"></a>Uwagi  
 `unsafe_size`nie jest bezpieczne współbieżności i może prowadzić do niepoprawnych wyników przypadku równocześnie z wywołaniami metod `push`, `try_pop`, i `empty`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
