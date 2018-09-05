---
title: Właściwości i właściwość strony klasy (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.properties
dev_langs:
- C++
helpviewer_keywords:
- property pages, classes
- properties [ATL], classes
- properties [ATL]
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c71ca9412c9db86421c586c0602eb8e6548df622
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766756"
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

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../atl/atl-class-overview.md)   
[Makra mapy właściwości](../atl/reference/property-map-macros.md)

