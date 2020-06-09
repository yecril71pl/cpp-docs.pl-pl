---
title: Klasy wspólnych okien dialogowych OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
ms.openlocfilehash: 1854d19c540f5e3e64b47786f465a05213eced86
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617793"
---
# <a name="ole-common-dialog-classes"></a>Klasy wspólnych okien dialogowych OLE

Te klasy obsługują typowe zadania OLE, implementując wiele standardowych okien dialogowych OLE. Zapewniają także spójny interfejs użytkownika dla funkcji OLE.

[COleDialog](reference/coledialog-class.md)<br/>
Używane przez platformę do przechowywania wspólnych implementacji dla wszystkich okien dialogowych OLE. Wszystkie klasy okien dialogowych w kategorii interfejs użytkownika są wyprowadzane z tej klasy bazowej. `COleDialog`nie można używać bezpośrednio.

[COleInsertDialog](reference/coleinsertdialog-class.md)<br/>
Wyświetla okno dialogowe Wstawianie obiektu, standardowy interfejs użytkownika służący do wstawiania nowych połączonych lub osadzonych elementów OLE.

[COlePasteSpecialDialog](reference/colepastespecialdialog-class.md)<br/>
Wyświetla okno dialogowe wklejanie specjalne, standardowy interfejs użytkownika do implementowania polecenia Edytuj Wklej specjalnie.

[COleLinksDialog](reference/colelinksdialog-class.md)<br/>
Wyświetla okno dialogowe Edytowanie linków, standardowy interfejs użytkownika służący do modyfikowania informacji o połączonych elementach.

[COleChangeIconDialog](reference/colechangeicondialog-class.md)<br/>
Wyświetla okno dialogowe Zmień ikonę, standardowy interfejs użytkownika służący do zmiany ikony skojarzonej z elementem OLE osadzonym lub połączonym.

[COleConvertDialog](reference/coleconvertdialog-class.md)<br/>
Wyświetla okno dialogowe Konwersja, standardowy interfejs użytkownika służący do konwertowania elementów OLE z jednego typu na drugi.

[COlePropertiesDialog](reference/colepropertiesdialog-class.md)<br/>
Hermetyzuje okno dialogowe właściwości typowego interfejsu OLE systemu Windows. Okna dialogowe wspólne właściwości OLE zapewniają łatwy sposób wyświetlania i modyfikowania właściwości elementu dokumentu OLE w sposób zgodny ze standardami systemu Windows.

[COleUpdateDialog](reference/coleupdatedialog-class.md)<br/>
Wyświetla okno dialogowe Aktualizacja, standardowy interfejs użytkownika do aktualizowania wszystkich linków w dokumencie. Okno dialogowe zawiera wskaźnik postępu, aby wskazać, w jaki sposób zamykana jest procedura aktualizacji.

[COleChangeSourceDialog](reference/colechangesourcedialog-class.md)<br/>
Wyświetla okno dialogowe Zmień źródło, standardowy interfejs użytkownika służący do zmiany miejsca docelowego lub źródła łącza.

[COleBusyDialog](reference/colebusydialog-class.md)<br/>
Wyświetla okna dialogowe zajęty serwer i serwer nie odpowiada, standardowy interfejs użytkownika do obsługi wywołań do zajętych aplikacji. Zwykle jest automatycznie wyświetlana przez `COleMessageFilter` implementację.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
