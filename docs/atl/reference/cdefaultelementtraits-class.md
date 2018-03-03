---
title: Klasa CDefaultElementTraits | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb6731913d10402016f2148e1ae7705a73e98944
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdefaultelementtraits-class"></a>Klasa CDefaultElementTraits
Ta klasa dostarcza metody domyślnej i funkcji do klasy kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T>  
class CDefaultElementTraits : public CElementTraitsBase<T>,
    public CDefaultHashTraits<T>,
    public CDefaultCompareTraits<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych ma być przechowywany w kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa udostępnia domyślny statyczne funkcje i metody przenoszenia, kopiowania, porównanie i wyznaczania wartości skrótu elementy przechowywane w obiekcie klasy kolekcji. Ta klasa dziedziczy jego funkcje i metody z [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md), [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md), i [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)i jest wykorzystywany przez [ CElementTraits](../../atl/reference/celementtraits-class.md), [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md), i [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md).  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
