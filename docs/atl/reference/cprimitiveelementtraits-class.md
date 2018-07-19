---
title: Klasa CPrimitiveElementTraits | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2219be699e879afb6ec19ad84acc50f18d93a9a9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885812"
---
# <a name="cprimitiveelementtraits-class"></a>Klasa CPrimitiveElementTraits
Ta klasa dostarcza metody domyślne i funkcji dla klasy kolekcji składa się z pierwotnych typów danych.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T>  
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Typ danych, które mają być przechowywane w obiekcie klasy kolekcji.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|Typ danych na potrzeby dodawania elementów do obiektu klasy kolekcji.|  
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|Typ danych używany do pobierania elementów z obiektu klasy kolekcji.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa udostępnia domyślną statyczne funkcje i metody przenoszenie, kopiowanie, porównywanie i wyznaczania wartości skrótu przechowywanych w obiekcie klasy kolekcji elementy typu danych pierwotnych.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CPrimitiveElementTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="inargtype"></a>  CPrimitiveElementTraits::INARGTYPE  
 Typ danych na potrzeby dodawania elementów do obiektu klasy kolekcji.  
  
```
typedef T INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CPrimitiveElementTraits::OUTARGTYPE  
 Typ danych używany do pobierania elementów z obiektu klasy kolekcji.  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
