---
title: Zastępowanie funkcji wirtualnych (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.virtualfunc.override
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
ms.openlocfilehash: 193c84d2b9a0fe50ae84d3e69834feab27342042
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484142"
---
# <a name="overriding-a-virtual-function-visual-c"></a>Zastępowanie funkcji wirtualnych (Visual C++)

Możesz przesłonić funkcji wirtualnych zdefiniowanych w klasie bazowej programu Visual Studio [okno właściwości](/visualstudio/ide/reference/properties-window).

### <a name="to-override-a-virtual-function-in-the-properties-window"></a>Aby przesłonić funkcji wirtualnej w oknie dialogowym właściwości

1. W widoku klas kliknij klasy.

1. W oknie dialogowym właściwości kliknij **zastępuje** przycisku.

   > [!NOTE]
   >  **Zastępuje** przycisk jest dostępny po wybraniu nazwy klasy w widoku klas lub po kliknięciu w oknie źródła.

   Kolumna po lewej stronie zawiera funkcje wirtualne. Jeśli nazwa funkcji wirtualnej pojawi się również w prawej kolumnie, zastąpienie już została zaimplementowana.

1. Jeśli funkcja nie ma żadnych override, następnie kliknij komórkę w prawej kolumnie w oknie dialogowym właściwości, aby wyświetlić sugerowane nazwę funkcji zastępują jako \<Dodaj >*FuncName*.

1. Kliknij nazwę sugerowaną można dodać kodu klasy zastępczej dla funkcji.

1. Aby edytować funkcji przez nadrzędne, kliknij dwukrotnie nazwę funkcji w widoku klas i edytowanie kodu w oknie źródła.

Aby usunąć zastąpienia, kliknij nazwę funkcji zastąpienie w prawej kolumnie, a następnie wybierz \<Usuń >*FuncName*. Kod funkcji jest opatrzona komentarzem.

## <a name="see-also"></a>Zobacz też

[Dodawanie funkcji za pomocą kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)<br>
[Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)<br>
[Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)<br>
[Handler komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[Nawigacja w strukturze klas](../ide/navigating-the-class-structure-visual-cpp.md)