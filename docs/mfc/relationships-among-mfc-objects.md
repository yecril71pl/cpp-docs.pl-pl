---
title: Relacje między obiektami MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
ms.openlocfilehash: bb8d1fcd9737b33d52038746a26f4e1bd1043e95
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276979"
---
# <a name="relationships-among-mfc-objects"></a>Relacje między obiektami MFC

Aby umieścić proces tworzenia dokumentu/widoku w perspektywie, należy wziąć pod uwagę uruchomiony program: dokument, okno ramowe zawiera widok i widok powiązany z dokumentem.

- Dokument przechowuje listę widoków dokumentu i wskaźnik do szablonu dokumentu, który utworzył dokument.

- Widok przechowuje wskaźnik do swoich dokumentów i jest elementem podrzędnym jej nadrzędnej ramki okna.

- Okna ramki dokumentu przechowuje wskaźnik do jego bieżący widok aktywne.

- Szablon dokumentu przechowuje listę jego otwartych dokumentów.

- Aplikacja przechowuje listę jej szablonów dokumentów.

- Przechowuje informacje o Windows wszystkie otwarte okna, dlatego jest w stanie wysyłać komunikaty do nich.

Te relacje są określane podczas tworzenia dokumentu/widoku. W poniższej tabeli przedstawiono, jak obiekty w uruchomiony program mają dostęp do innych obiektów. Dowolny obiekt można uzyskać wskaźnik do obiektu aplikacji przez wywołanie funkcji globalnych [afxgetapp —](../mfc/reference/application-information-and-management.md#afxgetapp).

### <a name="gaining-access-to-other-objects-in-your-application"></a>Uzyskiwanie dostępu do innych obiektów w aplikacji

|Z obiektu|Jak uzyskać dostęp do innych obiektów|
|-----------------|---------------------------------|
|dokument|Użyj [GetFirstViewPosition](../mfc/reference/cdocument-class.md#getfirstviewposition) i [GetNextView](../mfc/reference/cdocument-class.md#getnextview) uzyskać dostępu do dokumentu widoku listy.<br /><br /> Wywołaj [GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate) pobrać szablonu dokumentu.|
|Widok|Wywołaj [GetDocument](../mfc/reference/cview-class.md#getdocument) można pobrać dokumentu.<br /><br /> Wywołaj [GetParentFrame](../mfc/reference/cwnd-class.md#getparentframe) można pobrać ramki okna.|
|Okno ramowe dokumentów|Wywołaj [GetActiveView](../mfc/reference/cframewnd-class.md#getactiveview) można pobrać bieżącego widoku.<br /><br /> Wywołaj [GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument) można pobrać dokumentu powiązanego z bieżącego widoku.|
|Okno ramek MDI|Wywołaj [MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive) można pobrać aktualnie aktywne [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).|

Zazwyczaj okno ramowe ma jeden widok, ale czasami, tak jak okna podziału w tym samym oknie ramki zawiera wiele widoków. Okno ramowe przechowuje wskaźnik do aktualnie aktywnego widoku; wskaźnik jest aktualizowany zawsze, gdy inny widok jest aktywowany.

> [!NOTE]
>  Wskaźnik do ramki głównego okna są przechowywane w [elementu m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd) zmiennej składowej obiektu aplikacji. Wywołanie `OnFileNew` w zastąpienie metody `InitInstance` funkcji składowej typu `CWinApp` ustawia *elementu m_pMainWnd* dla Ciebie. Jeśli nie zostanie wywołana `OnFileNew`, należy ustawić wartość zmiennej w `InitInstance` samodzielnie. (Aplikacji (serwer) składnika SDI COM może nie ustawiono zmiennej Jeśli/Embedding znajduje się w wierszu polecenia.) Należy pamiętać, że *elementu m_pMainWnd* jest teraz członkiem klasy `CWinThread` zamiast `CWinApp`.

## <a name="see-also"></a>Zobacz także

[Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Tworzenie szablonu dokumentu](../mfc/document-template-creation.md)<br/>
[Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)<br/>
[Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)
