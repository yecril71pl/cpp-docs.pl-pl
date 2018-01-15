---
title: "Dodawanie poleceń do Menu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.menu
dev_langs: C++
helpviewer_keywords:
- menu items, adding to menus
- menus, adding items
- commands, adding to menus
- commands
- menu items
ms.assetid: 1523a755-0ab5-42f8-9e98-bb9881564431
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d53f868fd76877152bb3ec81fdba85c1d97b3aac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="adding-commands-to-a-menu"></a>Dodawanie poleceń do menu
### <a name="to-add-commands-to-a-menu"></a>Aby dodać polecenia do menu  
  
1.  [Tworzenie menu](../windows/creating-a-menu.md).  
  
2.  Kliknij nazwę menu, na przykład plik.  
  
     Każdego menu będzie Rozwiń i ujawnia pole nowego elementu poleceń. Na przykład można dodać nowego polecenia, otwierać i zamykać do menu Plik.  
  
3.  W polu Nowy element wpisz nazwę nowego polecenia menu.  
  
    > [!NOTE]
    >  Wpisywania tekstu w edytorze Menu, a w **podpis** polu [okna właściwości](/visualstudio/ide/reference/properties-window). Można edytować właściwości dla Twojego nowego menu w dowolnej lokalizacji.  
  
    > [!TIP]
    >  Można zdefiniować klawisz skrótu (klawisza dostępu), który umożliwia użytkownikowi wybranie polecenia menu. Wpisz znak (&) przed literą, aby określić go jako klawisz skrótu. Użytkownik może wybrać polecenie menu, wpisując litery.  
  
4.  W oknie właściwości wybierz właściwości poleceń menu, które są stosowane. Aby uzyskać więcej informacji, zobacz [właściwości poleceń Menu](../windows/menu-command-properties.md).  
  
5.  W **wiersza** pola w oknie właściwości, wpisz ciąg monitu ma być wyświetlany w pasku stanu aplikacji.  
  
     Spowoduje to utworzenie wpisu w tabeli ciągów o tym samym identyfikatorze zasobu jako polecenia menu, który został utworzony.  
  
    > [!NOTE]
    >  Monity można stosować tylko do elementów menu z **podręcznego** właściwość **True**. Może to mieć na przykład elementów menu najwyższego poziomu monitów, mają one elementy podmenu. Wiersz ma na celu wskazują, co się stanie, gdy użytkownik kliknie elementu menu.  
  
6.  Naciśnij klawisz **ENTER** ukończyć polecenia menu.  
  
     Pole nowego elementu jest zaznaczone, dzięki czemu można tworzyć dodatkowe polecenia.  
  

  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor menu](../windows/menu-editor.md)   
