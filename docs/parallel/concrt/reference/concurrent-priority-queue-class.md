---
title: "concurrent_priority_queue — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::clear
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::empty
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::get_allocator
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::push
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::size
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::swap
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::try_pop
dev_langs: C++
helpviewer_keywords: concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1796351dc594712ef69ec5562f85501b30997104
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="concurrentpriorityqueue-class"></a>concurrent_priority_queue — Klasa
`concurrent_priority_queue` Klasy to kontener udostępniający wiele wątków jednocześnie elementów wypychania i pop. Elementy są zdjęte ze stosu w kolejności priorytetu, której priorytet jest określana przez obiekt podana jako argument szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych elementów, które mają być przechowywane w kolejce priorytet.  
  
 `_Compare`  
 Typ obiektu funkcji, które można porównać dwóch wartości elementu jako klucze sortowania, aby określić ich kolejność względny priorytet kolejki. Ten argument jest opcjonalny i binarne predykatu `less<T>` jest wartością domyślną.  
  
 `_Ax`  
 Typ reprezentujący obiekt alokatora przechowywane, który hermetyzuje szczegółowe informacje dotyczące alokacji i cofania alokacji pamięci dla kolejki równoczesnych priorytet. Ten argument jest opcjonalny, a wartość domyślna to `allocator<T>`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`allocator_type`|Typ, który reprezentuje klasę alokatora równoczesnych priorytet kolejki.|  
