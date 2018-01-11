---
title: Klasa CInterfaceList | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
dev_langs: C++
helpviewer_keywords: CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5bd8817b325ebb9a9d8899211416dcbecfcd3f79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cinterfacelist-class"></a>Klasa CInterfaceList
Ta klasa dostarcza metody przydatne podczas konstruowania listy wskaźników interfejsów COM.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class I, const IID* piid =& __uuidof(I)>  
class CInterfaceList 
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>Parametry  
 `I`  
 Interfejs COM, określenie typu wskaźnika do zapisania.  
  
 `piid`  
 Wskaźnik na celu uzyskanie identyfikatora IID `I`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInterfaceList::CInterfaceList](#cinterfacelist)|Konstruktor listy interfejsów.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa udostępnia konstruktora i pochodnej metody do tworzenia listy wskaźników interfejsów COM. Użyj [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) gdy tablica jest wymagana.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CInterfaceList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="cinterfacelist"></a>CInterfaceList::CInterfaceList  
 Konstruktor listy interfejsów.  
  
```
CInterfaceList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Rozmiar bloku z domyślną 10.  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar bloku jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszyć wywołania procedury alokacji pamięci, ale użyj więcej zasobów.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlList](../../atl/reference/catllist-class.md)   
 [Klasa CComQIPtr](../../atl/reference/ccomqiptr-class.md)   
 [Klasa CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
