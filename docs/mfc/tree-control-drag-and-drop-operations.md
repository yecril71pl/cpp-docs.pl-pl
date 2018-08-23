---
title: Operacje przeciągania i upuszczania kontrolki drzewa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e1c642642f94c021001ae67d2dcc3fd87f4f287
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589088"
---
# <a name="tree-control-drag-and-drop-operations"></a>Operacje przeciągania i upuszczania kontrolki drzewa
Kontrolka drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) wysyła powiadomienie, gdy użytkownik rozpoczyna przeciągnij element. Kontrolka wysyła [TVN_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773504) komunikat powiadomienia, gdy użytkownik rozpoczyna przeciągania elementu z lewym przyciskiem myszy i [TVN_BEGINRDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773509) komunikat powiadomienia, gdy użytkownik rozpoczyna, przeciągając go Prawy przycisk. Kontrolka drzewa można zapobiec wysyłania powiadomień, zapewniając styl TVS_DISABLEDRAGDROP kontrolki drzewa.  
  
 Uzyskanie obrazu do wyświetlenia w czasie trwania operacji przeciągania, wywołując [CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) funkcja elementu członkowskiego. Kontrolka drzewa tworzy mapę bitową przeciągania na podstawie etykiety elementu przeciąganie. Następnie tworzy listy obrazów kontrolki drzewa, dodaje mapę bitową i zwraca wskaźnik do [CImageList](../mfc/reference/cimagelist-class.md) obiektu.  
  
 Należy podać kod, który faktycznie przeciągnięty element. Zazwyczaj wiąże się to przy użyciu funkcji przeciągania funkcji listy obrazów i przetwarzanie [WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) i [WM_LBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms645608) (lub [WM_RBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms646243)) Komunikaty wysyłane po rozpoczęciu operacji przeciągania. Aby uzyskać więcej informacji na temat funkcji listy obrazów, zobacz [CImageList](../mfc/reference/cimagelist-class.md) w *odwołanie MFC* i [listy obrazów](http://msdn.microsoft.com/library/windows/desktop/bb761389) w zestawie Windows SDK. Aby uzyskać więcej informacji na temat przeciągania elementu kontrolki drzewa, zobacz [przeciągnięcie elementu widoku drzewa](http://msdn.microsoft.com/library/windows/desktop/bb760017), również w zestawie Windows SDK.  
  
 W przypadku elementów kontrolki drzewa jako obiekty docelowe operacji przeciągania i upuszczania, musisz wiedzieć, gdy wskaźnik myszy znajduje się na element docelowy. Możesz dowiedzieć się, wywołując [hitTest —](../mfc/reference/ctreectrl-class.md#hittest) funkcja elementu członkowskiego. Określ punkt i liczby całkowitej lub adres [TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448) strukturę, która zawiera bieżące współrzędne kursora myszy. Po powrocie z tej funkcji liczby całkowitej lub struktura zawiera flagę wskazującą położenie kursora myszy względem kontrolki drzewa. Jeśli kursor znajduje się nad elementem w drzewie, struktura zawiera dojście także elementu.  
  
 Można wskazać, że element jest obiekt docelowy operacji przeciągania i upuszczania, wywołując [SetItem](../mfc/reference/ctreectrl-class.md#setitem) funkcja elementu członkowskiego, aby ustawić stan `TVIS_DROPHILITED` wartość. Element, który ma ten stan jest rysowana w stylu służy do wskazywania docelowej przeciągania i upuszczania.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

