---
title: Portret architektury dokument widok | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], views
- multiple views [MFC], updating from document
- document/view architecture [MFC]
- views [MFC], and user input
- documents [MFC], accessing data from view
- views [MFC], updating
- input [MFC], view class
- documents [MFC], multiple views
- document/view architecture [MFC], accessing data from view
- document/view architecture [MFC], about document/view architecture
- views [MFC], accessing document data from
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9ceadc55945a31e4787287beb6943897784aeaad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="a-portrait-of-the-documentview-architecture"></a>Portret architektury dokument/widok
Dokumenty i widoki są skojarzone w typowej aplikacji MFC. Dane są przechowywane w dokumencie, ale widok ma uprzywilejowany dostęp do danych. Rozdzielenie widoku dokumentu oddziela przechowywania i obsługi danych od jego wyświetlania.  
  
## <a name="gaining-access-to-document-data-from-the-view"></a>Aby uzyskać dostęp do danych z widoku dokumentu  
 Widok uzyskuje dostęp do swoich dokumentów danych za pomocą [GetDocument](../mfc/reference/cview-class.md#getdocument) funkcji, która zwraca wskaźnik do dokumentu lub wprowadzając w widoku klas C++ `friend` klasy dokumentu. Widoku jest używana jego dostęp do danych, aby uzyskać dane, gdy będzie gotowy do rysowania lub wprowadzenia innych zmian.  
  
 Na przykład z widoku [OnDraw](../mfc/reference/cview-class.md#ondraw) używa widoku funkcji członkowskiej **GetDocument** uzyskać wskaźnik dokumentu. Następnie używa tego wskaźnika dostępu do `CString` elementu członkowskiego danych w dokumencie. Widok przekazuje ciąg do `TextOut` funkcji. Aby wyświetlić kod w tym przykładzie, zobacz [Rysowanie w widoku](../mfc/drawing-in-a-view.md).  
  
## <a name="user-input-to-the-view"></a>Dane wejściowe użytkownika do widoku  
 Widok może również zinterpretować kliknięcie myszki w siebie jako zaznaczenie lub edytowanie danych. Podobnie może go zinterpretować naciśnięcia klawiszy jako wprowadzania danych lub edycji. Załóżmy, że użytkownik wpisuje ciąg w widoku, który zarządza tekstu. Widok uzyskuje wskaźnik do dokumentu i używa wskaźnika do przekazania nowe dane do dokumentu, który zapisuje je w niektórych struktury danych.  
  
## <a name="updating-multiple-views-of-the-same-document"></a>Aktualizowanie różne widoki tego samego dokumentu  
 W aplikacji z wielu widoków tego samego dokumentu — takie jak okna dzielącego w edytorze tekstów — widok przekazuje najpierw nowe dane do dokumentu. A następnie wywołuje dokumentu [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) funkcji członkowskiej, która określa, że wszystkie widoki dokumentu, aby zaktualizować, aby odzwierciedlić nowe dane. Widoki do synchronizacji.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Zalety architektury dokument/widok](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [Alternatywy dla architektury dokument/widok](../mfc/alternatives-to-the-document-view-architecture.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura dokument/widok](../mfc/document-view-architecture.md)

