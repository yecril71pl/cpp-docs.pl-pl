---
title: Klasa CInterfaceList | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 33cfcc072e000bc903cceb4ac5551071e35610d9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884379"
---
# <a name="cinterfacelist-class"></a>Klasa CInterfaceList
Ta klasa dostarcza metody przydatne podczas tworzenia listy wskaźniki interfejsu COM.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class I, const IID* piid =& __uuidof(I)>  
class CInterfaceList 
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>Parametry  
 *I*  
 Interfejs COM, określając typ wskaźnika, które mają być przechowywane.  
  
 *piid*  
 Wskaźnik do identyfikatora IID z *I*.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInterfaceList::CInterfaceList](#cinterfacelist)|Konstruktor dla listy interfejsu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa zawiera konstruktora i pochodnej metody do tworzenia list wskaźniki interfejsu COM. Użyj [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) gdy tablica jest wymagana.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CInterfaceList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="cinterfacelist"></a>  CInterfaceList::CInterfaceList  
 Konstruktor dla listy interfejsu.  
  
```
CInterfaceList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nBlockSize*  
 Rozmiar bloku z domyślną 10.  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar bloku jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszają liczbę interwencji do procedur alokacji pamięci, ale używa więcej zasobów.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlList](../../atl/reference/catllist-class.md)   
 [Klasa CComQIPtr](../../atl/reference/ccomqiptr-class.md)   
 [Klasa CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
