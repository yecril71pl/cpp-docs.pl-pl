---
title: 'Porady: Dostosowywanie przycisku aplikacja | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5a2512c212efe2cba09d23baf1a997de3a98d154
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-customize-the-application-button"></a>Porady: dostosowywanie przycisku Aplikacja
Po kliknięciu przycisku aplikacji, menu poleceń jest wyświetlany. Zazwyczaj menu zawiera polecenia związane z plików, takie jak **Otwórz**, **zapisać**, **drukowania**, i **zakończenia**.  
  
 ![Przycisk aplikacji wstążki MFC](../mfc/media/application_button.png "application_button")  
  
 Aby dostosować przycisku aplikacji, otwórz go w **właściwości** , zmodyfikuj jego właściwości, a następnie podglądu formantu wstążki.  
  
### <a name="to-open-the-application-button-in-the-properties-window"></a>Aby otworzyć okno Właściwości przycisku aplikacji  
  
1.  W programie Visual Studio na **widoku** menu, kliknij przycisk **widok zasobów**.  
  
2.  W **widok zasobów**, kliknij dwukrotnie plik zasobu wstążki, aby go wyświetlić na powierzchni projektu.  
  
3.  Na powierzchni projektu, kliknij prawym przyciskiem myszy przycisk menu aplikacja, a następnie kliknij przycisk **właściwości**.  
  
## <a name="application-button-properties"></a>Właściwości przycisku aplikacji  
 W poniższej tabeli opisano właściwości przycisku aplikacji.  
  
|Właściwość|Definicja|  
|--------------|----------------|  
|**Przyciski**|Zawiera kolekcję maksymalnie trzy przyciski, które znajdują się w prawym dolnym rogu menu aplikacji.|  
|**Podpis**|Określa tekst formantu. W przeciwieństwie do innych elementów wstążki przycisku aplikacji nie jest wyświetlany tekst podpisu. Zamiast tego tekst jest używany dla ułatwień dostępu.|  
|**Obraz HDPI**|Określa identyfikator wysokie dpi ikona przycisk aplikacji (HDPI). Po uruchomieniu aplikacji na monitorze wysokiej rozdzielczości DPI **obraz HDPI** jest używany zamiast **obrazu**.|  
|**Duże obrazy HDPI**|Określa identyfikator wysokiej rozdzielczości DPI dużych obrazów. Po uruchomieniu aplikacji na monitorze wysokiej rozdzielczości DPI **duże obrazy HDPI** jest używany zamiast **duże obrazy**.|  
|**Małe obrazy HDPI**|Określa identyfikator wysokiej małe obrazy DPI. Po uruchomieniu aplikacji na monitorze wysokiej rozdzielczości DPI **małe obrazy HDPI** jest używany zamiast **małe obrazy**.|  
|**IDENTYFIKATOR**|Określa identyfikator kontrolki.|  
|**Obraz**|Określa identyfikator przycisku ikonę aplikacji. Ikona jest mapą bitową 26 x 26 32-bitowy, zawierający alfa przezroczystości. Przezroczyste obiekty ikony są wyróżnione po kliknięciu przycisku aplikacji lub aktywowany przez.|  
|**Klucze**|Określa ciąg, który jest wyświetlany po klucz Porada nawigacji jest włączona. Porada klucza nawigacji jest włączona po naciśnięciu klawisza ALT.|  
|**Duże obrazy**|Określa identyfikator obrazu, który zawiera szereg ikony 32 x 32. Ikony są używane przez przyciski w kolekcji elementów Main.|  
|**Elementy główne**|Zawiera kolekcję elementów menu, które są wyświetlane w menu aplikacji.|  
|**Podpis MRU**|Określa tekst wyświetlany w panelu ostatnie listy.|  
|**Małe obrazy**|Określa identyfikator obrazu, który zawiera szereg ikony 16 x 16. Ikony są używane przez przycisków w kolekcji przycisków.|  
|**Użyj**|Włącza lub wyłącza panelu ostatnie listy. Panel ostatnie listy pojawia się w menu aplikacji.|  
|**Szerokość**|Określa szerokość w pikselach panelu ostatnie listy.|  
  
 W menu aplikacji nie jest wyświetlana na powierzchni projektu. Aby go wyświetlić, możesz wyświetlić podgląd Wstążki lub uruchomić aplikację.  
  
#### <a name="to-preview-the-ribbon-control"></a>Aby wyświetlić podgląd formantu wstążki  
  
-   Na **paska narzędzi edytora wstążki**, kliknij przycisk **wstążki testu**.  
  
## <a name="see-also"></a>Zobacz też  
 [Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md)

