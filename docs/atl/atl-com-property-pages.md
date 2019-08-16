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
ms.openlocfilehash: f6f549388e69e9549c64645de758d92822205fd5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491856"
---
# <a name="atl-com-property-pages"></a>Strony właściwości ALT COM

Strony właściwości COM udostępniają interfejs użytkownika do ustawiania właściwości (lub wywoływania metod) jednego lub większej liczby obiektów COM. Strony właściwości są szeroko używane przez kontrolki ActiveX do udostępniania bogatych interfejsów użytkownika, które umożliwiają ustawianie właściwości formantu w czasie projektowania.

Strony właściwości to obiekty COM implementujące interfejs [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) lub [IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) . Te interfejsy zapewniają metody, które pozwalają na skojarzenie strony z `site` (obiekt com reprezentujący kontener strony) i wiele *obiektów* (obiekty com, których metody będą wywoływane w odpowiedzi na zmiany wprowadzone przez użytkownika Strona właściwości). Kontener strony właściwości jest odpowiedzialny za wywoływanie metod w interfejsie strony właściwości, aby określić, kiedy ma być wyświetlana lub Ukryta jego interfejs użytkownika, oraz kiedy zastosować zmiany wprowadzone przez użytkownika do obiektów bazowych.

Każda Strona właściwości może być skompilowana całkowicie niezależnie od obiektów, których właściwości można ustawić. Wszystko, co jest potrzebne na stronie właściwości, ma zrozumieć konkretny interfejs (lub zestaw interfejsów) i zapewnia interfejs użytkownika do wywoływania metod w tym interfejsie.

Aby uzyskać więcej informacji, zobacz [arkusze właściwości i strony właściwości](/windows/win32/com/property-sheets-and-property-pages) w Windows SDK.

## <a name="in-this-section"></a>W tej sekcji

[Określanie stron właściwości](../atl/specifying-property-pages.md)<br/>
Wyświetla listę kroków służących do określania stron właściwości na potrzeby kontroli i pokazuje przykładową klasę.

[Implementowanie stron właściwości](../atl/implementing-property-pages.md)<br/>
Zawiera instrukcje dotyczące implementowania stron właściwości, w tym metod przesłonięcia. Przeprowadzi Cię przez kompletny przykład w oparciu o Przykładowy program ATLPages.

## <a name="related-sections"></a>Sekcje pokrewne

[Przykład ATLPages](../overview/visual-cpp-samples.md)<br/>
Przykładowa abstract dla przykładu ATLPages, który implementuje stronę właściwości przy użyciu `IPropertyPageImpl`.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Zawiera łącza do tematów koncepcyjnych dotyczących sposobu programowania przy użyciu Active Template Library.

## <a name="see-also"></a>Zobacz także

[Pojęcia](../atl/active-template-library-atl-concepts.md)
