---
title: Klasa CDefaultHashTraits | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
dev_langs:
- C++
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85cf9e27211763559617715a6c025055b25379fa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
  
##  <a name="hash"></a>  CDefaultHashTraits::Hash  
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
