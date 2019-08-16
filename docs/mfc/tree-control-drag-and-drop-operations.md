---
title: Operacje przeciągania i upuszczania formantu drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: 5d2c5aa511844a3d7cbe64d9a15f8ffb46046b29
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510907"
---
# <a name="tree-control-drag-and-drop-operations"></a>Operacje przeciągania i upuszczania formantu drzewa

Kontrolka drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) wysyła powiadomienie, gdy użytkownik rozpocznie przeciąganie elementu. Kontrolka wysyła komunikat powiadomienia [TVN_BEGINDRAG](/windows/win32/Controls/tvn-begindrag) , gdy użytkownik rozpocznie przeciąganie elementu przy użyciu lewego przycisku myszy i komunikatu powiadomienia [TVN_BEGINRDRAG](/windows/win32/Controls/tvn-beginrdrag) , gdy użytkownik rozpocznie przeciąganie przy użyciu prawego przycisku. Można zapobiec wysyłaniu przez formant drzewa tych powiadomień, nadając formantowi drzewie styl TVS_DISABLEDRAGDROP.

Uzyskanie obrazu do wyświetlenia podczas operacji przeciągania przez wywołanie funkcji składowej [CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) . Formant drzewa tworzy mapę bitową w oparciu o etykietę przeciąganego elementu. Następnie formant drzewa tworzy listę obrazów, dodaje do niej mapę bitową i zwraca wskaźnik do obiektu [Korzystanie CImageList](../mfc/reference/cimagelist-class.md) .

Należy podać kod, który faktycznie przeciąga element. Zwykle polega to na użyciu możliwości przeciągania funkcji list obrazów i przetwarzania komunikatów [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) i [WM_LBUTTONUP](/windows/win32/inputdev/wm-lbuttonup) (lub [WM_RBUTTONUP](/windows/win32/inputdev/wm-rbuttonup)) wysyłanych po rozpoczęciu operacji przeciągania. Aby uzyskać więcej informacji na temat funkcji list obrazu, zobacz [Korzystanie CImageList](../mfc/reference/cimagelist-class.md) in the *MFC References* and [image lists](/windows/win32/controls/image-lists) in the Windows SDK. Aby uzyskać więcej informacji na temat przeciągania elementu kontrolki drzewa, zobacz przeciąganie [elementu widoku drzewa](/windows/win32/Controls/tree-view-controls), również w Windows SDK.

Jeśli elementy w formancie drzewa mają być obiektami docelowymi operacji przeciągania i upuszczania, musisz wiedzieć, kiedy wskaźnik myszy znajduje się na elemencie docelowym. Możesz sprawdzić, wywołując funkcję elementu członkowskiego [HitTest](../mfc/reference/ctreectrl-class.md#hittest) . Należy określić punkt i liczbę całkowitą albo adres struktury [TVHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tvhittestinfo) , która zawiera bieżące współrzędne kursora myszy. Gdy funkcja zwraca, liczba całkowita lub struktura zawiera flagę wskazującą lokalizację kursora myszy względem kontrolki drzewa. Jeśli kursor znajduje się nad elementem w kontrolce drzewa, struktura zawiera również uchwyt elementu.

Można wskazać, że element jest obiektem docelowym operacji przeciągania i upuszczania przez wywołanie funkcji elementu członkowskiego SetItem, aby ustawić stan na [](../mfc/reference/ctreectrl-class.md#setitem) `TVIS_DROPHILITED` wartość. Element, który ma ten stan, jest rysowany w stylu używanym do wskazywania docelowego przeciągania i upuszczania.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
