---
title: Przeciąganie obrazów z listy obrazów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb872cba298d6d18ab5287a285b22d2f568fa04b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382378"
---
# <a name="dragging-images-from-an-image-list"></a>Przeciąganie obrazów z listy obrazów

[CImageList](../mfc/reference/cimagelist-class.md) obejmuje funkcje przeznaczone dla przeciąganie obrazu na ekranie. Funkcje przeciągania przenoszenie obrazu sprawnie, kolor i bez żadnych migania kursora. Zarówno w przypadku maskowana, jak i usunąć ich maskowanie obrazy mogą być przeciągnięte.

[BeginDrag](../mfc/reference/cimagelist-class.md#begindrag) funkcja elementu członkowskiego zaczyna się operacja przeciągania. Parametry zawierają indeks obrazu, aby przeciągnąć i lokalizacja punktu aktywnego w obrazie. Punkt aktywny jest piksela, która przeciągania funkcji jest rozpoznawana jako lokalizacja ekranu dokładnego obrazu. Zazwyczaj aplikacja ustawia punkt aktywny tak, aby go pokrywa się z aktywnego punktu kursora myszy. [DragMove](../mfc/reference/cimagelist-class.md#dragmove) funkcja elementu członkowskiego przenosi obrazu do nowej lokalizacji.

[DragEnter](../mfc/reference/cimagelist-class.md#dragenter) funkcja elementu członkowskiego Ustawia położenie początkowe elementu przeciągnij obraz w ramach okna i rysuje obraz w położeniu. Parametry to wskaźnik do okna, w którym do rysowania obrazu i punkt, który określa współrzędne początkowe położenie w oknie. Współrzędne są względne wobec oknie w lewym górnym rogu, nie obszaru klienta. Dotyczy to wszystkich obrazów, przeciągając funkcje, których współrzędne jako parametry. Oznacza to, że należy kompensuje szerokości okna elementów, takich jak obramowania paska tytułu i pasek menu, określając współrzędne. Jeśli określisz **NULL** uchwyt okna podczas wywoływania `DragEnter`funkcji przeciągania narysuj obraz w kontekście urządzenia skojarzone z okna pulpitu i współrzędne są podawane względem lewego górnego rogu ekranu.

`DragEnter` blokuje wszystkie inne aktualizacje do danego okna podczas operacji przeciągania. Jeśli musisz wykonać dowolnego rysunku podczas operacji przeciągania, takich jak wyróżnianie obiekt docelowy operacji przeciągania i upuszczania, można tymczasowo ukryć przeciąganego obrazu za pomocą [DragLeave](../mfc/reference/cimagelist-class.md#dragleave) funkcja elementu członkowskiego. Można również użyć [DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock) funkcja elementu członkowskiego.

Wywołaj [EndDrag](../mfc/reference/cimagelist-class.md#enddrag) po zakończeniu przeciągnięcie obrazu.

[SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage) funkcja elementu członkowskiego tworzy nowy obraz przeciągania, łącząc danego obrazu (zazwyczaj obraz kursora myszy) z bieżącego obrazu przeciągania. Ponieważ funkcje przeciągania korzystała z nowego obrazu w czasie trwania operacji przeciągania, należy używać Windows [wartość](/windows/desktop/api/winuser/nf-winuser-showcursor) funkcję, aby ukryć rzeczywiste kursor po wywołaniu `SetDragCursorImage`. W przeciwnym razie system może być w dwóch kursory myszy na czas trwania operacji przeciągania.

Kiedy aplikacja wywołuje `BeginDrag`, system tworzy listę obrazu tymczasowego, wewnętrzne i kopiuje określony przeciągnij obraz do wewnętrznej listy. Wskaźnik do listy obrazów tymczasowe przeciągania można pobrać za pomocą [GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage) funkcja elementu członkowskiego. Funkcja pobiera również bieżącej pozycji przeciągania i przesunięcie przeciągnij obraz względem pozycji przeciągania.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

