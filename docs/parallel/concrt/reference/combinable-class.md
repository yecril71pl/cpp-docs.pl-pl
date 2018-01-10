---
title: "combinable — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
dev_langs: C++
helpviewer_keywords: combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 698c59614894314e70019fe2b4621755b4cd3085
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="combinable-class"></a>combinable — Klasa
`combinable<T>` Obiektu mają na celu dostarczenie prywatnego wątku kopie danych, aby wykonać obliczenia podrzędnych lokalnej wątku zwolnienia blokady podczas algorytmy równoległe. Na koniec operacji równoległej obliczenia podrzędne prywatnego wątku można następnie scalić w wynik końcowy. Ta klasa można zamiast udostępnionego zmiennej i może spowodować zwiększenie wydajności, jeśli byłoby wiele rywalizacji udostępnionego zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename T>
class combinable;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych scalonych wynik końcowy. Typ musi mieć konstruktora kopiującego i konstruktora domyślnego.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[combinable —](#ctor)|Przeciążone. Tworzy nową `combinable` obiektu.|  
|[~ combinable — destruktor](#dtor)|Niszczy `combinable` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Wyczyść](#clear)|Czyści wszystkie pośrednie wyniki obliczeniową z poprzedniego użycia.|  
|[Łączenie](#combine)|Oblicza wartość końcowego z zestawu obliczenia podrzędnych lokalnej wątku przez wywołanie metody łączenia podany obiekt.|  
|[combine_each](#combine_each)|Oblicza końcowej z zestawu obliczenia podrzędnych lokalnej wątku przez wywołanie metody obiekt Połącz podany raz na lokalnej wątku podrzędnego obliczeń. Wynik końcowy jest zgromadzonych przez obiekt funkcji.|  
|[lokalne](#local)|Przeciążone. Zwraca odwołanie do obliczenia podrzędne prywatnego wątku.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator =](#operator_eq)|Przypisuje `combinable` obiektu z innego `combinable` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `combinable`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppl.h  
  
 **Namespace:** współbieżności  
  
##  <a name="clear"></a>Wyczyść 

 Czyści wszystkie pośrednie wyniki obliczeniową z poprzedniego użycia.  
  
```
void clear();
```  
  
##  <a name="ctor"></a>combinable — 

 Tworzy nową `combinable` obiektu.  
  
```
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ obiektu, obiekt inicjowania.  
  
 `_FnInitialize`  
 Funkcja, która będzie wywoływana w celu zainicjowania każdej nowej wartości prywatnego wątku typu `T`. Operator wywołania funkcji z podpisem musi obsługiwać `T ()`.  
  
 `_Copy`  
 Istniejące `combinable` kopiowanego do tego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje nowych elementów przy użyciu domyślnego konstruktora dla typu `T`.  
  
 Drugi Konstruktor inicjuje nowe elementy za pomocą obiekt inicjowania podana jako `_FnInitialize` parametru.  
  
 Trzeci Konstruktor jest Konstruktor kopiujący.  
  
##  <a name="dtor"></a>~ combinable — 

 Niszczy `combinable` obiektu.  
  
```
~combinable();
```  
  
##  <a name="combine"></a>Łączenie 

 Oblicza wartość końcowego z zestawu obliczenia podrzędnych lokalnej wątku przez wywołanie metody łączenia podany obiekt.  
  
```
template<typename _Function>
T combine(_Function _FnCombine) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ obiektu funkcji, który zostanie wywołany, do łączenia dwóch obliczenia podrzędnych lokalnej wątku.  
  
 `_FnCombine`  
 Obiekt, który jest używany do łączenia podrzędnego obliczenia. Podpis jest `T (T, T)` lub `T (const T&, const T&)`, i musi być asocjacyjnych i przemienne.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynik końcowy łączenia wszystkich obliczeń podrzędne prywatnego wątku.  
  
##  <a name="combine_each"></a>combine_each 

 Oblicza końcowej z zestawu obliczenia podrzędnych lokalnej wątku przez wywołanie metody obiekt Połącz podany raz na lokalnej wątku podrzędnego obliczeń. Wynik końcowy jest zgromadzonych przez obiekt funkcji.  
  
```
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ obiektu — funkcja, która będzie wywołana połączyć pojedynczy obliczeń podrzędnych lokalnej wątku.  
  
 `_FnCombine`  
 Obiekt, który służy do łączenia jednego podrzędnego obliczeń. Podpis jest `void (T)` lub `void (const T&)`, a musi być asocjacyjnych i przemienne.  
  
##  <a name="local"></a>lokalne 

 Zwraca odwołanie do obliczenia podrzędne prywatnego wątku.  
  
```
T& local();

T& local(bool& _Exists);
```  
  
### <a name="parameters"></a>Parametry  
 `_Exists`  
 Odwołanie do typu boolean. Wartość logiczna odwołuje się ten argument zostanie ustawiona do `true` Jeśli obliczenia podrzędnych już istnieje dla tego wątku i ustaw `false` Jeśli była to pierwszy podrzędny obliczeń dla tego wątku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obliczenia podrzędne prywatnego wątku.  
  
##  <a name="operator_eq"></a>operator = 

 Przypisuje `combinable` obiektu z innego `combinable` obiektu.  
  
```
combinable& operator= (const combinable& _Copy);
```  
  
### <a name="parameters"></a>Parametry  
 `_Copy`  
 Istniejące `combinable` kopiowanego do tego obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `combinable` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
