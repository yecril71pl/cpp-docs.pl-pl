---
title: Operacje przeciągania i upuszczania formantu drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: c7febeec513d8004df2bd1cc42e4e97e027e9f17
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286312"
---
# <a name="tree-control-drag-and-drop-operations"></a>Operacje przeciągania i upuszczania formantu drzewa

Kontrolka drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) wysyła powiadomienie, gdy użytkownik rozpoczyna przeciągnij element. Kontrolka wysyła [TVN_BEGINDRAG](/windows/desktop/Controls/tvn-begindrag) komunikat powiadomienia, gdy użytkownik rozpoczyna przeciągania elementu z lewym przyciskiem myszy i [TVN_BEGINRDRAG](/windows/desktop/Controls/tvn-beginrdrag) komunikat powiadomienia, gdy użytkownik rozpoczyna, przeciągając go Prawy przycisk. Kontrolka drzewa można zapobiec wysyłania powiadomień, zapewniając styl TVS_DISABLEDRAGDROP kontrolki drzewa.

Uzyskanie obrazu do wyświetlenia w czasie trwania operacji przeciągania, wywołując [CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) funkcja elementu członkowskiego. Kontrolka drzewa tworzy mapę bitową przeciągania na podstawie etykiety elementu przeciąganie. Następnie tworzy listy obrazów kontrolki drzewa, dodaje mapę bitową i zwraca wskaźnik do [CImageList](../mfc/reference/cimagelist-class.md) obiektu.

Należy podać kod, który faktycznie przeciągnięty element. Zazwyczaj wiąże się to przy użyciu funkcji przeciągania funkcji listy obrazów i przetwarzanie [WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove) i [WM_LBUTTONUP](/windows/desktop/inputdev/wm-lbuttonup) (lub [WM_RBUTTONUP](/windows/desktop/inputdev/wm-rbuttonup)) Komunikaty wysyłane po rozpoczęciu operacji przeciągania. Aby uzyskać więcej informacji na temat funkcji listy obrazów, zobacz [CImageList](../mfc/reference/cimagelist-class.md) w *odwołanie MFC* i [listy obrazów](/windows/desktop/controls/image-lists) w zestawie Windows SDK. Aby uzyskać więcej informacji na temat przeciągania elementu kontrolki drzewa, zobacz [przeciągnięcie elementu widoku drzewa](/windows/desktop/Controls/tree-view-controls), również w zestawie Windows SDK.

W przypadku elementów kontrolki drzewa jako obiekty docelowe operacji przeciągania i upuszczania, musisz wiedzieć, gdy wskaźnik myszy znajduje się na element docelowy. Możesz dowiedzieć się, wywołując [hitTest —](../mfc/reference/ctreectrl-class.md#hittest) funkcja elementu członkowskiego. Określ punkt i liczby całkowitej lub adres [TVHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvhittestinfo) strukturę, która zawiera bieżące współrzędne kursora myszy. Po powrocie z tej funkcji liczby całkowitej lub struktura zawiera flagę wskazującą położenie kursora myszy względem kontrolki drzewa. Jeśli kursor znajduje się nad elementem w drzewie, struktura zawiera dojście także elementu.

Można wskazać, że element jest obiekt docelowy operacji przeciągania i upuszczania, wywołując [SetItem](../mfc/reference/ctreectrl-class.md#setitem) funkcja elementu członkowskiego, aby ustawić stan `TVIS_DROPHILITED` wartość. Element, który ma ten stan jest rysowana w stylu służy do wskazywania docelowej przeciągania i upuszczania.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
