---
title: Bieżące zaznaczenie w formancie edycji wzbogaconej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5f0d9332d1118809ae3d62c187ec848ec95ffbf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="current-selection-in-a-rich-edit-control"></a>Bieżące zaznaczenie w formancie edycji wzbogaconej
Użytkownik może wybrać tekst w formancie edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) za pomocą myszy lub klawiatury. Bieżące zaznaczenie jest zakres wybranych znaków lub położenie punktu wstawiania, jeśli żadne znaki nie są wybrane. Aplikacji można uzyskać informacje na temat bieżącego zaznaczenia, ustawianie bieżącego zaznaczenia, określić, kiedy Zaznacz bieżące zaznaczenie zmiany i Pokaż lub Ukryj zaznaczenie.  
  
 Aby sprawdzić bieżące zaznaczenie w formancie edycji wzbogaconej, użyj [GetSel](../mfc/reference/cricheditctrl-class.md#getsel) funkcję elementu członkowskiego. Aby ustawić bieżącego zaznaczenia, użyj [SetSel](../mfc/reference/cricheditctrl-class.md#setsel) funkcję elementu członkowskiego. [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) struktura jest używana z tych funkcji, aby określić zakres znaków. Aby uzyskać informacje o zawartości bieżącego zaznaczenia, można użyć [GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype) funkcję elementu członkowskiego.  
  
 Domyślnie kontrolki zaawansowanej edycji pokazuje i ukrywa wyróżnienie zaznaczenia, kiedy uzyska i traci fokus. Możesz wyświetlić lub ukryć wyróżnienie zaznaczenia w dowolnej chwili za pomocą [hideselection zostanie](../mfc/reference/cricheditctrl-class.md#hideselection) funkcję elementu członkowskiego. Na przykład aplikacja może zawierać okno dialogowe wyszukiwania, aby wyszukać tekst w formancie edycji wzbogaconej. Aplikacja może wybrać szukanego tekstu bez zamykania okna dialogowego, w którym to przypadku należy użyć `HideSelection` zaznaczenie.  
  
 Aby uzyskać zaznaczonego tekstu w formancie edycji wzbogaconej, należy użyć [GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext) funkcję elementu członkowskiego. Tekst jest kopiowany do określoną tablicę znaków. Należy się upewnić, że tablica jest wystarczająco duży, aby pomieścić zaznaczonego tekstu oraz znak końcowy null.  
  
 Ciąg w formancie edycji wzbogaconej można wyszukiwać za pomocą [ciąg FindText](../mfc/reference/cricheditctrl-class.md#findtext) funkcji członkowskiej [FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909) struktury używane z tą funkcją określa zakres tekstu do wyszukiwania i ciąg do wyszukania. Można również określić takie opcje jak czy wyszukiwanie uwzględnia wielkość liter.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

