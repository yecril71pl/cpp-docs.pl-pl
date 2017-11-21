---
title: Tworzenie Menu | Dokumentacja firmy Microsoft
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
- mnemonics, associating menu items
- menus, associating commands with mnemonic keys
- menus, creating
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 953de61b199acda1b6cf4f9e0d06b1bd1875ab1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-menu"></a>Tworzenie menu
> [!NOTE]
>  Okno zasobu nie jest dostępna w wersji Express.  
  
### <a name="to-create-a-standard-menu"></a>Aby utworzyć standardowe menu  
  
1.  Z **widoku** menu, kliknij polecenie **widok zasobów** , a następnie kliknij prawym przyciskiem myszy **Menu** nagłówek i wybierz polecenie **dodawania zasobów**. Wybierz **Menu**.  
  
2.  Wybierz **nowy element** polu (prostokąt zawiera "Typ w tym miejscu") na pasku menu.  
  
     ![Pole nowego elementu w edytorze menu](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")  
Pole nowego elementu  
  
3.  Wpisz nazwę nowego menu programu, na przykład "Plik".  
  
     Możesz wpisać tekst, który jest dostępny w **Menu** edytora i **podpis** polu [okno właściwości](/visualstudio/ide/reference/properties-window). Można edytować właściwości dla Twojego nowego menu w dowolnej lokalizacji.  
  
     Po otrzymał Twoje nowe menu nazwę na pasku menu, przesuwa okno nowy element w prawo (aby umożliwić innym menu dodawania), a inny nowy element otworzy się okno poniżej menu programu pierwszego polecenia menu można dodać do niego.  
  
     ![Rozwinięte pole nowego elementu](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")  
Pole nowego elementu z fokusem przesunięte po wpisaniu nazwy Menu  
  
    > [!NOTE]
    >  Aby utworzyć jeden element menu na pasku menu, ustaw właściwość podręcznego na wartość False.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor menu](../windows/menu-editor.md)