---
title: Tworzenie menu wyskakujących | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- context menus, Menu Editor
- pop-up menus, creating
- menus, pop-up
- menus, creating
- shortcut menus, creating
- pop-up menus, displaying
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 218ed28a8b44100beead46ab13e04ad07d86c7e5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="creating-pop-up-menus"></a>Tworzenie menu wyskakujących
[Menu wyskakujące](../mfc/menus-mfc.md) wyświetlania często używanych poleceń. Mogą to być kontekstowa do lokalizacji wskaźnika. Za pomocą menu podręcznego w aplikacji wymaga tworzenia samo menu, a następnie łącząc go do kodu aplikacji.  
  
 Po utworzeniu zasobu menu kod aplikacji musi załadować zasobu menu i użyj [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) spowodować są wyświetlane w menu. Po użytkownik ma ukryty menu podręczne przez kliknięcie poza nią lub po kliknięciu polecenia, ta funkcja zwróci. Jeśli użytkownik wybierze polecenie, komunikat tego polecenia będą wysyłane do okna, którego uchwyt został przekazany.  
  
### <a name="to-create-a-pop-up-menu"></a>Aby utworzyć menu podręczne  
  
1.  [Tworzenie menu](../windows/creating-a-menu.md) z pustym tytułem (nie udostępniają **podpis**).  
  
2.  [Dodawanie polecenia menu do nowego menu](../windows/adding-commands-to-a-menu.md). Przejście do pierwszego polecenia menu pod tytułem puste menu (tymczasowego podpis mówi typu w tym miejscu). Wpisz **podpis** i inne informacje.  
  
     Powtórz te kroki dla innych poleceń menu w menu podręcznym.  
  
3.  Zapisz zasobów menu.  
  
    > [!TIP]
    >  Aby uzyskać więcej informacji o wyświetlaniu menu podręczne, zobacz [wyświetlanie jako Menu podręcznego](../windows/viewing-a-menu-as-a-pop-up-menu.md).  
  

  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Łączenie Menu wyskakującego do aplikacji](../windows/connecting-a-pop-up-menu-to-your-application.md)   
 [Edytor menu](../windows/menu-editor.md)