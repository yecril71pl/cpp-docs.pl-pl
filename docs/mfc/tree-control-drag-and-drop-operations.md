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
ms.openlocfilehash: 73aa47a2d888c88dd58d114dd4f5ca9a3f086cd3
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956255"
---
# <a name="tree-control-drag-and-drop-operations"></a>Operacje przeciągania i upuszczania kontrolki drzewa
Formant drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) wysyła powiadomienie, gdy użytkownik uruchomi przeciągnij element. Formant wysyła [TVN_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773504) powiadomienie, gdy użytkownik rozpocznie przeciąganie elementu z lewego przycisku myszy i [TVN_BEGINRDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773509) powiadomienie, gdy użytkownik rozpocznie przeciąganie z Prawy przycisk. Formant drzewa uniemożliwi wysyłanie te powiadomienia, zapewniając drzewie styl TVS_DISABLEDRAGDROP.  
  
 Uzyskaj obraz, który będzie wyświetlany podczas operacji przeciągania, wywołując [CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) funkcję elementu członkowskiego. Formant drzewa tworzy przeciągania mapy bitowej na podstawie etykiety przeciąganie elementu. Następnie tworzy listy obrazów formantu drzewa, dodaje mapy bitowej do niej i zwraca wskaźnik do [CImageList](../mfc/reference/cimagelist-class.md) obiektu.  
  
 Należy podać kod, który faktycznie przeciąga element. Zazwyczaj wiąże się to przy użyciu funkcji przeciągania obrazu funkcji listy i przetwarzanie [WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) i [WM_LBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms645608) (lub [WM_RBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms646243)) Komunikaty wysyłane po rozpoczęciu operacji przeciągania. Aby uzyskać więcej informacji na temat funkcji listy obrazów, zobacz [CImageList](../mfc/reference/cimagelist-class.md) w *odwołania MFC* i [listy obrazów](http://msdn.microsoft.com/library/windows/desktop/bb761389) w zestawie Windows SDK. Aby uzyskać więcej informacji na temat przeciągania elementu formantu drzewa, zobacz [przeciąganie elementu widoku drzewa](http://msdn.microsoft.com/library/windows/desktop/bb760017), również w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 W przypadku elementów formantu drzewa jako obiekty docelowe operacji przeciągania i upuszczania, musisz wiedzieć, gdy wskaźnik myszy znajduje się na element docelowy. Można sprawdzić, wywołując [HitTest](../mfc/reference/ctreectrl-class.md#hittest) funkcję elementu członkowskiego. Określ punkt i liczby całkowitej lub adres [TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448) strukturę, która zawiera bieżące współrzędne kursora myszy. Po powrocie z funkcji liczbą całkowitą lub struktura zawiera flagę wskazującą położenie kursora myszy względem formantu drzewa. Jeśli kursor znajduje się nad elementem w drzewie, struktura zawiera dojście również elementu.  
  
 Można wskazać, czy element jest elementem docelowym operacji przeciągania i upuszczania, wywołując [SetItem](../mfc/reference/ctreectrl-class.md#setitem) funkcji członkowskiej, aby ustawić stan `TVIS_DROPHILITED` wartość. Stanem tego elementu jest rysowana w stylu służy do określania docelowych przeciągania i upuszczania.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

