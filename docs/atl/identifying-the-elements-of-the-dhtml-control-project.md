---
title: Określający elementy projektu kontroli DHTML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 525ad4e073607064234641f6544a11901ded0096
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357685"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Określający elementy projektu kontroli DHTML
Większość kodu kontroli DHTML dokładnie tak samo, jak to jest tworzony dla każdego formantu ATL. Dla podstawy Kod rodzajowy pracy za pośrednictwem [ALT — samouczek](../atl/active-template-library-atl-tutorial.md), i odczytywane sekcji [tworzenie Projekt ATL](../atl/reference/creating-an-atl-project.md) i [podstawy ATL obiektów COM](../atl/fundamentals-of-atl-com-objects.md).  
  
 Formant DHTML jest podobny do żadnego formantu ATL z wyjątkiem:  
  
-   Oprócz regularnych interfejsów, które implementuje formantu implementuje interfejs dodatkowych, który jest używany do komunikacji między kodem C++ i HTML interfejsu użytkownika (UI). Wywołanie interfejsu użytkownika HTML do kodu C++ przy użyciu tego interfejsu.  
  
-   Tworzy zasób języka HTML dla formantu interfejsu użytkownika.  
  
-   Zezwala na dostęp do modelu obiektów DHTML za pośrednictwem zmiennej członkowskiej `m_spBrowser`, która jest typu wskaźnika inteligentnego [IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx). Umożliwia dostęp do dowolnej części model obiektowy DHTML ten wskaźnik.  
  
 Poniższa ilustracja przedstawia relację między biblioteki DLL, DHTML formant przeglądarki sieci Web i zasobu HTML.  
  
 ![Elementy projektu kontroli DHTML](../atl/media/vc52en1.gif "vc52en1")  
  
> [!NOTE]
>  W tym grafiki są symbole zastępcze. Nazwy zasobu HTML i interfejsy widoczne formantu są oparte na nazwy, które można przypisać w Kreator formantu ATL.  
  
 W tej grafiki dostępne są następujące elementy:  
  
-   **Moje DLL** bibliotece utworzonych za pomocą kreatora Projekt ATL DLL.  
  
-   **Formant DHTML** (`m_spBrowser`) formantu DHTML, utworzonych za pomocą Kreatora obiekt ATL. Ten formant uzyskuje dostęp do obiektu przeglądarki sieci Web i jego metody za pomocą interfejsu obiektu przeglądarki sieci Web, **IWebBrowser2**. Formancie uwidacznia następujące dwa interfejsy, oprócz innych standardowych interfejsów wymaganych do formantu.  
  
    -   **IDHCTL1** interfejs udostępniany przez formant do użytku w kontenerze.  
  
    -   **IDHCTLUI1** interfejs wysyłania dla komunikacji między kodem C++ i interfejsu użytkownika HTML. Przeglądarka sieci Web używa kontrolki interfejs wysyłania do wyświetlania formantu. Różne metody tego interfejsu wysyłania można wywołać z formantu interfejsu użytkownika, wywołując `window.external`, a następnie nazwę metody w tym interfejsie wysyłania, który chcesz wywołać. Czy dostępu `window.external` z tagu skryptu w języku HTML, tworzącą interfejsu użytkownika dla tego formantu. Aby uzyskać więcej informacji na temat wywoływania metod zewnętrznego pliku zasobu, zobacz [wywoływania kodu C++ z DHTML](../atl/calling-cpp-code-from-dhtml.md).  
  
-   **IDR_CTL1** zasobów identyfikator zasobu HTML. Nazwa pliku, w tym przypadku jest DHCTL1UI.htm. Formant DHTML używa zasobu HTML, który zawiera standardowych znaczników HTML i ewnętrznym oknie wysyłania poleceń, które można edytować za pomocą edytora tekstu.  
  
-   **Przeglądarki sieci Web** przeglądarki sieci Web Wyświetla formantu interfejsu użytkownika, oparte na kodzie HTML w zasobie HTML. Wskaźnik do przeglądarki sieci Web **IWebBrowser2** interfejs jest dostępny w formancie DHTML, aby zezwolić na dostęp do modelu obiektu DHTML.  
  
 Kreator formantu ATL generuje formantu o domyślny kod w pliku .cpp i zasobu HTML. Można skompilować i uruchomić formantu wygenerowane przez kreatora i następnie wyświetlanie kontroli w przeglądarce sieci Web lub kontener testu formantu ActiveX. Na rysunku poniżej przedstawiono domyślne formant ATL DHTML z trzy przyciski wyświetlane w kontenerze testowym:  
  
 ![Formant ATL DHTML](../atl/media/vc52en2.gif "vc52en2")  
  
 Zobacz [tworzenia kontrolek DHTML ATL](../atl/creating-an-atl-dhtml-control.md) aby rozpocząć tworzenie formantu DHTML. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat sposobu dostępu kontener testu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa dla DHTML](../atl/atl-support-for-dhtml-controls.md)

