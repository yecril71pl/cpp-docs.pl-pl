---
title: Przeciąganie obrazów z listy obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
ms.openlocfilehash: 3035e6f21d38568b364fce02358c3baed4870bc3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508652"
---
# <a name="dragging-images-from-an-image-list"></a>Przeciąganie obrazów z listy obrazów

[Korzystanie CImageList](../mfc/reference/cimagelist-class.md) zawiera funkcje do przeciągnięcia obrazu na ekranie. Funkcja przeciągania bezproblemowo przenosi obraz, w kolorze i bez migotania kursora. Można przeciągać zarówno obrazy maskowane, jak i niemaskowane.

Funkcja członkowska [BeginDrag](../mfc/reference/cimagelist-class.md#begindrag) rozpoczyna operację przeciągania. Parametry obejmują indeks obrazu do przeciągnięcia i lokalizację punktu aktywnego w obrazie. Gorąca plamka to jeden piksel, który funkcja przeciągania rozpoznaje jako dokładną lokalizację ekranu obrazu. Zazwyczaj aplikacja ustawia punkt aktywny, tak aby był zgodny z gorącą plamą kursora myszy. Funkcja członkowska [DragMove](../mfc/reference/cimagelist-class.md#dragmove) przenosi obraz do nowej lokalizacji.

Funkcja członkowska [DragEnter](../mfc/reference/cimagelist-class.md#dragenter) ustawia początkową pozycję przeciąganego obrazu w oknie i rysuje obraz na pozycji. Parametry obejmują wskaźnik do okna, w którym narysujesz obraz, i punkt, który określa współrzędne początkowej pozycji w oknie. Współrzędne są względem lewego górnego rogu okna, a nie obszaru klienckiego. To samo jest prawdziwe dla wszystkich funkcji przeciągania obrazu, które przyjmują współrzędne jako parametry. Oznacza to, że należy wyrównać szerokość elementów okna, takich jak obramowanie, pasek tytułu i pasek menu, podczas określania współrzędnych. Jeśli określisz uchwyt okna o **wartości null** podczas `DragEnter`wywoływania, funkcja przeciągania rysuje obraz w kontekście urządzenia skojarzonym z oknem pulpitu, a współrzędne są względne w lewym górnym rogu ekranu.

`DragEnter`blokuje wszystkie pozostałe aktualizacje danego okna podczas operacji przeciągania. Jeśli musisz wykonać dowolny rysunek podczas operacji przeciągania, na przykład podświetlić obiekt docelowy operacji przeciągania i upuszczania, możesz tymczasowo ukryć przeciągany obraz przy użyciu funkcji składowej [zdarzenie DragLeave](../mfc/reference/cimagelist-class.md#dragleave) . Można również użyć funkcji składowej [DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock) .

Wywołaj [endDrag](../mfc/reference/cimagelist-class.md#enddrag) , gdy skończysz przeciąganie obrazu.

Funkcja członkowska [SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage) tworzy nowy obraz przeciągany przez połączenie danego obrazu (zazwyczaj obraz kursora myszy) z bieżącym przeciąganym obrazem. Ponieważ funkcje przeciągania używają nowego obrazu podczas operacji przeciągania, należy użyć funkcji [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) systemu Windows, aby ukryć rzeczywisty wskaźnik myszy po wywołaniu `SetDragCursorImage`. W przeciwnym razie system może wydawać dwa kursory myszy na czas trwania operacji przeciągania.

Gdy aplikacja wywołuje `BeginDrag`program, system tworzy tymczasową, wewnętrzną listę obrazów i kopiuje określony obraz przeciągnij do listy wewnętrznej. Możesz pobrać wskaźnik do listy tymczasowych przeciąganych obrazów przy użyciu funkcji składowej [GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage) . Funkcja pobiera również bieżącą pozycję przeciągania i Przesunięcie obrazu przeciągnij względem pozycji przeciągania.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
