---
title: "Ustawianie szerokości poziomego paska przewijania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- list controls, scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars, displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars, width
ms.assetid: 51dad141-aa0b-46a3-a82c-46b80d603d94
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 97015327803a82161e8dc121e8085e63b791acdc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="setting-the-width-of-a-horizontal-scroll-bar"></a>Ustawianie szerokości poziomego paska przewijania
Po dodaniu pola listy z poziomy pasek przewijania do okna dialogowego za pomocą klasy MFC na pasku przewijania nie będzie automatycznie wyświetlany w aplikacji.  
  
### <a name="to-make-the-scroll-bar-appear"></a>Aby wyświetlanie paska przewijania  
  
1.  Ustaw maksymalną szerokość najszerszego elementu przez wywołanie metody [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) w kodzie.  
  
     Bez ustawienia tej wartości na pasku przewijania nie będą wyświetlane, nawet gdy elementy w polu listy są większe niż okno.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 Wymagania  
  
 MFC  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)   
 [Formanty](../mfc/controls-mfc.md)

