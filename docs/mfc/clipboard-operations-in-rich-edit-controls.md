---
title: Operacje schowka w zaawansowanej edycji kontrolki | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ec468b1f763e2f855f25fd8808d83605fb10673a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Operacje schowka w formantach edycji wzbogaconej
Aplikacja może Wklej zawartość Schowka do kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) przy użyciu określonego formatu Schowka lub najlepiej dostępne formatu Schowka. Można również określić, czy kontrolki zaawansowanej edycji jest w stanie wklejanie formatu Schowka.  
  
 Można skopiować lub wyciąć zawartości bieżącego zaznaczenia przy użyciu [kopiowania](../mfc/reference/cricheditctrl-class.md#copy) lub [Wytnij](../mfc/reference/cricheditctrl-class.md#cut) funkcję elementu członkowskiego. Podobnie, Wklej zawartość Schowka w formantach edycji wzbogaconej przy użyciu [Wklej](../mfc/reference/cricheditctrl-class.md#paste) funkcję elementu członkowskiego. Formant wkleja pierwszy dostępny formacie, który rozpoznaje, który prawdopodobnie jest format najbardziej opisowy.  
  
 Aby wkleić określonego formatu Schowka, można użyć [PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial) funkcję elementu członkowskiego. Ta funkcja jest przydatna do aplikacji za pomocą polecenia Wklej specjalne, które umożliwia użytkownikowi wybranie formatu Schowka. Można użyć [CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste) funkcji członkowskiej, aby określić, czy dany format jest rozpoznawana przez formant.  
  
 Można również użyć `CanPaste` ustalenie, czy wszystkie dostępne formatu Schowka jest rozpoznawana przez kontrolkę zaawansowanej edycji. Ta funkcja jest przydatna w `OnInitMenuPopup` programu obsługi. Aplikacja może włączyć lub szary polecenia Wklej w zależności od tego, czy formant można wkleić dostępnych formatów.  
  
 Zaawansowanej edycji kontrolki rejestru dwa formaty Schowka: tekst sformatowany i format nazywany RichEdit tekstu i obiektów. Aplikację można zarejestrować tych formatów za pomocą [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) działanie, określając **CF_RTF** i **CF_RETEXTOBJ** wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

