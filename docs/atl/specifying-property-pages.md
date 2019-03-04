---
title: Określanie stron właściwości (ATL)
ms.date: 11/04/2016
f1_keywords:
- ISpecifyPropertyPages
helpviewer_keywords:
- ISpecifyPropertyPages method
- property pages, specifying
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
ms.openlocfilehash: d738759dfba50f26b788ee1b0761baf8bc4b00ab
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287145"
---
# <a name="specifying-property-pages"></a>Określanie stron właściwości

Podczas tworzenia formantu ActiveX, często można skojarzyć go na stronach właściwości, które mogą służyć do ustawiania właściwości formantu. Kontrolowanie użycia kontenery `ISpecifyPropertyPages` interfejsu, aby dowiedzieć się, które strony właściwości może służyć do ustawiania właściwości formantu. Należy zaimplementować ten interfejs na Twoją kontrolą.

Aby zaimplementować `ISpecifyPropertyPages` przy użyciu biblioteki ATL, wykonaj następujące czynności:

1. Pochodzi z klasy [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md).

1. Dodaj wpis dla `ISpecifyPropertyPages` do mapy COM swojej klasy.

1. Dodaj [PROP_PAGE](reference/property-map-macros.md#prop_page) wpisu do map właściwości dla każdej strony skojarzonych z Twoją kontrolą.

> [!NOTE]
> Podczas generowania, za pomocą formantu standardowego [Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md), tylko trzeba będzie dodać wpisy PROP_PAGE map właściwości. Kreator generuje kod wymagane inne czynności.

Dobrze działające kontenery będą wyświetlane na stronach właściwości określonego w takiej samej kolejności jak wpisy PROP_PAGE w mapie właściwości. Ogólnie rzecz biorąc należy umieszczać wpisów stron właściwości standardowych po pozycji stron niestandardowego w mapowaniu właściwości, dzięki czemu użytkownicy zobaczą specyficzne dla formantu strony najpierw.

## <a name="example"></a>Przykład

Następujące klasy dla kalendarza kontrolować używa `ISpecifyPropertyPages` interfejsu stwierdzić, kontenery, które można ustawić jego właściwości za pomocą strony niestandardowa data i strony podstawowego koloru.

[!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/cpp/specifying-property-pages_1.h)]

## <a name="see-also"></a>Zobacz także

[Strony właściwości](../atl/atl-com-property-pages.md)<br/>
[Przykładowe ATLPages](../visual-cpp-samples.md)
