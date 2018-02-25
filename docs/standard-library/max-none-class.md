---
title: "max_none — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
dev_langs:
- C++
helpviewer_keywords:
- stdext::max_none
- stdext::max_none [C++], allocated
- stdext::max_none [C++], deallocated
- stdext::max_none [C++], full
- stdext::max_none [C++], released
- stdext::max_none [C++], saved
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db65e89f0079c56929359c6130ad2b8342752bc9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="maxnone-class"></a>max_none — Klasa
W tym artykule opisano [maksymalnej liczby klasy](../standard-library/allocators-header.md) obiekt, który ogranicza [elementu freelist](../standard-library/freelist-class.md) obiektu maksymalną długość równą zero.  
  
## <a name="syntax"></a>Składnia  
  
```
template <std::size_t Max>  
class max_none
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Max`|Max klasy, która określa maksymalną liczbę elementów, które mają być przechowywane w `freelist`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Przydzielone](#allocated)|Zwiększa liczbę bloków alokacji pamięci.|  
|[Cofnięcie przydziału](#deallocated)|Zmniejsza liczbę przydzielonych bloków pamięci.|  
|[full](#full)|Zwraca wartość, która określa, czy należy dodać więcej bloków pamięci do wolnego listy.|  
|[Wydane](#released)|Zmniejsza liczbę pamięci blokuje na liście wolne.|  
|[zapisane](#saved)|Zwiększa liczbę bloków pamięci na liście wolne.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<allocators — >  
  
 **Namespace:** stdext —  
  
##  <a name="allocated"></a>  max_none::allocated  
 Zwiększa liczbę bloków alokacji pamięci.  
  
```
void allocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`_Nx`|Wartość przyrostu.|  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska nie działa. Jest ona wywoływana po każdym pomyślnym wywołaniem przez `cache_freelist::allocate` operator `new`. Argument `_Nx` jest to liczba bloków pamięci we fragmencie przydzielone przez operatora `new`.  
  
##  <a name="deallocated"></a>  max_none::deallocated  
 Zmniejsza liczbę przydzielonych bloków pamięci.  
  
```
void deallocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`_Nx`|Wartość przyrostu.|  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska nie działa. Ta funkcja elementu członkowskiego jest wywoływana po każdym wywołania `cache_freelist::deallocate` operator `delete`. Argument `_Nx` jest to liczba bloków pamięci we fragmencie alokację przez operatora `delete`.  
  
##  <a name="full"></a>  max_none::Full  
 Zwraca wartość, która określa, czy należy dodać więcej bloków pamięci do wolnego listy.  
  
```
bool full();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta funkcja członkowska zawsze zwraca `true`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate`. Jeśli wywołanie zwraca `true`, `deallocate` umieszcza blok pamięci na liście wolnego; Jeśli zwraca wartość false, `deallocate` operator wywołania `delete` można cofnąć alokacji bloku.  
  
##  <a name="released"></a>  max_none::released  
 Zmniejsza liczbę pamięci blokuje na liście wolne.  
  
```
void released();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska nie działa. `released` Funkcji członkowskiej klasy bieżący maksymalny jest wywoływana przez `cache_freelist::allocate` po każdej zmianie Usuwa blok pamięci z wolnego listy.  
  
##  <a name="saved"></a>  max_none::Saved  
 Zwiększa liczbę bloków pamięci na liście wolne.  
  
```
void saved();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska nie działa. Jest ona wywoływana przez `cache_freelist::deallocate` zawsze, gdy blok pamięci są umieszczane na liście wolne.  
  
## <a name="see-also"></a>Zobacz też  
 [\<allocators>](../standard-library/allocators-header.md)



