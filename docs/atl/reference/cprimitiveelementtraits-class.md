---
title: Klasa CPrimitiveElementTraits | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
dev_langs: C++
helpviewer_keywords: CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e9713ae95e5c47f67c09ecbfc571b118f6a9989f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cprimitiveelementtraits-class"></a>Klasa CPrimitiveElementTraits
Ta klasa dostarcza metody domyślnej i funkcje do klasy kolekcji składa się z następujących typów danych pierwotnych.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T>  
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych, które mają być przechowywane w obiekcie klasy kolekcji.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|Typ danych służących do dodawania elementów do obiektu klasy kolekcji.|  
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|Typ danych używany do pobierania elementów z kolekcji klasy obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa udostępnia domyślny statyczne funkcje i metody przenoszenia, kopiowania, porównanie i tworzenia skrótów elementy typu pierwotnych danych przechowywanych w obiekcie klasy kolekcji.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CPrimitiveElementTraits`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="inargtype"></a>CPrimitiveElementTraits::INARGTYPE  
 Typ danych służących do dodawania elementów do obiektu klasy kolekcji.  
  
```
typedef T INARGTYPE;
```  
  
##  <a name="outargtype"></a>CPrimitiveElementTraits::OUTARGTYPE  
 Typ danych używany do pobierania elementów z kolekcji klasy obiektu.  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
