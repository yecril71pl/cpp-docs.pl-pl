---
title: Okna dialogowe w OLE
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], OLE dialog boxes
- OLE dialog boxes
- dialog boxes
- OLE dialog boxes [MFC], about OLE dialog boxes
- dialog boxes [MFC], about dialog boxes
- dialog boxes [MFC], OLE
- Insert object
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
ms.openlocfilehash: 1081a831cc2b9fc0ab22e2c80a4f657466534d86
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270894"
---
# <a name="dialog-boxes-in-ole"></a>Okna dialogowe w OLE

Gdy użytkownik uruchamia aplikację z obsługą OLE, istnieją razy, gdy aplikacja potrzebuje informacji od użytkownika w celu wykonania operacji. Klasy MFC OLE zapewniają szereg okna dialogowe w celu zebrania wymaganych informacji. Ten temat zawiera listę zadań, obsługiwane przez okna dialogowe OLE i klasy niezbędne do wyświetlania tych okien dialogowych. Szczegółowe informacje na temat okien dialogowych OLE i struktur, używany w celu dostosowania ich zachowania, [odwołanie MFC](../mfc/mfc-desktop-applications.md).

*INSERT — obiekt*<br/>
To okno dialogowe umożliwia użytkownikowi Wstawianie nowo utworzone lub istniejących obiektów w dokumencie złożonym. Ponadto pozwala użytkownikowi wybrać wyświetlanie elementu jako ikony i umożliwia zmienianie ikony przycisku polecenia. Wyświetl to okno dialogowe, gdy użytkownik wybierze Wstawianie obiektu z menu Edycja. Użyj [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) klasy, aby wyświetlić to okno dialogowe. Należy pamiętać, że aplikacja MDI nie można wstawić do niej samej. Aplikacja kontenera/serwera nie można wstawić do niej samej, chyba że jest aplikacją SDI.

*Wklej specjalne*<br/>
To okno dialogowe pozwala użytkownikowi na kontrolowanie format używany podczas wklejania danych w dokumencie złożonym. Użytkownik może wybrać format danych, czy chcesz osadzić lub łączenia danych i czy ma być wyświetlana jako ikona. Wyświetl to okno dialogowe, gdy użytkownik wybierze Wklej specjalne z menu Edycja. Użyj [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) klasy, aby wyświetlić to okno dialogowe.

*Zmień ikonę*<br/>
To okno dialogowe umożliwia użytkownikowi wybranie ikony, która jest wyświetlana reprezentujący element osadzony lub połączony. Wyświetl to okno dialogowe, gdy użytkownik wybierze ikonę zmiany z menu Edycja lub wybierze przycisk Zmień ikonę Wklej specjalne lub konwertowanie, okno dialogowe. Również wyświetlać go po użytkownik otwiera okno dialogowe Wstawianie obiektu, a wyświetlana jako ikona. Użyj [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) klasy, aby wyświetlić to okno dialogowe.

*Konwertuj*<br/>
To okno dialogowe umożliwia użytkownikowi zmianę typu elementu osadzony lub połączony. Na przykład jeśli zostały osadzone metaplik w dokumencie złożonym, a później chcesz Użyj innej aplikacji, aby zmodyfikować metaplik osadzone, można użyć okno dialogowe Konwertowanie. To okno dialogowe jest zwykle wyświetlany przez kliknięcie przycisku *typ elementu* obiekt menu Edycja, a następnie w menu kaskadowych, klikając konwersji. Użyj [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md) klasy, aby wyświetlić to okno dialogowe. Aby uzyskać przykład, uruchom aplikację przykładową MFC OLE [OCLIENT](../visual-cpp-samples.md).

*Edytuj linki lub linki aktualizacji*<br/>
Okno dialogowe Edytuj linki umożliwia użytkownikowi zmianę informacji o źródle połączonego obiektu. Okno dialogowe aktualizacji łącza sprawdza źródeł połączone elementy w bieżącym oknie dialogowym i wyświetla okno dialogowe Edytuj linki, jeśli to konieczne. Wyświetl okno dialogowe Edytuj linki, gdy użytkownik wybierze łącza z menu Edycja. Przy pierwszym otwarciu dokumencie złożonym, zwykle wyświetlane jest okno dialogowe aktualizacji linków. Użyj jednej [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) lub [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md) klasy, w zależności od tego, okno dialogowe, które mają być wyświetlane.

*Serwer jest zajęty lub serwer nie odpowiada*<br/>
Serwer jest zajęty okno dialogowe jest wyświetlany, gdy użytkownik próbuje uaktywnić element i serwer nie może obecnie obsłużyć żądania, zazwyczaj, ponieważ serwer jest używany przez innego użytkownika lub zadanie. Jeśli serwer nie odpowiada na żądania uaktywnienia na wszystkich, zostanie wyświetlone okno dialogowe serwer nie odpowiada. Okna te są wyświetlane przy użyciu `COleMessageFilter`zgodnie z implementacją interfejsu OLE `IMessageFilter`, i użytkownik może podjąć decyzję o próbę żądania aktywacji. Użyj [COleBusyDialog](../mfc/reference/colebusydialog-class.md) klasy, aby wyświetlić to okno dialogowe.

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[OLE](../mfc/ole-in-mfc.md)
