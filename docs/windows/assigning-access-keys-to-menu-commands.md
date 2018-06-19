---
title: Przypisywanie klawiszy skrótów do poleceń Menu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 44a21e5930d0d8f2fcaad79cc5cef5bc984ad8b5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857902"
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