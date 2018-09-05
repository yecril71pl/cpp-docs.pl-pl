---
title: Wstążka Projektant (MFC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.editors.ribbon.F1
dev_langs:
- C++
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0a812ff5304288a2a7c25edeb07d76a4d06ded8
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683018"
---
# <a name="ribbon-designer-mfc"></a>Projektant wstążki (MFC)
Projektant wstążki pozwala tworzyć i dostosowywać wstążki w aplikacjach MFC. Wstążka jest element interfejsu użytkownika, który organizuje polecenia w logiczne grupy. Te grupy są wyświetlane na osobnych kartach w górnej części okna. Wstążka zastępuje pasek menu i paski narzędzi. Wstążka może znacznie zwiększyć użyteczność aplikacji. Aby uzyskać więcej informacji, zobacz [wstążek](/windows/desktop/uxguide/cmd-ribbons). Na poniższej ilustracji pokazano Wstążkę.  
  
 ![Kontrola zasobów wstążki MFC](../mfc/media/ribbon_no_callouts.png "ribbon_no_callouts")  
  
 We wcześniejszych wersjach programu Visual Studio, wstążki musiały być utworzone przez pisanie kodu, który używa klasy wstążek MFC, takich jak [klasa CMFCRibbonBar](../mfc/reference/cmfcribbonbar-class.md). W programie Visual Studio 2010 i nowszych Projektant wstążki oferuje alternatywną metodę tworzenia wstążki. Najpierw utwórz i Dostosuj Wstążkę jako zasób. Następnie załaduj zasób wstążki z kodu w aplikacji MFC. Możesz nawet użyć zasobów Wstążki i klas wstążki MFC. Na przykład można utworzyć zasób wstążki, a następnie programowo dodać więcej elementów do niej w czasie wykonywania za pomocą kodu.  
  
## <a name="understanding-the-ribbon-designer"></a>Informacje o projektancie wstążki  
 Projektant wstążki tworzy i przechowuje Wstążkę jako zasób. Kiedy tworzysz zasób wstążki, Projektant wstążki wykona te trzy rzeczy:  
  
-   Dodaje wpis w skrypcie definicji zasobów projektu (* .rc). W poniższym przykładzie IDR_RIBBON jest unikatową nazwą, która identyfikuje zasób wstążki, RT_RIBBON_XML jest typem zasobu i ribbon.mfcribbon ms jest nazwą pliku zasobów.  
  
 ```  
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"  
 ```  
  
-   Dodaje definicje identyfikatorów poleceń do resource.h.  
  
 ```  
 #define IDR_RIBBON            307  
 ```  
  
-   Tworzy plik zasobów wstążki (*.mfcribbon-ms), który zawiera kod XML definiujący przyciski wstążki, formanty i atrybuty. Zmiany na Wstążce w Projektancie wstążki są przechowywane w pliku zasobów w formacie XML. Poniższy przykład kodu pokazuje części zawartości \*pliku .mfcribbon ms:  
  
 ```  
 <RIBBON_BAR>  
 <ELEMENT_NAME>RibbonBar</ELEMENT_NAME>  
 <IMAGE>  
 <ID>  
 <NAME>IDB_BUTTONS</NAME>  
 <VALUE>113</VALUE>  
 </ID>   
 ```  
  
 Aby użyć zasobu wstążki w Twojej aplikacji MFC, załaduj zasób wywołując [CMFCRibbonBar::LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource).  
  
## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>Tworzenie wstążki przy użyciu projektanta wstążki  
 Poniżej przedstawiono dwa sposoby dodawania zasobów wstążki do projektu MFC:  
  
-   Tworzenie aplikacji MFC i skonfiguruj Kreator projektu MFC w celu utworzenia na Wstążce. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie Wstążki aplikacji przy użyciu MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).  
  
