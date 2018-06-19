---
title: Klasa CAutoPtrArray | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b99fe8fde475453c9e6dc0b524a6b1b94821bf75
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358954"
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
  
##  <a name="cautoptrarray"></a>  CAutoPtrArray::CAutoPtrArray  
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
