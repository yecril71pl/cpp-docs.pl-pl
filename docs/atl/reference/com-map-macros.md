---
title: Makra mapy COM | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
dev_langs: C++
helpviewer_keywords: COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5493d2a1777b999dd13f2fe295b9ee9192580d33
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="com-map-macros"></a>Makra mapy COM
Te makra zdefiniuj mapy interfejsu COM.  
  
|||  
|-|-|  
|[BEGIN_COM_MAP](#begin_com_map)|Oznacza początek wpisy mapy interfejsu COM.|  
|[END_COM_MAP](#end_com_map)|Oznacza koniec wpisy mapy interfejsu COM.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
   
##  <a name="begin_com_map"></a>BEGIN_COM_MAP  
 Mapa COM jest mechanizm, który udostępnia interfejsy na obiekt, aby klienta za pośrednictwem `QueryInterface`.  
  
```
BEGIN_COM_MAP(x)
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Nazwa obiektu klasy, które interfejsy są udostępnianie na.  
  
### <a name="remarks"></a>Uwagi  
 [CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) tylko zwraca wskaźników interfejsów w mapie modelu COM. Uruchom mapy interfejsu z `BEGIN_COM_MAP` makra, dodanie wpisów dla poszczególnych interfejsów z [com_interface_entry —](com-interface-entry-macros.md#com_interface_entry) makro lub jednej z jej wariantów i ukończyć mapy [END_COM_MAP](#end_com_map) makra.  

  
### <a name="example"></a>Przykład  
 Z ATL [BEEPER](../../visual-cpp-samples.md) próbki:  
  
 [!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  

  
##  <a name="end_com_map"></a>END_COM_MAP  
 Kończy definicję mapy interfejsu COM.  
  
```
END_COM_MAP()
```  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)   
 [Funkcje globalne mapie modelu COM](../../atl/reference/com-map-global-functions.md)
