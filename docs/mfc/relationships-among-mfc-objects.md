---
title: Relacje między obiektami MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
ms.openlocfilehash: d7e40e25b405d3f8ec50a518889cc2b89bc8c725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372811"
---
# <a name="relationships-among-mfc-objects"></a>Relacje między obiektami MFC

Aby ułatwić umieszczenie procesu tworzenia dokumentu/widoku w perspektywie, należy wziąć pod uwagę uruchomiony program: dokument, okno ramki używane do przechowywania widoku i widok skojarzony z dokumentem.

- Dokument przechowuje listę widoków tego dokumentu i wskaźnik do szablonu dokumentu, który utworzył dokument.

- Widok zachowuje wskaźnik do dokumentu i jest elementem podrzędnym okna ramki nadrzędnej.

- Okno ramki dokumentu przechowuje wskaźnik do bieżącego aktywnego widoku.

- Szablon dokumentu przechowuje listę otwartych dokumentów.

- Aplikacja przechowuje listę swoich szablonów dokumentów.

- System Windows śledzi wszystkie otwarte okna, dzięki czemu może wysyłać do nich wiadomości.

Relacje te są ustanawiane podczas tworzenia dokumentu/widoku. W poniższej tabeli przedstawiono, jak obiekty w uruchomionym programie mogą uzyskiwać dostęp do innych obiektów. Każdy obiekt może uzyskać wskaźnik do obiektu aplikacji, wywołując funkcję globalną [AfxGetApp](../mfc/reference/application-information-and-management.md#afxgetapp).

### <a name="gaining-access-to-other-objects-in-your-application"></a>Uzyskiwanie dostępu do innych obiektów w aplikacji

|Z obiektu|Jak uzyskać dostęp do innych obiektów|
|-----------------|---------------------------------|
|Dokument|Aby uzyskać dostęp do listy wyświetleń dokumentu, należy użyć [funkcji GetFirstViewPosition](../mfc/reference/cdocument-class.md#getfirstviewposition) i [GetNextView.](../mfc/reference/cdocument-class.md#getnextview)<br /><br /> Wywołanie [GetDocTemplate,](../mfc/reference/cdocument-class.md#getdoctemplate) aby uzyskać szablon dokumentu.|
|Widok|Zadzwoń [do GetDocument,](../mfc/reference/cview-class.md#getdocument) aby uzyskać dokument.<br /><br /> Wywołanie [GetParentFrame,](../mfc/reference/cwnd-class.md#getparentframe) aby uzyskać okno ramki.|
|Okno ramki dokumentu|Wywołanie [GetActiveView,](../mfc/reference/cframewnd-class.md#getactiveview) aby uzyskać bieżący widok.<br /><br /> Wywołanie [GetActiveDocument,](../mfc/reference/cframewnd-class.md#getactivedocument) aby uzyskać dokument dołączony do bieżącego widoku.|
|Okno ramki MDI|Wywołanie [MDIGetActive,](../mfc/reference/cmdiframewnd-class.md#mdigetactive) aby uzyskać aktualnie aktywny [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).|

Zazwyczaj okno ramki ma jeden widok, ale czasami, jak w oknach rozdzielacza, to samo okno ramki zawiera wiele widoków. Okno ramki przechowuje wskaźnik do aktualnie aktywnego widoku; wskaźnik jest aktualizowany za każdym razem, gdy inny widok jest aktywowany.

> [!NOTE]
> Wskaźnik do okna ramki głównej jest przechowywany w [zmiennej m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd) elementu członkowskiego obiektu aplikacji. Wywołanie `OnFileNew` w zastąpienie funkcji `InitInstance` elementu członkowskiego `CWinApp` zestawów *m_pMainWnd* dla Ciebie. Jeśli nie wywołasz, `OnFileNew`musisz ustawić wartość zmiennej w `InitInstance` sobie. (SDI COM component (serwer) aplikacje nie może ustawić zmienną, jeśli /Osadzanie znajduje się w wierszu polecenia.) Należy zauważyć, *że m_pMainWnd* jest teraz `CWinThread` członkiem klasy, a nie `CWinApp`.

## <a name="see-also"></a>Zobacz też

[Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Tworzenie szablonu dokumentu](../mfc/document-template-creation.md)<br/>
[Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)<br/>
[Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)
