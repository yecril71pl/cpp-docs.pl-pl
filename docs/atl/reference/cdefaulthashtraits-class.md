---
title: Klasa CDefaultHashTraits | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
dev_langs: C++
helpviewer_keywords: CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2407ffdd5d8ea327cd4669f2c33ccda5e0246d6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdefaulthashtraits-class"></a>Klasa CDefaultHashTraits
Ta klasa udostępnia funkcję statyczną do obliczania wartości skrótu.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename T>  
class CDefaultHashTraits
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych ma być przechowywany w kolekcji.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDefaultHashTraits::Hash](#hash)|(Statyczny) Wywołanie tej funkcji, aby obliczyć wartość skrótu dla danego elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa zawiera pojedynczy statycznej funkcji, która zwraca wartość skrótu dla danego elementu. Ta klasa jest wykorzystywany przez [CDefaultElementTraits klasy](../../atl/reference/cdefaultelementtraits-class.md).  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="hash"></a>CDefaultHashTraits::Hash  
 Wywołanie tej funkcji, aby obliczyć wartość skrótu dla danego elementu.  
  
```
static ULONG Hash(const T& element) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `element`  
 Element.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość skrótu.  
  
### <a name="remarks"></a>Uwagi  
 Wartość domyślna algorytmem wyznaczania wartości skrótu jest bardzo prosta: wartość zwracana jest liczba elementów. Należy przesłonić tę funkcję, jeśli wymagana jest bardziej skomplikowany algorytmu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