-   W istniejącym projekcie MFC należy utworzyć zasób Wstążki i załaduj go. Aby uzyskać więcej informacji, zobacz [wskazówki: aktualizowanie aplikacji klasa Scribble MFC (część 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).  
  
 Jeśli projekt zawiera już ręcznie zakodowane wstążki, MFC posiada funkcje, których można przekonwertować istniejącą Wstążkę na zasób wstążki. Aby uzyskać więcej informacji, zobacz [porady: Konwertowanie istniejącej wstążki MFC na zasób wstążki](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md).  
  
> [!NOTE]
>  Wstążek nie można utworzyć w aplikacjach opartych na okno dialogowe. Aby uzyskać więcej informacji, zobacz [typ aplikacji, Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md).  
  
## <a name="customizing-ribbons"></a>Dostosowywanie wstążek  
 Aby otworzyć Wstążkę w Projektancie wstążki, kliknij dwukrotnie zasób wstążki w widoku zasobów. W Projektancie można dodać, usunąć i dostosować elementy na Wstążce, przycisku aplikacji lub paska narzędzi Szybki dostęp. Możesz również połączyć zdarzenia, na przykład zdarzenia kliknięcia przycisku i zdarzenia menu, do metody w aplikacji.  
  
 Na poniższej ilustracji przedstawiono różne składniki w Projektancie wstążki.  
  
 ![Projektant wstążki MFC](../mfc/media/ribbon_designer.png "ribbon_designer")  
  
- **Przybornik:** zawiera formanty, które mogą być przeciągnięte na powierzchnię projektanta.  
  
- **Projektanta powierzchni:** zawiera wizualną reprezentacją zasobu wstążki.  
  
- **Okno właściwości:** Wyświetla listę atrybutów elementu zaznaczonego na powierzchni projektowej.  
  
- **Okno Widok zasobów:** Wyświetla zasoby, które obejmują zasoby wstążki w projekcie.  
  
- **Pasek narzędzi edytora wstążki:** zawiera polecenia, które umożliwiają przeglądanie Wstążki i zmieniają jej motyw wizualny.  
  
 W następujących tematach opisano sposób korzystania z funkcji w Projektancie wstążki:  
  
- [Instrukcje: dostosowywanie przycisku Aplikacja](../mfc/how-to-customize-the-application-button.md)  
  
- [Instrukcje: dostosowywanie paska narzędzi Szybki dostęp](../mfc/how-to-customize-the-quick-access-toolbar.md)  
  
- [Instrukcje: dodawanie kontrolek wstążki do programów obsługi zdarzeń](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)  
  
- [Instrukcje: ładowanie zasobu wstążki z aplikacji MFC](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)  
  
## <a name="definitions-of-ribbon-elements"></a>Definicje elementów wstążki  
 ![Wstążki MFC](../mfc/media/ribbon.png "wstążki")  
  
- **Przycisk aplikacji:** przycisk, który pojawia się w lewym górnym rogu wstążki. Przycisk aplikacji zastępuje menu Plik i jest widoczny nawet wtedy, gdy Wstążka jest zminimalizowana. Po kliknięciu przycisku menu, który zawiera listę poleceń jest wyświetlany.  
  
- **Pasek narzędzi Szybki dostęp:** mały, konfigurowalny pasek narzędzi, który wyświetla często używane polecenia.  
  
- **Kategoria**: logiczne grupowanie, które reprezentuje zawartość zakładki wstążki.  
  
- **Przycisk Kategoria domyślna:** przycisk, który jest wyświetlany na Wstążce, gdy Wstążka jest zminimalizowana. Po kliknięciu przycisku, kategoria ponownie wyświetla się menu.  
  
- **Panel:** obszar paska wstążki, który wyświetla grupy pokrewnych formantów. Każda kategoria wstążki zawiera jeden lub więcej paneli wstążki.  
  
- **Elementy wstążki:** kontrolki w panelach, na przykład, przyciski i pola kombi. Aby zobaczyć różne kontrolki, które mogą być hostowane na Wstążce, zobacz [przykład RibbonGadgets: aplikacja gadżetów wstążki](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)   
 [Praca z plikami zasobów](../windows/working-with-resource-files.md)

