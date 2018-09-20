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
ms.openlocfilehash: 498644a159c6472ed197fcadd28ad0236d62ca0b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389645"
---
# <a name="drag-and-drop-ole"></a>Przeciąganie i upuszczanie (OLE)

Funkcja przeciąganie i upuszczanie OLE jest głównie skrót do kopiowania i wklejania danych. Gdy używasz Schowka dotyczące kopiowania i wklejania danych szereg czynności są wymagane. Wybierz dane, kliknij przycisk **Wytnij** lub **kopiowania** z **Edytuj** menu, przejście do pliku docelowego, okno lub aplikacji, umieść kursor w odpowiednie miejsce, a następnie kliknij przycisk **Wklej** z **Edytuj** menu.

Przeciąganie i upuszczanie OLE różni się od mechanizmu przeciągania i upuszczania Menedżera plików, który może obsługiwać tylko nazwy plików i jest zaprojektowany specjalnie w celu przekazywania plików do aplikacji. Przeciąganie i upuszczanie OLE jest znacznie bardziej ogólne. Pozwala ona na przeciąganie i upuszczanie wszelkie dane, które można także umieścić w Schowku.

Korzystając z OLE przeciągania i upuszczania, możesz usunąć dwa kroki z procesu. Wybierz dane z okna źródła ("Źródło listy"), przeciągnij go do docelowej lokalizacji ("target listy") i upuść go przez zwolnieniem przycisku myszy. Operacja eliminuje potrzebę stosowania menu i jest szybsze niż sekwencji kopiowania/wklejania. Jedynym wymaganiem jest, że zarówno miejsca źródłowego, jak i miejsca docelowego musi być otwarty i co najmniej częściowo widoczne na ekranie.

Korzystając z OLE przeciągania i upuszczania, dane można przenieść z jednej lokalizacji do drugiej w ramach dokumentu, między różnymi dokumentami lub aplikacji. Można ją wdrożyć w kontenerze lub aplikacji serwera, a każda aplikacja może być miejsca źródłowego i/lub miejsca docelowego. Jeśli aplikacja obsługuje zarówno miejsca źródłowego i docelowego upuszczania zaimplementowane, przeciągania i upuszczania włączono między oknami podrzędnymi lub w obrębie jednego okna. Ta funkcja ułatwia aplikacji znacznie łatwiejsze do użycia.

Jeśli chcesz korzystać z możliwości przeciągania i upuszczania OLE, zobacz [przeciąganie i upuszczanie: dostosowywanie](../mfc/drag-and-drop-customizing.md). Za pomocą techniki opisane w tym artykule można wprowadzić do aplikacji innych niż OLE, Porzuć źródeł. Artykuł [przeciąganie i upuszczanie: Implementowanie docelowego upuszczania](../mfc/drag-and-drop-implementing-a-drop-target.md) w tym artykule opisano sposób wdrażania docelowego upuszczania obsługę zarówno OLE, jak i aplikacji innych niż OLE. Konieczne będzie również przydatne zbadać przykłady MFC OLE [OCLIENT](../visual-cpp-samples.md) i [HIERSVR](../visual-cpp-samples.md).

Jeśli nie znasz [obiekty danych i źródeł danych (OLE)](../mfc/data-objects-and-data-sources-ole.md) rodziny artykuły, możesz to zrobić teraz. Artykuły te wyjaśniają zasady podstawowe informacje dotyczące transferu danych i sposobie jego implementowania w swoich aplikacjach.

Aby uzyskać więcej informacji na temat przeciągania i upuszczania zobacz:

- [Przeciąganie i upuszczanie: implementowanie miejsca źródłowego](../mfc/drag-and-drop-implementing-a-drop-source.md)

- [Przeciąganie i upuszczanie: implementowanie miejsca docelowego](../mfc/drag-and-drop-implementing-a-drop-target.md)

- [Przeciąganie i upuszczanie: dostosowywanie](../mfc/drag-and-drop-customizing.md)

## <a name="see-also"></a>Zobacz też

[OLE](../mfc/ole-in-mfc.md)<br/>
[Obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md)

