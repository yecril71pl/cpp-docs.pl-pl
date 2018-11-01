---
title: Strony właściwości ALT COM
ms.date: 11/04/2016
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
ms.openlocfilehash: 5bc17bfc415576d50c84e880bef955e49d926c86
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595562"
---
# <a name="atl-com-property-pages"></a>Strony właściwości ALT COM

Strony właściwości COM udostępniają interfejs użytkownika do ustawiania właściwości (lub wywoływania metod) jeden lub więcej obiektów COM. Strony właściwości są często używane przez formanty ActiveX zapewniające bogatych interfejsów użytkownika umożliwiające właściwości formantu należy ustawić w czasie projektowania.

Strony właściwości są obiektów COM, które implementują [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) lub [IPropertyPage2](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage2) interfejsu. Te interfejsy, zapewniają metody, które umożliwiają strony do skojarzenia z `site` (obiekt COM reprezentujący kontener strony) i liczbę *obiektów* (obiekty COM metod, których zostanie wywołana w odpowiedzi na zmiany wprowadzone przez użytkownika na stronie właściwości). Kontener strony właściwości jest odpowiedzialny za wywoływanie metod na interfejsie strony właściwości sprawdzić na stronie, gdy pokazać lub ukryć jego interfejs użytkownika i kiedy należy zastosować zmiany wprowadzone przez użytkownika do obiektów.

Każdą stronę właściwości mogą być wbudowane w całkowicie niezależnie od obiektów, których właściwości można ustawić. Wszystko to strona właściwości jest wymaga, aby zrozumieć określonego interfejsu (lub zestawu interfejsów) i udostępniają interfejs użytkownika na potrzeby wywoływania metod, w tym interfejsie.

Aby uzyskać więcej informacji, zobacz [arkusze właściwości i strony właściwości](/windows/desktop/com/property-sheets-and-property-pages) w zestawie Windows SDK.

## <a name="in-this-section"></a>W tej sekcji

[Określanie stron właściwości](../atl/specifying-property-pages.md)<br/>
Lista czynności prowadzących do określanie stron właściwości dla sterować i przedstawia przykład klasy.

[Implementowanie stron właściwości](../atl/implementing-property-pages.md)<br/>
Lista czynności prowadzących do Implementowanie stron właściwości, włączając w to metody do przesłonięcia. Przeprowadzi Cię przez kompletny przykład, w oparciu o ATLPages przykładowy program.

## <a name="related-sections"></a>Sekcje pokrewne

[Przykładowe ATLPages](../visual-cpp-samples.md)<br/>
Abstrakcyjny próbki dla przykładu ATLPages, która implementuje stronę właściwości przy użyciu `IPropertyPageImpl`.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Zawiera łącza do tematów pojęciowych dotyczące programowania przy użyciu biblioteki Active Template Library.

## <a name="see-also"></a>Zobacz też

[Pojęcia](../atl/active-template-library-atl-concepts.md)

