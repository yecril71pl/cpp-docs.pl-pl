---
title: "max_variable_size — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
dev_langs: C++
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 425a93ff12aad138ff2c539765f9afeeb2f22756
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="maxvariablesize-class"></a>max_variable_size — Klasa
W tym artykule opisano [maksymalnej liczby klasy](../standard-library/allocators-header.md) obiekt, który ogranicza [elementu freelist](../standard-library/freelist-class.md) obiektu maksymalną długość, który jest około proporcjonalny do liczby przydzielonych bloków pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```
class max_variable_size
```  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[max_variable_size —](#max_variable_size)|Tworzy obiekt typu `max_variable_size`.|  
  
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
  
##  <a name="allocated"></a>max_variable_size::allocated  
 Zwiększa liczbę bloków alokacji pamięci.  
  
```
void allocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`_Nx`|Wartość przyrostu.|  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska dodaje `_Nx` przechowywanej wartości `_Nallocs`. Ta funkcja elementu członkowskiego jest wywoływana po każdym pomyślnym wywołaniem przez `cache_freelist::allocate` operator `new`. Argument `_Nx` jest to liczba bloków pamięci we fragmencie przydzielone przez operatora `new`.  
  
##  <a name="deallocated"></a>max_variable_size::deallocated  
 Zmniejsza liczbę przydzielonych bloków pamięci.  
  
```
void deallocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`_Nx`|Wartość przyrostu.|  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska odejmuje `_Nx` z wartością przechowywaną `_Nallocs`. Ta funkcja elementu członkowskiego jest wywoływana po każdym wywołania `cache_freelist::deallocate` operator `delete`. Argument `_Nx` jest to liczba bloków pamięci we fragmencie alokację przez operatora `delete`.  
  
##  <a name="full"></a>max_variable_size::Full  
 Zwraca wartość, która określa, czy należy dodać więcej bloków pamięci do wolnego listy.  
  
```
bool full();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli `_Nallocs / 16 + 16 <= _Nblocks`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate`. Jeśli wywołanie zwraca `true`, `deallocate` umieszcza blok pamięci na liście wolnego; Jeśli zwraca wartość false, `deallocate` operator wywołania `delete` można cofnąć alokacji bloku.  
  
##  <a name="max_variable_size"></a>max_variable_size::max_variable_size  
 Tworzy obiekt typu `max_variable_size`.  
  
```
max_variable_size();
```  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor inicjuje przechowywane wartości `_Nblocks` i `_Nallocs` od zera.  
  
##  <a name="released"></a>max_variable_size::released  
 Zmniejsza liczbę pamięci blokuje na liście wolne.  
  
```
void released();
```  
  
### <a name="remarks"></a>Uwagi  
 Ten element członkowski funkcji zmniejsza przechowywana wartość `_Nblocks`. `released` Funkcji członkowskiej klasy bieżący maksymalny jest wywoływana przez `cache_freelist::allocate` po każdej zmianie Usuwa blok pamięci z wolnego listy.  
  
##  <a name="saved"></a>max_variable_size::Saved  
 Zwiększa liczbę bloków pamięci na liście wolne.  
  
```
void saved();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego zwiększa przechowywana wartość `_Nblocks`. Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate` zawsze, gdy blok pamięci są umieszczane na liście wolne.  
  
## <a name="see-also"></a>Zobacz też  
 [\<allocators — >](../standard-library/allocators-header.md)



