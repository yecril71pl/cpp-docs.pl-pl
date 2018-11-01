---
title: Identyfikowanie elementów projektu kontrolki DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
ms.openlocfilehash: bb7fa67e6a3009922596c225895032bfb2f4fbb5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533695"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Identyfikowanie elementów projektu kontrolki DHTML

Większość kodu kontrolki DHTML dokładnie Krewny, który jest tworzony dla każdego formantu biblioteki ATL. Aby uzyskać podstawową wiedzę na temat kodzie rodzajowym, pracować za pośrednictwem [ALT — samouczek](../atl/active-template-library-atl-tutorial.md), i przeczytaj sekcje [Tworzenie projektu ATL](../atl/reference/creating-an-atl-project.md) i [podstawy ATL obiektów COM](../atl/fundamentals-of-atl-com-objects.md).

Kontrolki DHTML jest podobny do dowolnego formantu biblioteki ATL z wyjątkiem:

- Oprócz regularnych interfejsów, które implementuje kontrolkę implementuje dodatkowe interfejs, który jest używany do komunikacji między kodem C++ i HTML interfejsu użytkownika (UI). Wywołania interfejsu użytkownika HTML do kodu C++ przy użyciu tego interfejsu.

- Tworzy zasób HTML dla kontrolki interfejsu użytkownika.

- Umożliwia ona dostęp do model obiektowy DHTML za pośrednictwem zmiennej elementu członkowskiego `m_spBrowser`, czyli inteligentnego wskaźnika typu [IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx). Umożliwia dostęp do dowolnej części model obiektowy DHTML ten wskaźnik.

Poniższa ilustracja przedstawia relację między biblioteką DLL, kontrolki DHTML, przeglądarki sieci Web i zasobu HTML.

![Elementy projektu kontrolki DHTML](../atl/media/vc52en1.gif "vc52en1")

> [!NOTE]
>  W tym grafiki są symbole zastępcze. Nazwy zasobu HTML i interfejsów udostępnianych na formant są oparte na nazwy, które można przypisać w Kreatorze formantu ATL.

W tej grafiki dostępne są następujące elementy:

- **Moje DLL** utworzonych za pomocą Kreatora projektu ATL Biblioteka DLL.

- **Kontrolki DHTML** (`m_spBrowser`) kontrolki DHTML, utworzonych za pomocą Kreatora obiektu ATL. Ten formant uzyskuje dostęp do obiektu przeglądarki sieci Web i jego metod za pośrednictwem interfejsu obiektu przeglądarki sieci Web `IWebBrowser2`. Sama kontrolka udostępnia następujące dwa interfejsy, oprócz innych standardowe interfejsy wymagane dla formantu.

   - `IDHCTL1` Interfejs udostępnianych przez formant do użytku tylko przez kontener.

   - `IDHCTLUI1` Interfejs ekspedycji dla komunikacji między kodem C++ i interfejsu użytkownika HTML. Przeglądarka sieci Web używa interfejs ekspedycji formantu, aby wyświetlić formant. Możesz wywołać różne metody ten interfejs ekspedycji z kontrolki interfejsu użytkownika, wywołując `window.external`, a następnie nazwę metody, w tym interfejsie wysyłania, którą chcesz wywołać. Dostęp do `window.external` z tagu skryptu w języku HTML, tworzącą interfejsu użytkownika dla tego formantu. Aby uzyskać więcej informacji na temat wywoływania metody zewnętrznej w pliku zasobów, zobacz [wywoływanie kodu C++ z elementu DHTML](../atl/calling-cpp-code-from-dhtml.md).

- **IDR_CTL1** identyfikator zasobu zasobu HTML. Nazwa pliku, w tym przypadku jest DHCTL1UI.htm. Kontrolki DHTML używa zasobu HTML, który zawiera standardowych znaczników HTML i ewnętrznym oknie wysyłania poleceń, które można edytować za pomocą edytora tekstów.

- **Przeglądarki sieci Web** przeglądarki sieci Web Wyświetla Interfejsu użytkownika formantu, w oparciu o HTML w zasobie HTML. Wskaźnik do przeglądarki sieci Web `IWebBrowser2` interfejs jest dostępny w kontrolki DHTML, aby umożliwić dostęp do model obiektowy DHTML.

Kreator kontrolki ATL generuje formantu za pomocą domyślnego kodu, zarówno w przypadku zasobu HTML, jak i plik .cpp. Możesz skompilować i uruchomić kontrolki, ponieważ generowane przez kreatora i następnie wyświetlanie kontroli w przeglądarce sieci Web lub kontener testu kontrolki ActiveX. Obraz poniżej przedstawia domyślne kontrolki ATL DHTML z trzy przyciski wyświetlane na kontener testu:

![Kontrolki ATL DHTML](../atl/media/vc52en2.gif "vc52en2")

Zobacz [tworzenie kontrolki DHTML ATL](../atl/creating-an-atl-dhtml-control.md) do rozpoczęcia tworzenia kontrolki DHTML. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat dostępu do kontenera testu.

## <a name="see-also"></a>Zobacz też

[Obsługa kontrolki DHTML](../atl/atl-support-for-dhtml-controls.md)