|`const_reference`|Typ, który reprezentuje typu const odwołanie do elementu typu przechowywane w kolejce równoczesnych priorytet.|  
|`reference`|Typ, który reprezentuje odwołanie do elementu typu przechowywane w kolejce równoczesnych priorytet.|  
|`size_type`|Typ, który oblicza liczbę elementów w kolejce równoczesnych priorytet.|  
|`value_type`|Typ, który reprezentuje typ danych przechowywanych w kolejce równoczesnych priorytet.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[concurrent_priority_queue —](#ctor)|Przeciążone. Tworzy kolejkę równoczesnych priorytet.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Wyczyść](#clear)|Usuwa wszystkie elementy w równoczesnych priorytet. Ta metoda nie jest bezpieczne współbieżności.|  
|[pusty](#empty)|Testy, jeśli kolejka równoczesnych priorytet jest pusta w momencie ta metoda jest wywoływana. Ta metoda jest bezpieczne współbieżności.|  
|[get_allocator](#get_allocator)|Zwraca kopię alokatora użyta do skonstruowania równoczesnych priorytet kolejki. Ta metoda jest bezpieczne współbieżności.|  
|[push](#push)|Przeciążone. Dodaje element do kolejki równoczesnych priorytet. Ta metoda jest bezpieczne współbieżności.|  
|[rozmiar](#size)|Zwraca liczbę elementów w kolejce równoczesnych priorytet. Ta metoda jest bezpieczne współbieżności.|  
|[swap](#swap)|Zamienia zawartość dwie równoczesne priorytet kolejki. Ta metoda nie jest bezpieczne współbieżności.|  
|[try_pop](#try_pop)|Usuwa i zwraca element najwyższy priorytet z kolejki, jeśli kolejka jest pusta. Ta metoda jest bezpieczne współbieżności.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator =](#operator_eq)|Przeciążone. Przypisuje zawartość innego `concurrent_priority_queue` obiektu do tego. Ta metoda nie jest bezpieczne współbieżności.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać szczegółowe informacje na temat `concurrent_priority_queue` , zobacz [równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `concurrent_priority_queue`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concurrent_priority_queue.h  
  
 **Namespace:** współbieżności  
  
##  <a name="clear"></a>Wyczyść 

 Usuwa wszystkie elementy w równoczesnych priorytet. Ta metoda nie jest bezpieczne współbieżności.  
  
```
void clear();
```  
  
### <a name="remarks"></a>Uwagi  
 `clear`nie jest bezpieczne współbieżności. Należy się upewnić, że nie ma innych wątków są wywoływanie metod w kolejce równoczesnych priorytet podczas wywoływania tej metody. `clear`nie spowoduje zwolnienia pamięci.  
  
##  <a name="ctor"></a>concurrent_priority_queue — 

 Tworzy kolejkę równoczesnych priorytet.  
  
```
explicit concurrent_priority_queue(
    const allocator_type& _Al = allocator_type());

explicit concurrent_priority_queue(
    size_type _Init_capacity,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_priority_queue(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());

concurrent_priority_queue(
    const concurrent_priority_queue& _Src);

concurrent_priority_queue(
    const concurrent_priority_queue& _Src,
    const allocator_type& _Al);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src,
    const allocator_type& _Al);
```  
  
### <a name="parameters"></a>Parametry  
 `_InputIterator`  
 Typ iteratora wejściowego.  
  
 `_Al`  
 Klasa alokatora do wykorzystania z tym obiektem.  
  
 `_Init_capacity`  
 Początkowa pojemność `concurrent_priority_queue` obiektu.  
  
 `_Begin`  
 Pozycja pierwszego elementu w zakresie elementów do skopiowania.  
  
 `_End`  
 Pozycja pierwszego elementu poza zakres elementów do skopiowania.  
  
 `_Src`  
 Źródło `concurrent_priority_queue` obiekt, aby skopiować lub przenieść elementy z.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie konstruktory zapisania obiektu alokatora `_Al` i zainicjuj priorytet kolejki.  
  
 Pierwszy Konstruktor określa priorytet początkowa pusta kolejki i opcjonalnie określa przydzielania.  
  
 Drugi Konstruktor określa priorytet kolejki z początkowej pojemności `_Init_capacity` i opcjonalnie określa przydzielania.  
  
 Trzeci konstruktora określa wartości dostarczone przez zakres iteratora [ `_Begin`, `_End`) i opcjonalnie określa przydzielania.  
  
 Konstruktory czwartym i piątym Określ kopię kolejki priorytet `_Src`.  
  
 Konstruktory szóstego lub siódmego Określ przenoszenia kolejki priorytet `_Src`.  
  
##  <a name="empty"></a>pusty 

 Testy, jeśli kolejka równoczesnych priorytet jest pusta w momencie ta metoda jest wywoływana. Ta metoda jest bezpieczne współbieżności.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli kolejka priorytetów była pusta w momencie wywołano funkcję `false` inaczej.  
  
##  <a name="get_allocator"></a>get_allocator 

 Zwraca kopię alokatora użyta do skonstruowania równoczesnych priorytet kolejki. Ta metoda jest bezpieczne współbieżności.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kopia programu przydzielania użyta do skonstruowania `concurrent_priority_queue` obiektu.  
  
##  <a name="operator_eq"></a>operator = 

 Przypisuje zawartość innego `concurrent_priority_queue` obiektu do tego. Ta metoda nie jest bezpieczne współbieżności.  
  
```
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
 Źródło `concurrent_priority_queue` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `concurrent_priority_queue` obiektu.  
  
##  <a name="push"></a>wypychania 

 Dodaje element do kolejki równoczesnych priorytet. Ta metoda jest bezpieczne współbieżności.  
  
```
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```  
  
### <a name="parameters"></a>Parametry  
 `_Elem`  
 Element ma zostać dodana do kolejki równoczesnych priorytet.  
  
##  <a name="size"></a>rozmiar 

 Zwraca liczbę elementów w kolejce równoczesnych priorytet. Ta metoda jest bezpieczne współbieżności.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w tym `concurrent_priority_queue` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Zwrócony rozmiar jest gwarantowana aby uwzględnić wszystkie elementy dodane przez wywołania funkcji `push`. Jednak mogą nie uwzględniać wyniki oczekujących współbieżnych operacji.  
  
##  <a name="swap"></a>swap 

 Zamienia zawartość dwie równoczesne priorytet kolejki. Ta metoda nie jest bezpieczne współbieżności.  
  
```
void swap(concurrent_priority_queue& _Queue);
```  
  
### <a name="parameters"></a>Parametry  
 `_Queue`  
 `concurrent_priority_queue` Obiekt do wymiany zawartości z.  
  
##  <a name="try_pop"></a>try_pop 

 Usuwa i zwraca element najwyższy priorytet z kolejki, jeśli kolejka jest pusta. Ta metoda jest bezpieczne współbieżności.  
  
```
bool try_pop(reference _Elem);
```  
  
### <a name="parameters"></a>Parametry  
 `_Elem`  
 Odwołanie do zmiennej, która zostanie wypełniona elementu najwyższy priorytet, jeśli kolejka jest pusta.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli wartość została zdjęte ze stosu, `false` inaczej.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md)



