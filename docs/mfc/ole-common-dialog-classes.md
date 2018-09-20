---
title: Klasy wspólnych okien dialogowych OLE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6ef5a7aed288331322243d316dde58d9f36cbd9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430426"
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

