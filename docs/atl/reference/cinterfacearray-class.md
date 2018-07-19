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
ms.openlocfilehash: c33e0783acfba1b460894ac8f5dde80e61780762
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882724"
---
# <a name="cinterfacearray-class"></a>Klasa CInterfaceArray
Ta klasa dostarcza metody przydatne przy konstruowaniu tablicy wskaźników interfejsu COM.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class I, const IID* piid=& __uuidof(I)>  
class CInterfaceArray : 
   public CAtlArray<ATL::CComQIPtr<I, piid>,
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
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|Konstruktor dla tablicy interfejsu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa zawiera konstruktora i pochodnej metody tworzenia tablicy wskaźników interfejsu COM. Użyj [CInterfaceList](../../atl/reference/cinterfacelist-class.md) gdy lista jest wymagana.  
  
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
 Inicjuje tablicę inteligentnego wskaźnika.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlArray](../../atl/reference/catlarray-class.md)   
 [Klasa CComQIPtr](../../atl/reference/ccomqiptr-class.md)   
 [Klasa CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
