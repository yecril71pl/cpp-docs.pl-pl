---
title: Klasy wspólnych okien dialogowych OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
ms.openlocfilehash: e11e072ad3133d5df9614afa8753178e11b2d025
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614074"
---
# <a name="ole-common-dialog-classes"></a>Klasy wspólnych okien dialogowych OLE

W ramach tych zajęć obsłużyć typowe zadania związane z OLE poprzez implementację szereg standardowych okien dialogowych OLE. Zapewniają także spójny interfejs użytkownika dla funkcji OLE.

[COleDialog](../mfc/reference/coledialog-class.md)<br/>
Używane przez architekturę, aby zawierała najczęściej występujące implementacje dla wszystkich okien dialogowych OLE. Wszystkie klasy okien dialogowych w kategorii interfejsu użytkownika są uzyskiwane z tej klasy bazowej. `COleDialog` Nie można używać bezpośrednio.

[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)<br/>
Wyświetla okno dialogowe Wstawianie obiektu standardowy interfejs użytkownika, wstawianie nowych OLE połączone lub osadzone elementy.

[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)<br/>
Wyświetla okno dialogowe Wklej specjalne standardowy interfejs użytkownika wykonywania polecenia Edytuj Wklej specjalne.

[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)<br/>
Wyświetla okno dialogowe Edytuj linki standardowy interfejs użytkownika do modyfikowania informacji na temat połączone elementy.

[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)<br/>
Wyświetla okno dialogowe Zmienianie ikony, standardowy interfejs użytkownika dla zmiany, które osadzone ikon skojarzonych z OLE lub połączony element.

[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)<br/>
Wyświetla okno dialogowe Konwertowanie standardowy interfejs użytkownika do konwertowania jeden typ elementów OLE.

[COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)<br/>
Hermetyzuje wspólne okno dialogowe właściwości OLE Windows. Wspólne okna dialogowe OLE właściwości zapewniają prosty sposób wyświetlania i modyfikacji właściwości elementu dokumentu OLE w sposób zgodny ze standardami Windows.

[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)<br/>
Wyświetla okno dialogowe aktualizacji standardowy interfejs użytkownika aktualizacji wszystkie linki w dokumencie. Okno dialogowe zawiera wskaźnik postępu, aby wskazać, jak blisko procedura aktualizacji zostanie ukończone.

[COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)<br/>
Wyświetla okno dialogowe Zmień źródło standardowy interfejs użytkownika do zmiany przeznaczenia lub źródłem linku.

[COleBusyDialog](../mfc/reference/colebusydialog-class.md)<br/>
Wyświetla oknach dialogowych serwer jest zajęty i serwer nie odpowiada, standardowy interfejs użytkownika do obsługi wywołań zajęty aplikacji. Zwykle jest wyświetlany automatycznie przez `COleMessageFilter` implementacji.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

