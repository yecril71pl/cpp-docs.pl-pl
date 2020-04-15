---
title: Identyfikowanie elementów projektu sterowania DHTML
ms.date: 11/19/2018
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
ms.openlocfilehash: 5fabdc815989c21bdf6b0932b9d6826e28d7012a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319506"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Identyfikowanie elementów projektu sterowania DHTML

Większość kodu sterującego DHTML jest dokładnie taka, jak ta utworzona dla dowolnego formantu ATL. Aby uzyskać podstawową wiedzę na temat ogólnego kodu, przejrzyj [samouczek ATL](../atl/active-template-library-atl-tutorial.md)i przeczytaj sekcje [Tworzenie projektu ATL](../atl/reference/creating-an-atl-project.md) i [podstaw obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md).

Formant DHTML jest podobny do dowolnego formantu ATL, z wyjątkiem:

- Oprócz regularnych interfejsów implementuje formantu, implementuje dodatkowy interfejs, który jest używany do komunikowania się między kodem C++ i interfejsu użytkownika HTML (UI). Interfejs użytkownika HTML wywołuje kod C++ przy użyciu tego interfejsu.

- Tworzy zasób HTML dla interfejsu użytkownika sterowania.

- Umożliwia dostęp do modelu obiektu DHTML `m_spBrowser`za pośrednictwem zmiennej członkowskiej, która jest inteligentnym wskaźnikiem typu [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\)). Ten wskaźnik służy do uzyskiwania dostępu do dowolnej części modelu obiektu DHTML.

Na poniższej ilustracji przedstawiono relację między biblioteką DLL, formantem DHTML, przeglądarką sieci Web i zasobem HTML.

![Elementy projektu sterowania DHTML](../atl/media/vc52en1.gif "Elementy projektu sterowania DHTML")

> [!NOTE]
> Nazwy na tej grafice są symbolami zastępczymi. Nazwy zasobu HTML i interfejsów udostępnianych w formancie są oparte na nazwach przypisanych ich w Kreatorze sterowania ATL.

W tej grafice elementy są:

- **Moja biblioteka DLL** Biblioteka DLL utworzona za pomocą Kreatora projektów ATL.

- **Kontrola DHTML** (`m_spBrowser`) Formant DHTML utworzony za pomocą Kreatora obiektów ATL. Ten formant uzyskuje dostęp do obiektu przeglądarki sieci Web i `IWebBrowser2`jej metod za pośrednictwem interfejsu obiektu przeglądarki sieci Web. Sam formant udostępnia następujące dwa interfejsy, oprócz innych standardowych interfejsów wymaganych do formantu.

  - `IDHCTL1`Interfejs udostępniane przez formant do użytku tylko przez kontener.

  - `IDHCTLUI1`Interfejs wysyłki do komunikacji między kodem C++ a interfejsem użytkownika HTML. Przeglądarka sieci Web używa interfejsu wysyłki formantu do wyświetlania formantu. Można wywołać różne metody tego interfejsu wysyłki z interfejsu `window.external`użytkownika formantu, wywołując , a następnie nazwę metody w tym interfejsie wysyłki, który chcesz wywołać. Dostęp można `window.external` uzyskać z tagu SCRIPT w html, który tworzy interfejs użytkownika dla tego formantu. Aby uzyskać więcej informacji na temat wywoływania metod zewnętrznych w pliku zasobów, zobacz [Wywoływanie kodu C++ z pliku DHTML](../atl/calling-cpp-code-from-dhtml.md).

- **IDR_CTL1** Identyfikator zasobu HTML. Jego nazwa pliku, w tym przypadku, jest DHCTL1UI.htm. Formant DHTML używa zasobu HTML zawierającego standardowe znaczniki HTML i polecenia wysyłania okien zewnętrznych, które można edytować za pomocą edytora tekstu.

- **Przeglądarka internetowa** Przeglądarka sieci Web wyświetla interfejs użytkownika formantu na podstawie kodu HTML w zasobie HTML. Wskaźnik do `IWebBrowser2` interfejsu przeglądarki sieci Web jest dostępny w formancie DHTML, aby umożliwić dostęp do modelu obiektu DHTML.

Kreator sterowania ATL generuje formant z domyślnym kodem zarówno w zasobie HTML, jak i w pliku cpp. Formant można skompilować i uruchomić jako wygenerowany przez kreatora, a następnie wyświetlić formant w przeglądarce sieci Web lub kontenerze testowym kontroli ActiveX. Poniższy obraz przedstawia domyślny kontrolka DHTML ATL z trzema przyciskami wyświetlanymi w kontenerze testowym:

![Sterowanie DHTML ATL](../atl/media/vc52en2.gif "Sterowanie DHTML ATL")

Zobacz [Tworzenie formantu DHTML ATL,](../atl/creating-an-atl-dhtml-control.md) aby rozpocząć tworzenie formantu DHTML. Zobacz [testowanie właściwości i zdarzenia z kontenerem testowym,](../mfc/testing-properties-and-events-with-test-container.md) aby uzyskać informacje na temat uzyskiwania dostępu do kontenera testowego.

## <a name="see-also"></a>Zobacz też

[Obsługa kontroli DHTML](../atl/atl-support-for-dhtml-controls.md)
