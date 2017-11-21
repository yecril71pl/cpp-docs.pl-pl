---
title: Klasa CComObjectRoot | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
dev_langs: C++
helpviewer_keywords: CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c2dc617eeb58594262ea272a0a4ef7da2865b73f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccomobjectroot-class"></a>Klasa CComObjectRoot
Ten element typedef z [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) którego jest ma zastosowany szablon domyślny model serwera wątków.  
  
## <a name="syntax"></a>Składnia  
  
```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```  
  
## <a name="remarks"></a>Uwagi  
 `CComObjectRoot`jest `typedef` z [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) którego ma zastosowany szablon domyślny model serwera wątków. W związku z tym [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) będzie odwoływać się albo [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md).  
  
 `CComObjectRootEx`obsługuje zarządzanie liczba odwołanie do obiektu zarówno nieagregowane zagregowane obiekty i. Jeśli obiekt nie jest agregowana i przechowuje wskaźnik do nieznanego zewnętrzne, jeśli obiekt jest agregowana posiada liczebności referencyjnej obiektu. Zagregowane obiekty `CComObjectRootEx` metody może służyć do obsługi błędów wewnętrzny obiekt w celu utworzenia i ochrony obiektu zewnętrznego przed usunięciem po udostępnieniu wewnętrzny interfejsów lub wewnętrzny obiekt jest usunięty.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy CComObjectRootEx klas](http://msdn.microsoft.com/en-us/e3ce9c3d-9c8e-4fe5-b682-8e56740a0164)   
 [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
 [Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)   
 [Element CComObject — klasa](../../atl/reference/ccomobject-class.md)   
 [Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
