---
title: Właściwości i klasy strony właściwości (ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.properties
helpviewer_keywords:
- property pages, classes
- properties [ATL], classes
- properties [ATL]
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
ms.openlocfilehash: f5d318cecc527d0c41124ccf14326ea308007b1d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290472"
---
# <a name="properties-and-property-pages-classes"></a>Właściwości i klasy strony właściwości

Następujące klasy obsługują właściwości i strony właściwości:

- [CComDispatchDriver](../atl/reference/atl-typedefs.md#ccomdispatchdriver) pobiera lub ustawia właściwości obiektu za pomocą `IDispatch` wskaźnika.

- [CStockPropImpl](../atl/reference/cstockpropimpl-class.md) implementuje właściwości podstawowe obsługiwane przez ATL.

- [IPerPropertyBrowsingImpl](../atl/reference/iperpropertybrowsingimpl-class.md) uzyskuje dostęp do informacji na stronach właściwości obiektu.

- [IPersistPropertyBagImpl](../atl/reference/ipersistpropertybagimpl-class.md) właściwości obiektu są przechowywane w zbiorze właściwości dostarczonych przez klienta.

- [IPropertyPageImpl](../atl/reference/ipropertypageimpl-class.md) zarządza określoną stronę właściwości w arkuszu właściwości.

- [IPropertyPage2Impl](../atl/reference/ipropertypage2impl-class.md) podobnie jak `IPropertyPageImpl`, ale również umożliwia klientowi wybrać określoną właściwość na stronie właściwości.

- [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md) uzyskuje CLSID dla stron właściwości obsługiwanych przez obiekt.

## <a name="related-articles"></a>Powiązane artykuły

[ALT — samouczek](../atl/active-template-library-atl-tutorial.md)

[Strony właściwości ALT COM](../atl/atl-com-property-pages.md)

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../atl/atl-class-overview.md)<br/>
[Makra mapy właściwości](../atl/reference/property-map-macros.md)
