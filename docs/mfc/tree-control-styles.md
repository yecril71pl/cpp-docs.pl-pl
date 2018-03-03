---
title: Style formantu drzewa | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
dev_langs:
- C++
helpviewer_keywords:
- TVS_LINESATROOT [MFC]
- styles [MFC], CTreeCtrl
- styles [MFC], tree control
- TVS_HASLINES
- TVS_SINGLEEXPAND
- CTreeCtrl class [MFC], styles
- TVS_EDITLABELS [MFC]
- TVS_NOTOOLTIPS [MFC]
- TVS_HASBUTTONS [MFC]
- tree controls [MFC], styles
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c141a2b0db673f8d3c5f2c116de5b5d2ec81a8ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-styles"></a>Style kontrolki drzewa
Kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) style regulują aspektów wygląd formantu drzewa. Można ustawić style początkowej podczas tworzenia formantu drzewa. Możesz pobrać i zmieniać style po utworzeniu drzewie przy użyciu [GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) i [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) funkcje systemu Windows, określając **GWL_STYLE** dla `nIndex` parametru. Aby uzyskać pełną listę style, zobacz [Style okna kontrolki widoku drzewa](http://msdn.microsoft.com/library/windows/desktop/bb760013) w zestawie Windows SDK.  
  
 **TVS_HASLINES** styl zwiększa graficzną reprezentację formantem drzewa hierarchii za pomocą rysowania linii połączonych elementów podrzędnych ich odpowiedniego elementu nadrzędnego. Ten styl nie połączyć elementy w elemencie głównym hierarchii. Aby to zrobić, należy połączyć **TVS_HASLINES** i **TVS_LINESATROOT** style.  
  
 Użytkownik może rozwinąć lub zwinąć listy elementów podrzędnych elementu nadrzędnego przez dwukrotne kliknięcie elementu nadrzędnego. Formant drzewa, który ma **TVS_SINGLEEXPAND** stylu powoduje, że element wybierana, aby rozwinąć i anulować tak, aby zwinąć elementu. Jeśli wskaźnik myszy jest używany do wybranego elementu jednym kliknięciem i tego elementu jest zamknięty, będą rozszerzane. Wybrany element jest kliknięte raz otwarty, będzie zwinięte.  
  
 Formant drzewa, który ma **TVS_HASBUTTONS** styl dodaje przycisku po lewej stronie każdego elementu nadrzędnego. Użytkownik może kliknąć przycisk, aby rozwinąć lub zwinąć elementy podrzędne zamiast dwukrotnie element nadrzędny. **TVS_HASBUTTONS** nie dodawanie przycisków do elementów w elemencie głównym hierarchii. Aby to zrobić, należy połączyć **TVS_HASLINES**, **TVS_LINESATROOT**, i **TVS_HASBUTTONS**.  
  
 **TVS_EDITLABELS** styl umożliwia użytkownikowi edytowanie etykiety elementów formantu drzewa. Aby uzyskać więcej informacji na temat edytowania etykiet, zobacz [edytowanie etykiety formantu drzewa](../mfc/tree-control-label-editing.md) dalszej części tego tematu.  
  
 **TVS_NOTOOLTIPS** styl wyłącza funkcję automatycznego narzędzia Porada kontrolki widoku drzewa. Funkcja ta automatycznie wyświetla etykietki narzędzia, zawierający tytuł elementu pod kursorem myszy, jeśli cały tytuł nie jest widoczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

