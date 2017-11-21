---
title: "Wstążka Projektant (MFC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.ribbon.F1
dev_langs: C++
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4a0076f9ce0bcf4787f4e848fbcb0d34ae8968f4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ribbon-designer-mfc"></a>Projektant wstążki (MFC)
Projektant wstążki umożliwia tworzenie i Dostosowywanie Wstążki w aplikacjach MFC. Wstążki jest elementem interfejsu użytkownika, który organizuje poleceń w grupy logiczne. Grupy te są wyświetlane na osobnych kartach pasek w górnej części okna. Wstążka zastępuje paska menu i pasków narzędzi. Wstążki może znacznie poprawić użyteczność aplikacji. Aby uzyskać więcej informacji, zobacz [wstążek](http://go.microsoft.com/fwlink/linkid=129233). Na poniższej ilustracji przedstawiono wstążki.  
  
 ![Formant zasobu wstążki MFC](../mfc/media/ribbon_no_callouts.png "ribbon_no_callouts")  
  
 We wcześniejszych wersjach programu Visual Studio wstążek ma zostać utworzona przez pisania kodu, który korzysta z klas wstążki MFC, takich jak [CMFCRibbonBar klasy](../mfc/reference/cmfcribbonbar-class.md). W [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)], projektanta wstążki zapewnia alternatywny sposób tworzenia wstążki. Po pierwsze tworzenia i dostosowywania wstążki jako zasób. Następnie ładowanie zasobu wstążki z kodu w aplikacji MFC. Nawet wstążki zasobów i służy klasy wstążki MFC razem. Można na przykład utwórz zasób wstążki, a następnie programowo dodać więcej elementów do niego w czasie wykonywania za pomocą kodu.  
  
## <a name="understanding-the-ribbon-designer"></a>Opis projektanta wstążki  
 Projektant wstążki tworzy i przechowuje wstążki jako zasób. Podczas tworzenia zasobu wstążki projektanta wstążki wykonuje te trzy czynności:  
  
-   Dodaje wpis w definicji skrypt zasobów projektu (* .rc). W poniższym przykładzie `IDR_RIBBON` jest unikatową nazwę, która identyfikuje zasób wstążki `RT_RIBBON_XML` jest typ zasobu i `ribbon.mfcribbon-ms` to nazwa pliku zasobu.  
  
 ```  
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"  
 ```  
  
-   Dodaje definicje identyfikatorów poleceń do resource.h.  
  
 ```  
 #define IDR_RIBBON            307  
 ```  
  
-   Tworzy plik zasobu wstążki (*.mfcribbon ms), który zawiera kod XML, który definiuje przycisków wstążki, kontrolek i atrybuty. Zmiany do wstążki w Projektancie wstążki są przechowywane w pliku zasobu jako XML. Poniższy przykład kodu pokazuje części zawartości \*pliku .mfcribbon ms:  
  
 ```  
 <RIBBON_BAR>  
 <ELEMENT_NAME>RibbonBar</ELEMENT_NAME>  
 <IMAGE>  
 <ID>  
 <NAME>IDB_BUTTONS</NAME>  
 <VALUE>113</VALUE>  
 </ID>   
 ```  
  
 Aby użyć zasobu wstążki w aplikacji MFC, załadować zasobu przez wywołanie metody [CMFCRibbonBar::LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource).  
  
## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>Tworzenie wstążki za pomocą projektanta wstążki  
 Są dwa sposoby dodawania zasób wstążki do projektu MFC:  
  
-   Tworzenie aplikacji MFC i skonfiguruj kreatora projektu MFC, aby utworzyć na Wstążce. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie Wstążki aplikacji za pomocą MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).  
  
