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
ms.openlocfilehash: d54984cdc1dc7897fb4f5d1d9680c6a2b95a787d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dragging-images-from-an-image-list"></a>Przeciąganie obrazów z listy obrazów
[Cimagelist —](../mfc/reference/cimagelist-class.md) obejmuje funkcje dla przeciąganie obrazu na ekranie. Funkcje przeciągania sprawnie, przenoszenie obrazu w kolorze i bez żadnych migania kursora. Obrazy zarówno maskowanego i zamaskowana można przeciągnąć.  
  
 [Elementu BeginDrag](../mfc/reference/cimagelist-class.md#begindrag) funkcji członkowskiej rozpoczyna się operacja przeciągania. Parametry zawierają indeks obrazu do przeciągnięcia i położenie punktu aktywnego w obrazie. Punkt aktywny jest piksela funkcji przeciągania rozpoznawany jako lokalizacji ekranu dokładnego obrazu. Zazwyczaj aplikacji ustawia punkt aktywny, aby go pokrywa się z punktu aktywnego kursora myszy. [DragMove](../mfc/reference/cimagelist-class.md#dragmove) funkcji członkowskiej przenosi obrazu do nowej lokalizacji.  
  
 [DragEnter](../mfc/reference/cimagelist-class.md#dragenter) funkcji członkowskiej ustawia początkowe położenie obrazu przeciągnij w ramach okna i rysuje obraz w pozycji. Parametry zawierają wskaźnik do okna, w którym do rysowania obrazu i punkt, który określa współrzędne początkowe położenie okna. Współrzędne są podawane względem oknie w lewym górnym rogu, nie obszaru klienckiego. To samo dotyczy wszystkich przeciąganie obrazu funkcje, których współrzędne jako parametry. Oznacza to, że należy kompensacji szerokości okna elementów, takich jak obramowania paska tytułu i paska menu, określając współrzędne. Jeśli określisz **NULL** uchwytu okna podczas wywoływania metody `DragEnter`funkcji przeciągania rysowania obrazu w kontekście urządzenia skojarzony z oknem pulpitu i współrzędne są podawane względem lewego górnego rogu ekranu.  
  
 `DragEnter` Umożliwia zablokowanie wszystkich aktualizacji do okna danego podczas operacji przeciągania. Jeśli trzeba dowolnego rysunku podczas operacji przeciągania, takich jak wyróżnianie obiekt docelowy operacji przeciągania i upuszczania, można ukryć przeciąganego obrazu przy użyciu [DragLeave](../mfc/reference/cimagelist-class.md#dragleave) funkcję elementu członkowskiego. Można również użyć [DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock) funkcję elementu członkowskiego.  
  
 Wywołanie [EndDrag](../mfc/reference/cimagelist-class.md#enddrag) po zakończeniu przeciąganie obrazu.  
  
 [SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage) funkcji członkowskiej tworzy nowy obraz przeciągania łącząc danego obrazu (zwykle obraz kursora myszy) z bieżącego obrazu przeciągania. Ponieważ funkcji przeciągania korzystała z nowego obrazu podczas operacji przeciągania, należy używać systemu Windows [wartość](http://msdn.microsoft.com/library/windows/desktop/ms648396) Ukryj wskaźnik myszy rzeczywiste po wywołaniu funkcji `SetDragCursorImage`. W przeciwnym razie system może być w dwóch kursory myszy w czasie trwania operacji przeciągania.  
  
 Gdy aplikacja wywołuje `BeginDrag`, system tworzy listę tymczasowego, wewnętrzny obrazu i kopiuje określony przeciągnij obrazu do wewnętrznej listy. Wskaźnik do tymczasowej przeciągania listy obrazów można pobrać za pomocą [GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage) funkcję elementu członkowskiego. Funkcja również pobiera bieżącą pozycję przeciągania i przesunięcie obrazu przeciągania położeniu przeciągania.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CImageList](../mfc/using-cimagelist.md)   
 [Kontrolki](../mfc/controls-mfc.md)

