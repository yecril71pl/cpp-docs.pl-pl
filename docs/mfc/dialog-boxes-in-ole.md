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
ms.openlocfilehash: 997bfc0bda05f5a2520c102cb38777b533bcef95
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685780"
---
# <a name="dialog-boxes-in-ole"></a>Okna dialogowe w OLE

Gdy użytkownik uruchamia aplikację z obsługą technologii OLE, są sytuacje, gdy aplikacja wymaga informacji od użytkownika w celu wykonania operacji. Klasy OLE MFC udostępniają wiele okien dialogowych, które umożliwiają zebranie wymaganych informacji. W tym temacie wymieniono zadania obsługiwane przez okna dialogowe OLE i klasy potrzebne do wyświetlania tych okien dialogowych. Aby uzyskać szczegółowe informacje o oknach dialogowych OLE i strukturach używanych do dostosowywania ich zachowań, zobacz [dokumentacja MFC](../mfc/mfc-desktop-applications.md).

*Wstaw obiekt*<br/>
To okno dialogowe umożliwia użytkownikowi Wstawianie nowo utworzonych lub istniejących obiektów do dokumentu złożonego. Umożliwia także użytkownikowi wybranie wyświetlania elementu jako ikony i włączenie przycisku polecenia Zmień ikonę. Wyświetl to okno dialogowe, gdy użytkownik wybierze pozycję Wstaw obiekt z menu Edycja. Użyj klasy [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) , aby wyświetlić to okno dialogowe. Należy pamiętać, że nie można wstawić aplikacji MDI do samej siebie. Aplikacji, która jest kontenerem/serwerem, nie można wstawić do samego siebie, chyba że jest to aplikacja SDI.

*Wklej specjalnie*<br/>
To okno dialogowe umożliwia użytkownikowi sterowanie formatem używanym podczas wklejania danych do dokumentu złożonego. Użytkownik może wybrać format danych, czy osadzić lub połączyć dane oraz czy wyświetlać ją jako ikonę. Wyświetl to okno dialogowe, gdy użytkownik wybierze opcję Wklej specjalnie z menu Edycja. Użyj klasy [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) , aby wyświetlić to okno dialogowe.

*Zmień ikonę*<br/>
To okno dialogowe umożliwia użytkownikowi wybranie ikony, która będzie reprezentować połączony lub osadzony element. Wyświetl to okno dialogowe, gdy użytkownik wybierze pozycję Zmień ikonę z menu Edycja lub wybierz przycisk Zmień ikonę w oknach dialogowych Wklej specjalnie lub Konwertuj. Wyświetlaj również, gdy użytkownik otwiera okno dialogowe Wstawianie obiektu i wybiera pozycję Wyświetl jako ikonę. Użyj klasy [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) , aby wyświetlić to okno dialogowe.

*Zamian*<br/>
To okno dialogowe umożliwia użytkownikowi zmianę typu osadzonego lub połączonego elementu. Na przykład jeśli osadzono metaplik w dokumencie złożonym, a później chcesz użyć innej aplikacji do zmodyfikowania osadzonego metapliku, możesz użyć okna dialogowego Konwertuj. To okno dialogowe jest zwykle wyświetlane po kliknięciu pozycji obiekt *Typ elementu* w menu Edycja, a następnie w menu kaskadowym, klikając polecenie Konwertuj. Użyj klasy [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md) , aby wyświetlić to okno dialogowe. Aby zapoznać się z przykładem, uruchom przykład MFC OLE [OCLIENT](../overview/visual-cpp-samples.md).

*Edytuj linki lub Aktualizuj linki*<br/>
Okno dialogowe Edytowanie linków umożliwia użytkownikowi zmianę informacji o źródle połączonego obiektu. Okno dialogowe Aktualizowanie linków weryfikuje źródła wszystkich połączonych elementów w bieżącym oknie dialogowym i w razie potrzeby wyświetla okno dialogowe Edytowanie linków. Wyświetl okno dialogowe Edytowanie linków, gdy użytkownik wybierze linki z menu Edycja. Po pierwszym otwarciu dokumentu złożonego jest zwykle wyświetlane okno dialogowe linki do aktualizacji. Użyj klasy [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) lub [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md) , w zależności od tego, które okno dialogowe ma być wyświetlane.

*Serwer jest zajęty lub serwer nie odpowiada*<br/>
Okno dialogowe zajęty serwer jest wyświetlane, gdy użytkownik próbuje aktywować element, a serwer nie może obecnie obsłużyć żądania, zwykle ponieważ serwer jest używany przez innego użytkownika lub zadanie. Okno dialogowe serwer nie odpowiada jest wyświetlane, jeśli serwer nie odpowiada na żądanie aktywacji. Te okna dialogowe są wyświetlane za pośrednictwem `COleMessageFilter`, na podstawie implementacji interfejsu OLE `IMessageFilter`, a użytkownik może zdecydować, czy ponowić próbę żądania aktywacji. Użyj klasy [COleBusyDialog](../mfc/reference/colebusydialog-class.md) , aby wyświetlić to okno dialogowe.

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[SERWERY](../mfc/ole-in-mfc.md)