-   W istniejących projektach MFC Utwórz zasób wstążki, a następnie załaduj. Aby uzyskać więcej informacji, zobacz [wskazówki: aktualizowanie aplikacji Bazgroły MFC (część 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).  
  
 Jeśli projekt zawiera już ręcznie kodowane wstążki, MFC ma funkcje, których można użyć do konwersji istniejącej wstążki na zasób wstążki. Aby uzyskać więcej informacji, zobacz [porady: Konwertowanie istniejącej wstążki MFC na zasób wstążki](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md).  
  
> [!NOTE]
>  Nie można utworzyć taśmy w aplikacjach opartych na oknach dialogowych. Aby uzyskać więcej informacji, zobacz [typ aplikacji, Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md).  
  
## <a name="customizing-ribbons"></a>Dostosowywanie Wstążki  
 Aby otworzyć projektanta wstążki wstążki, kliknij dwukrotnie zasobu wstążki w widoku zasobów. W Projektancie możesz dodać, usunąć i dostosować elementów na Wstążce, przycisk aplikacji lub pasek narzędzi Szybki dostęp. Możesz również połączyć zdarzenia, na przykład, kliknij przycisk zdarzenia i menu, do metody w aplikacji.  
  
 Na poniższej ilustracji przedstawiono różne składniki w Projektancie wstążki.  
  
 ![Projektant wstążki MFC](../mfc/media/ribbon_designer.png "ribbon_designer")  
  
- **Przybornika:** zawiera formanty, które mogą być przeciągnięte powierzchnię projektanta.  
  
- **Powierzchnię projektanta:** zawiera wizualną reprezentację zasobu wstążki.  
  
- **Okno właściwości:** zawiera listę atrybutów elementu wybranego na powierzchnię projektanta.  
  
- **Okno Widok zasobów:** Wyświetla zasoby, które zawierają zasoby wstążki w projekcie.  
  
- **Pasek narzędzi edytora wstążki:** zawiera polecenia, które pozwalają Podgląd Wstążki i zmień jego visual motyw.  
  
 W następujących tematach opisano sposób korzystania z funkcji w Projektancie wstążki:  
  
- [Porady: Dostosowywanie przycisku aplikacja](../mfc/how-to-customize-the-application-button.md)  
  
- [Porady: Dostosowywanie paska narzędzi Szybki dostęp](../mfc/how-to-customize-the-quick-access-toolbar.md)  
  
- [Porady: dodawanie formantów wstążki do programów obsługi zdarzeń](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)  
  
- [Porady: ładowanie zasobu wstążki z aplikacji MFC](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)  
  
## <a name="definitions-of-ribbon-elements"></a>Definicje elementów wstążki  
 ![Wstążka MFC](../mfc/media/ribbon.png "wstążki")  
  
- **Przycisk aplikacji:** przycisku, który znajduje się w lewym górnym rogu wstążki. Przycisk aplikacji zastępuje menu Plik i jest widoczny, nawet wtedy, gdy jest zminimalizowany wstążki. Po kliknięciu przycisku menu, która zawiera listę poleceń jest wyświetlany.  
  
- **Pasek narzędzi Szybki dostęp:** pasek narzędzi małych, które można dostosowywać, który wyświetla często używanych poleceń.  
  
- **Kategoria**: logiczne grupowanie, który reprezentuje zawartość karty wstążki.  
  
- **Przycisk domyślny kategorii:** przycisku, który jest wyświetlany na Wstążce, gdy jest zminimalizowany wstążki. Po kliknięciu przycisku kategorii pojawi się ponownie jako menu.  
  
- **Panel:** obszar na pasku wstążki, która wyświetla grupy formantów powiązanych. Każda kategoria wstążki zawiera co najmniej jeden panele wstążki.  
  
- **Wstążka elementów:** formanty w panele, na przykład, przycisków i pola kombi. Aby wyświetlić różne formantów, które mogą być hostowane na Wstążce, zobacz [RibbonGadgets próbki: aplikacji gadżetów wstążki](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)   
 [Praca z plikami zasobów](../windows/working-with-resource-files.md)

