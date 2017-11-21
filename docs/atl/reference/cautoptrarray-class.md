---
title: Klasa CAutoPtrArray | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
dev_langs: C++
helpviewer_keywords: CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 952f6a6d9fa06c0f0c34e5769b4302c6230abb43
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cautoptrarray-class"></a>Klasa CAutoPtrArray
Ta klasa dostarcza metody przydatne podczas konstruowania tablicę wskaźniki inteligentne.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```  
  
#### <a name="parameters"></a>Parametry  
 `E`  
 Typ wskaźnika.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|Konstruktor.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa zawiera konstruktora i pochodzi z metody [CAtlArray](../../atl/reference/catlarray-class.md) i [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) ułatwiających tworzenie obiektu klasy zbierania, przechowywania wskaźniki inteligentne.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CAtlArray`  
  
 `CAutoPtrArray`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="cautoptrarray"></a>CAutoPtrArray::CAutoPtrArray  
 Konstruktor.  
  
```
CAutoPtrArray() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje tablicy wskaźnika inteligentnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlArray](../../atl/reference/catlarray-class.md)   
 [Klasa CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)   
 [Klasa CAutoPtrList](../../atl/reference/cautoptrlist-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
