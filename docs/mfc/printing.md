---
title: Drukowanie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 48395276acfac71cd940be307c3b5f0735c356ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="printing"></a>Drukowanie
Microsoft Windows implementuje wyświetlania niezależnych od urządzenia. W MFC, oznacza to, że tego samego wywołań rysowania, w `OnDraw` funkcji członkowskiej klasy widoku, są zobowiązani do rysowania na ekranie i na innych urządzeniach, takich jak drukarki. Podglądu wydruku urządzenie docelowe jest symulowane wydruk do wyświetlenia.  
  
##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>Twoja rola w drukowanie, a w ramach roli  
 Klasy widoku ma następujące obowiązki:  
  
-   Poinformuj platformę są liczbę stron w dokumencie.  
  
-   Po otrzymaniu monitu, aby wydrukować stronę określony, Rysuj część dokumentu.  
  
-   Przydziel i cofnięcia przydzielenia czcionek ani innych zasobów grafiki urządzenia interfejsu (GDI) wymagane do drukowania.  
  
-   W razie potrzeby wysyłania wszelkie specjalne kody potrzebne, aby zmienić tryb drukarki przed wydrukowaniem daną stronę, na przykład, aby zmienić drukowania orientację na podstawie na stronie.  
  
 Obowiązki framework są następujące:  
  
-   Wyświetl **drukowania** okno dialogowe.  
  
-   Utwórz [CDC](../mfc/reference/cdc-class.md) obiekt do drukarki.  
  
-   Wywołanie [StartDoc](../mfc/reference/cdc-class.md#startdoc) i [EndDoc](../mfc/reference/cdc-class.md#enddoc) funkcji Członkowskich `CDC` obiektu.  
  
-   Wielokrotnie wywoływać [StartPage](../mfc/reference/cdc-class.md#startpage) funkcji członkowskiej klasy `CDC` obiekt informuje klasa widoku strony, która ma być drukowana i Wywołaj [EndPage](../mfc/reference/cdc-class.md#endpage) funkcji członkowskiej klasy `CDC` obiektu.  
  
-   Wywołanie funkcji możliwym do zastąpienia w widoku w odpowiednim czasie.  
  
 W następujących artykułach omówiono sposób platforma obsługuje drukowania i podglądu wydruku:  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Jak jest wykonywane Drukowanie domyślne](../mfc/how-default-printing-is-done.md)  
  
-   [Dokumenty wielostronicowe](../mfc/multipage-documents.md)  
  
-   [Nagłówki i stopki](../mfc/headers-and-footers.md)  
  
-   [Alokowanie zasobów GDI do drukowania](../mfc/allocating-gdi-resources.md)  
  
-   [Podgląd wydruku](../mfc/print-preview-architecture.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Drukowanie i Podgląd wydruku](../mfc/printing-and-print-preview.md)

