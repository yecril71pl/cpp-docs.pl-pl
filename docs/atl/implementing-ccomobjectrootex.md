---
title: Implementowanie klasy CComObjectRootEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CComObjectRootEx
dev_langs:
- C++
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f91346febbb84ab7c1978740e0cbc6f0c43cbb4b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052637"
---
# <a name="implementing-ccomobjectrootex"></a>Implementowanie klasy CComObjectRootEx

[Klasy CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) ma zasadnicze znaczenie; wszystkie obiekty ATL muszą mieć jedno wystąpienie `CComObjectRootEx` lub [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) w ich dziedziczenia. `CComObjectRootEx` udostępnia domyślną `QueryInterface` mechanizm oparte na wpisy mapy COM.

Za pomocą jego mapy interfejsu COM interfejsy obiektu są widoczne dla klienta, gdy klient wysyła zapytanie do interfejsu. Zapytanie jest wykonywane za pośrednictwem `CComObjectRootEx::InternalQueryInterface`. `InternalQueryInterface` obsługuje tylko interfejsów COM tabeli mapy.

Możesz wprowadzić interfejsy do tabeli mapy modelu COM z [com_interface_entry —](reference/com-interface-entry-macros.md#com_interface_entry) — makro lub jedna z jej wariantów. Na przykład, poniższy kod wprowadza interfejsy `IDispatch`, `IBeeper`, i `ISupportErrorInfo` do tabeli mapy COM:

[!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]

## <a name="see-also"></a>Zobacz też

[Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Makra mapy modelu COM](../atl/reference/com-map-macros.md)

