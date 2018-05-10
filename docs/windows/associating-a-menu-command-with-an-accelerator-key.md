---
title: Kojarzenie polecenia Menu z klawiszem skrótu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts, menu association
- commands, associating menu commands with accelerator keys
- menu commands, associating with keyboard shortcuts
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4f1aa4b80aec2e7c16485c08d2505695b21f4d5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="associating-a-menu-command-with-an-accelerator-key"></a>Kojarzenie polecenia menu z klawiszem skrótu
Są często razy ma polecenia menu oraz kombinację klawiszy, aby wystawiać tego samego polecenia programu. Aby to zrobić, aby przypisać ten sam identyfikator zasobu do polecenia menu i wpis w tabeli akceleratora aplikacji za pomocą edytora Menu. Następnie Edytuj [podpis](../windows/menu-command-properties.md) polecenia menu, aby wyświetlić nazwę klawisz skrótu.  
  
### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Aby skojarzyć polecenia menu z klawiszem skrótu  
  
1.  W **Menu** edytora, wybierz polecenie menu.  
  
2.  W [okna właściwości](/visualstudio/ide/reference/properties-window), Dodaj nazwę klawisz skrótu do **podpis** właściwości:  
  
    -   Następujące podpis menu wpisz sekwencji unikowej tabulatora (\t) tak, aby wszystkie klawisze skrótów menu pozostaną wyrównane.  
  
    -   Wpisz nazwę klawisz modyfikujący (**CTRL**, **ALT**, lub **SHIFT**) i znak plus (**+**) i nazwę, list, lub symbol dodatkowego klucza.  
  
         Na przykład, aby przypisać **CTRL + O** do **Otwórz** na **pliku** menu, zmodyfikuj polecenia menu **podpis** tak, aby wyglądało to:  
  
        ```  
        &Open...\tCtrl+O   
        ```  
  
         Polecenia menu w edytorze Menu jest aktualizowany w celu odzwierciedlenia nowych podpis, w trakcie pisania.  
  
3.  [Utworzenia wpisu tabeli akceleratora](../windows/adding-an-entry-to-an-accelerator-table.md) w **akceleratora** edytora i przypisz go w taki sam identyfikator jak polecenie menu. Użyj kombinacji klawiszy uważasz, że będą łatwe do zapamiętania.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie poleceń do Menu](../windows/adding-commands-to-a-menu.md)   
 [Edytor menu](../windows/menu-editor.md)