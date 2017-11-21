---
title: Klasa CAutoPtrList | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
dev_langs: C++
helpviewer_keywords: CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 79ca570b8f4534287ae4ec40167de3bc3d947139
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cautoptrlist-class"></a>Klasa CAutoPtrList
Ta klasa dostarcza metody przydatne podczas konstruowania listy wskaźniki inteligentne.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename E>  
class CAutoPtrList : 
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```  
  
#### <a name="parameters"></a>Parametry  
 `E`  
 Typ wskaźnika.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|Konstruktor.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa zawiera konstruktora i pochodzi z metody [CAtlList](../../atl/reference/catllist-class.md) i [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) do utworzenia obiektu listy przechowywania wskaźniki inteligentne pomocy. Klasa [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) udostępnia podobną funkcję dla obiekt array.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CAutoPtrList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="cautoptrlist"></a>CAutoPtrList::CAutoPtrList  
 Konstruktor.  
  
```
CAutoPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Rozmiar bloku z domyślną 10.  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar bloku jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszyć wywołania procedury alokacji pamięci, ale użyj więcej zasobów.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlList](../../atl/reference/catllist-class.md)   
 [Klasa CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
