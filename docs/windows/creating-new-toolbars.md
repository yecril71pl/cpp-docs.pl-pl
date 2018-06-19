---
title: Tworzenie nowych pasków narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar
dev_langs:
- C++
helpviewer_keywords:
- toolbars [C++], creating
- Toolbar editor, creating new toolbars
- Insert Resource
ms.assetid: 1b28264b-0718-4df8-9f65-979805d2efef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b61d1c530272ecaba2cbeb36c21e158bd5a6b401
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888083"
---
# <a name="creating-new-toolbars"></a>Tworzenie nowych pasków narzędzi
### <a name="to-create-a-new-toolbar"></a>Aby utworzyć nowy pasek narzędzi  
  
1.  W **zasobów** wyświetlić, kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **dodawania zasobów** z menu skrótów. (Jeśli masz istniejący pasek narzędzi w pliku .rc, użytkownik może po prostu kliknij prawym przyciskiem myszy **narzędzi** i wybierz polecenie **Wstaw narzędzi** z menu skrótów.)  
  
     **Uwaga** Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W **dodawania zasobów** okno dialogowe, wybierz opcję **narzędzi** w **typu zasobu** listy, a następnie kliknij przycisk **nowy**.  
  
     Jeśli występuje znak plus (+) obok pozycji **narzędzi** typ zasobu, oznacza to, że narzędzi szablony są dostępne. Kliknij znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie kliknij przycisk **nowy**.  
  
     \- lub -  
  
3.  [Konwertowanie istniejącej mapy bitowej na pasku narzędzi](../windows/converting-bitmaps-to-toolbars.md).  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 MFC i ATL  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor paska narzędzi](../windows/toolbar-editor.md)

