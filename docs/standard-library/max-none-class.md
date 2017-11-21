---
title: "max_none — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
dev_langs: C++
helpviewer_keywords:
- stdext::max_none
- stdext::max_none [C++], allocated
- stdext::max_none [C++], deallocated
- stdext::max_none [C++], full
- stdext::max_none [C++], released
- stdext::max_none [C++], saved
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3a1d8f9a133c2ad07fbd46113d7e90d58066993c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[przydzielone](#allocated)|Zwiększa liczbę bloków alokacji pamięci.|  
|[cofnięcie przydziału](#deallocated)|Zmniejsza liczbę przydzielonych bloków pamięci.|  
|[Pełna](#full)|Zwraca wartość, która określa, czy należy dodać więcej bloków pamięci do wolnego listy.|  
|[wydane](#released)|Zmniejsza liczbę pamięci blokuje na liście wolne.|  
|[zapisane](#saved)|Zwiększa liczbę bloków pamięci na liście wolne.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<allocators — >  
  
 **Namespace:** stdext —  
  
##  <a name="allocated"></a>max_none::allocated  
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
  
##  <a name="deallocated"></a>max_none::deallocated  
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
  
##  <a name="full"></a>max_none::Full  
 Zwraca wartość, która określa, czy należy dodać więcej bloków pamięci do wolnego listy.  
  
```
bool full();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta funkcja członkowska zawsze zwraca `true`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate`. Jeśli wywołanie zwraca `true`, `deallocate` umieszcza blok pamięci na liście wolnego; Jeśli zwraca wartość false, `deallocate` operator wywołania `delete` można cofnąć alokacji bloku.  
  
##  <a name="released"></a>max_none::released  
 Zmniejsza liczbę pamięci blokuje na liście wolne.  
  
```
void released();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska nie działa. `released` Funkcji członkowskiej klasy bieżący maksymalny jest wywoływana przez `cache_freelist::allocate` po każdej zmianie Usuwa blok pamięci z wolnego listy.  
  
##  <a name="saved"></a>max_none::Saved  
 Zwiększa liczbę bloków pamięci na liście wolne.  
  
```
void saved();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska nie działa. Jest ona wywoływana przez `cache_freelist::deallocate` zawsze, gdy blok pamięci są umieszczane na liście wolne.  
  
## <a name="see-also"></a>Zobacz też  
 [\<allocators — >](../standard-library/allocators-header.md)



