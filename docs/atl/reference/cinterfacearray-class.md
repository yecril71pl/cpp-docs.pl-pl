---
title: Klasa CInterfaceArray | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36a24eadea87d0d34adf0f577b321fa16a7cfc86
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359465"
---
# <a name="cinterfacearray-class"></a>Klasa CInterfaceArray
Ta klasa dostarcza metody przydatne podczas tworzenia tablicy wskaźników interfejsów COM.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class I, const IID* piid=& __uuidof(I)>  
class CInterfaceArray : 
   public CAtlArray<ATL::CComQIPtr<I, piid>,
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
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|Konstruktor dla tablicy interfejsu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa udostępnia konstruktora i pochodnej metody tworzenia tablicy wskaźników interfejsów COM. Użyj [CInterfaceList](../../atl/reference/cinterfacelist-class.md) gdy jest wymagany.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CAtlArray`  
  
 `CInterfaceArray`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="cinterfacearray"></a>  CInterfaceArray::CInterfaceArray  
 Konstruktor.  
  
```
CInterfaceArray() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje tablicy wskaźnika inteligentnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlArray](../../atl/reference/catlarray-class.md)   
 [Klasa CComQIPtr](../../atl/reference/ccomqiptr-class.md)   
 [Klasa CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
