---
title: Implementing CComObjectRootEx
ms.date: 11/04/2016
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
ms.openlocfilehash: 80ce9936546b936770d8dedd0ba55f8c05617d37
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809759"
---
# <a name="implementing-ccomobjectrootex"></a>Implementing CComObjectRootEx

[Klasy CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) ma zasadnicze znaczenie; wszystkie obiekty ATL muszą mieć jedno wystąpienie `CComObjectRootEx` lub [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) w ich dziedziczenia. `CComObjectRootEx` udostępnia domyślną `QueryInterface` mechanizm oparte na wpisy mapy COM.

Za pomocą jego mapy interfejsu COM interfejsy obiektu są widoczne dla klienta, gdy klient wysyła zapytanie do interfejsu. Zapytanie jest wykonywane za pośrednictwem `CComObjectRootEx::InternalQueryInterface`. `InternalQueryInterface` obsługuje tylko interfejsów COM tabeli mapy.

Możesz wprowadzić interfejsy do tabeli mapy modelu COM z [com_interface_entry —](reference/com-interface-entry-macros.md#com_interface_entry) — makro lub jedna z jej wariantów. Na przykład, poniższy kod wprowadza interfejsy `IDispatch`, `IBeeper`, i `ISupportErrorInfo` do tabeli mapy COM:

[!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]

## <a name="see-also"></a>Zobacz także

[Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Makra mapy modelu COM](../atl/reference/com-map-macros.md)
