---
title: Przeciąganie i upuszczanie (OLE) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc23c7695bf5afa22734c382ddc72e8418ff74c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="drag-and-drop-ole"></a>Przeciąganie i upuszczanie (OLE)
Funkcja przeciągania i upuszczania OLE jest głównie skrót do kopiowania i wklejania danych. Gdy używasz Schowka do kopiowania lub wklej dane liczbę czynności są wymagane. Wybierz dane, kliknij przycisk **Wytnij** lub **kopiowania** z **Edytuj** menu, aby przejść do pliku docelowego, okna lub aplikacji, umieść kursor w odpowiedniej lokalizacji, a następnie kliknij przycisk **Wklej** z **Edytuj** menu.  
  
 Przeciąganie i upuszczanie OLE różni się od mechanizmu przeciągania i upuszczania Menedżera plików, który może obsługiwać tylko nazwy plików i jest zaprojektowany specjalnie w celu przekazania nazwy plików do aplikacji. Przeciąganie i upuszczanie OLE jest bardziej ogólne. Umożliwia ona przeciągnij i upuść dowolne dane, które można również można umieścić w Schowku.  
  
 Gdy używasz przeciąganie i upuszczanie OLE, należy usunąć dwa kroki w procesie. Wybierz dane, z okna źródła ("źródło porzucenia"), przeciągnij go do docelowej lokalizacji ("docelowy upuszczania") i upuść go przez zwolnieniem przycisku myszy. Operacja eliminuje potrzebę stosowania menu i jest krótszy sekwencji kopiowania i wklejania. Jedynym wymaganiem jest to, że listy źródłowej i miejsca docelowego musi być otwarte i co najmniej częściowo widoczne na ekranie.  
  
 Przy użyciu przeciąganie i upuszczanie OLE, dane można przenosić z jednej lokalizacji do drugiego w dokumencie, między różnymi dokumentami lub aplikacji. Można ją wdrożyć w kontenerze lub aplikacji serwera, a wszelkie aplikacje mogą być miejsca źródłowego i docelowego upuszczania. Jeśli aplikacja obsługuje zarówno miejsca źródłowego i docelowego upuszczania zaimplementowana, przeciągnij i upuść włączono między okno podrzędne lub w obrębie jednego okna. Tej funkcji można zwiększyć bezpieczeństwo aplikacji znacznie łatwiejsze do użycia.  
  
 Jeśli chcesz korzystać z funkcji przeciągania i upuszczania OLE, zobacz [przeciąganie i upuszczanie: dostosowywanie](../mfc/drag-and-drop-customizing.md). Można użyć technikach wyjaśnione w tym artykule można wprowadzić do aplikacji innych niż OLE porzucić źródeł. Artykuł [przeciąganie i upuszczanie: Implementowanie docelowego upuszczania](../mfc/drag-and-drop-implementing-a-drop-target.md) opisano, jak obsługa aplikacji innych niż OLE i OLE miejsca docelowego. Konieczne będzie również przydatne do sprawdzenia przykłady MFC OLE [OCLIENT](../visual-cpp-samples.md) i [HIERSVR](../visual-cpp-samples.md).  
  
 Jeśli nie znasz [obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md) rodziny artykuły, możesz to zrobić teraz. Artykuły te wyjaśniają zasady podstawowe informacje dotyczące transferu danych i jak ją wdrożyć w aplikacji.  
  
 Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania zobacz:  
  
-   [Przeciąganie i upuszczanie: implementowanie miejsca źródłowego](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [Przeciąganie i upuszczanie: implementowanie miejsca docelowego](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [Przeciąganie i upuszczanie: dostosowywanie](../mfc/drag-and-drop-customizing.md)  
  
## <a name="see-also"></a>Zobacz też  
 [OLE](../mfc/ole-in-mfc.md)   
 [Obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md)

