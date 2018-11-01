---
title: Obsługa ALT dla kontrolek DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
ms.openlocfilehash: 321c8c14f2049622b43741cfa9d856cb00e2cd61
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638688"
---
# <a name="atl-support-for-dhtml-controls"></a>Obsługa ALT dla kontrolek DHTML

Przy użyciu biblioteki ATL, można utworzyć kontrolki za pomocą funkcji dynamicznego języka HTML (DHTML). Kontrolki ATL DHTML:

- Obsługuje formant WebBrowser.

- Określa, że za pomocą kodu HTML, w interfejsie użytkownika (UI) kontrolki DHTML.

- Uzyskuje dostęp do obiektu WebBrowser i jego metod za pośrednictwem jego interfejsu [IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx).

- Zarządza komunikacją między kodem C++ i HTML.

Kontrolki DHTML jest podobny do dowolnej innej kontrolki ATL, jednak kontrolki DHTML obejmuje interfejs ekspedycji dodatkowe. Zobacz ilustrację w [identyfikowanie elementów projektu kontrolki DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) ilustrację dostarczanych w projekcie DHTML domyślne.

Kontrolki ATL DHTML można wyświetlić w przeglądarce sieci Web lub innych kontenerów, takich jak kontener testu kontrolki ActiveX.

## <a name="in-this-section"></a>W tej sekcji

[Identyfikowanie elementów projektu kontrolki DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md)<br/>
Opisano elementy projektu kontrolki DHTML.

[Wywoływanie kodu C++ z elementu DHTML](../atl/calling-cpp-code-from-dhtml.md)<br/>
Przykład wywołania kodu w języku C++ z kontrolki DHTML.

[Tworzenie kontrolki DHTML ATL](../atl/creating-an-atl-dhtml-control.md)<br/>
Lista czynności prowadzących do tworzenia kontrolki DHTML.

[Testowanie kontrolki DHTML ATL](../atl/testing-the-atl-dhtml-control.md)<br/>
Przedstawia sposób tworzenia i testowania początkowego projektu kontrolki DHTML.

[Modyfikowanie kontrolki DHTML ATL](../atl/modifying-the-atl-dhtml-control.md)<br/>
Pokazuje, jak dodawać funkcjonalność do formantu.

[Testowanie kontrolki DHTML ATL zmieniony](../atl/testing-the-modified-atl-dhtml-control.md)<br/>
Pokazuje, jak tworzyć i testować dodatkowa funkcjonalność formantu.

## <a name="related-sections"></a>Sekcje pokrewne

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Zawiera łącza do tematów pojęciowych dotyczące programowania przy użyciu biblioteki Active Template Library.

