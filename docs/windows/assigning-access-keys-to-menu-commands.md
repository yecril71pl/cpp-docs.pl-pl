---
title: "Przypisywanie klawiszy skrótów do poleceń Menu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- access keys [C++], checking
- menus, shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics, adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics, uniqueness checking
- Check Mnemonics command
ms.assetid: fbcf1a00-af6a-4171-805a-0ac01d4e8b0d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ccf64739d0a54b5a96551b3a8145dc3c3f8378c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="assigning-access-keys-to-menu-commands"></a>Przypisywanie klawiszy skrótów do poleceń menu
Klucz dostępu (symbol, który umożliwia użytkownikowi wybranie w menu za pomocą klawiatury) można przypisać do menu i poleceń menu.  
  
### <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>Aby przypisać klawisza dostępu (skrót) do polecenia menu  
  
1.  Wpisz znak (**&**) przed litery w nazwie menu lub polecenia, aby określić tę literę jako odpowiedniego klucza dostępu. Na przykład "& plik" Ustawia klawisze ALT + F, jako klawisz skrótu menu Plik w aplikacji napisanych systemu Microsoft Windows.  
  
     Element menu będzie udostępniać widoczne oznaką jedną z liter ma przypisane do niej klawisza skrótu. Handlowe "i" zostaną wyświetlone następujące litery podkreślone (warunkowe w systemie operacyjnym).  
  
    > [!NOTE]
    >  Upewnij się, że wszystkie klucze dostępu w menu są unikatowe prawym przyciskiem myszy ikonę programu w menu i wybierając pozycję **Sprawdź Mnemoniki** z menu skrótów.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor menu](../windows/menu-editor.md)