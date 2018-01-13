---
title: Klasa CInterfaceArray | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
dev_langs: C++
helpviewer_keywords: CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ece9858d0be171febaeb52e820e922665ac2a351
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
  
##  <a name="cinterfacearray"></a>CInterfaceArray::CInterfaceArray  
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
