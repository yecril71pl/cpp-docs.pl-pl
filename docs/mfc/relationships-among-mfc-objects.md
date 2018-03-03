---
title: "Relacje między obiektami MFC | Dokumentacja firmy Microsoft"
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
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2ea93e9e56b676e4dfef33ecbcabfd9754458024
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="relationships-among-mfc-objects"></a>Relacje między obiektami MFC
Aby pomóc proces tworzenia dokumentu/widoku w perspektywie, należy wziąć pod uwagę uruchomiony program: dokument, okno ramowe zawiera widok i widok powiązany z dokumentem.  
  
-   Dokument przechowuje listę widoki tego dokumentu i wskaźnik do szablonu dokumentu, w której go utworzono.  
  
-   Widok temu wskaźnik do swoich dokumentów i jest elementem podrzędnym ramki okna nadrzędnego.  
  
-   Okna ramowe dokumentów zachowuje wskaźnik do jego bieżący widok aktywne.  
  
-   Szablon dokumentu przechowuje listę otwartych dokumentów.  
  
-   Aplikacja przechowuje listę jej szablonów dokumentów.  
  
-   Przechowuje informacje o Windows wszystkie otwarte okna, więc może wysłać wiadomości do nich.  
  
 Te relacje są konfigurowane podczas tworzenia dokumentu/widoku. W poniższej tabeli przedstawiono, jak obiekty w uruchomiony program może uzyskać dostęp do innych obiektów. Dowolny obiekt można uzyskać wskaźnik do obiektu aplikacji przez wywołanie funkcji globalnej [afxgetapp —](../mfc/reference/application-information-and-management.md#afxgetapp).  
  
### <a name="gaining-access-to-other-objects-in-your-application"></a>Aby uzyskać dostęp do innych obiektów w aplikacji  
  
|Z obiektu|Jak uzyskać dostęp do innych obiektów|  
|-----------------|---------------------------------|  
|dokument|Użyj [GetFirstViewPosition](../mfc/reference/cdocument-class.md#getfirstviewposition) i [GetNextView](../mfc/reference/cdocument-class.md#getnextview) dostęp do dokumentu widoku listy.<br /><br /> Wywołanie [GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate) pobrać szablonu dokumentu.|  
|Widok|Wywołanie [GetDocument](../mfc/reference/cview-class.md#getdocument) można pobrać dokumentu.<br /><br /> Wywołanie [GetParentFrame](../mfc/reference/cwnd-class.md#getparentframe) można pobrać ramkę okna.|  
|Okna ramowe dokumentów|Wywołanie [GetActiveView](../mfc/reference/cframewnd-class.md#getactiveview) można pobrać bieżącego widoku.<br /><br /> Wywołanie [GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument) pobrać dokumentu dołączony do bieżącego widoku.|  
|Okna ramowe MDI|Wywołanie [MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive) można pobrać aktualnie aktywny [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).|  
  
 Zazwyczaj okno ramowe ma jeden widok, ale czasami, tak jak okna podziału w tym samym oknie ramki zawiera wiele widoków. Okno ramowe zachowuje wskaźnik do aktywnego widoku; wskaźnik jest aktualizowany za każdym razem inny widok jest aktywowane.  
  
> [!NOTE]
>  Wskaźnik do głównego okna ramowego są przechowywane w [m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd) zmiennej członkowskiej obiektu aplikacji. Wywołanie `OnFileNew` w zastąpienia z `InitInstance` funkcji członkowskiej klasy `CWinApp` ustawia `m_pMainWnd` dla Ciebie. Jeśli nie zostanie wywołana `OnFileNew`, należy ustawić wartość zmiennej w `InitInstance` samodzielnie. (Aplikacji składowych (serwer) SDI COM może nie ustawiono zmiennej Jeśli Embedding znajduje się w wierszu polecenia.) Należy pamiętać, że `m_pMainWnd` teraz jest elementem członkowskim klasy `CWinThread` zamiast `CWinApp`.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Tworzenie szablonu dokumentu](../mfc/document-template-creation.md)   
 [Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)   
 [Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)

