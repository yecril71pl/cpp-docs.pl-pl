---
title: Klasy wspólnych okien dialogowych OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
ms.openlocfilehash: b44a7b203c17f09f872cfedbb05798affb57f0f9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447673"
---
# <a name="ole-common-dialog-classes"></a>Klasy wspólnych okien dialogowych OLE

Te klasy obsługują typowe zadania OLE, implementując wiele standardowych okien dialogowych OLE. Zapewniają także spójny interfejs użytkownika dla funkcji OLE.

[COleDialog](../mfc/reference/coledialog-class.md)<br/>
Używane przez platformę do przechowywania wspólnych implementacji dla wszystkich okien dialogowych OLE. Wszystkie klasy okien dialogowych w kategorii interfejs użytkownika są wyprowadzane z tej klasy bazowej. nie można używać `COleDialog` bezpośrednio.

[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)<br/>
Wyświetla okno dialogowe Wstawianie obiektu, standardowy interfejs użytkownika służący do wstawiania nowych połączonych lub osadzonych elementów OLE.

[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)<br/>
Wyświetla okno dialogowe wklejanie specjalne, standardowy interfejs użytkownika do implementowania polecenia Edytuj Wklej specjalnie.

[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)<br/>
Wyświetla okno dialogowe Edytowanie linków, standardowy interfejs użytkownika służący do modyfikowania informacji o połączonych elementach.

[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)<br/>
Wyświetla okno dialogowe Zmień ikonę, standardowy interfejs użytkownika służący do zmiany ikony skojarzonej z elementem OLE osadzonym lub połączonym.

[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)<br/>
Wyświetla okno dialogowe Konwersja, standardowy interfejs użytkownika służący do konwertowania elementów OLE z jednego typu na drugi.

[COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)<br/>
Hermetyzuje okno dialogowe właściwości typowego interfejsu OLE systemu Windows. Okna dialogowe wspólne właściwości OLE zapewniają łatwy sposób wyświetlania i modyfikowania właściwości elementu dokumentu OLE w sposób zgodny ze standardami systemu Windows.

[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)<br/>
Wyświetla okno dialogowe Aktualizacja, standardowy interfejs użytkownika do aktualizowania wszystkich linków w dokumencie. Okno dialogowe zawiera wskaźnik postępu, aby wskazać, w jaki sposób zamykana jest procedura aktualizacji.

[COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)<br/>
Wyświetla okno dialogowe Zmień źródło, standardowy interfejs użytkownika służący do zmiany miejsca docelowego lub źródła łącza.

[COleBusyDialog](../mfc/reference/colebusydialog-class.md)<br/>
Wyświetla okna dialogowe zajęty serwer i serwer nie odpowiada, standardowy interfejs użytkownika do obsługi wywołań do zajętych aplikacji. Zwykle jest automatycznie wyświetlana przez implementację `COleMessageFilter`.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
