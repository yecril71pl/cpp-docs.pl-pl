---
title: Implementowanie CComObjectRootEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CComObjectRootEx
dev_langs:
- C++
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ae8b8266aca2c9d6099455ddcb7618206dbe8c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-ccomobjectrootex"></a>Implementowanie CComObjectRootEx
[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) niezbędnego; wszystkie obiekty ATL muszą mieć jedno wystąpienie `CComObjectRootEx` lub [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) w ich dziedziczenia. `CComObjectRootEx`udostępnia domyślne `QueryInterface` mechanizmu oparte na modelu COM wpisów map.  
  
 Za pośrednictwem jego mapy COM interfejsów obiektów są widoczne dla klientów, gdy klient wysyła zapytanie dla interfejsu. Zapytanie jest wykonywane za pośrednictwem `CComObjectRootEx::InternalQueryInterface`. `InternalQueryInterface`obsługuje tylko interfejsy COM tabeli mapy.  
  
 Interfejsy można wprowadzić do tabeli mapy COM z [com_interface_entry —](reference/com-interface-entry-macros.md#com_interface_entry) makro lub jednej z jej wariantów. Na przykład następujący kod przechodzi interfejsy `IDispatch`, `IBeeper`, i `ISupportErrorInfo` w tabeli mapowania modelu COM:  
  
 [!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje na temat ATL COM — obiekty](../atl/fundamentals-of-atl-com-objects.md)   
 [Makra mapy modelu COM](../atl/reference/com-map-macros.md)

