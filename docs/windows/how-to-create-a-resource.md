---
title: 'Porady: tworzenie zasobu | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [Visual Studio], creating
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 46e03602e53c79ff6c384ad9cc613849cb329423
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-create-a-resource"></a>Porady: tworzenie zasobu
> [!NOTE]
>  Widok zasobów nie jest obsługiwany w wersjach Express.  
  
### <a name="to-create-a-new-resource-in-resource-view"></a>Aby utworzyć nowy zasób w widokach  
  
1.  Fokus jest ustawiony w pliku .rc w [widok zasobów](../windows/resource-view-window.md), kliknij przycisk **Edytuj** menu i wybierz polecenie **dodawania zasobów** (lub kliknij prawym przyciskiem myszy plik .rc w widoku zasobów i wybierz polecenie  **Dodaj zasób** z menu skrótów).  
  
     **Uwaga** Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W [okno dialogowe dodawania zasobów](../windows/add-resource-dialog-box.md), wybierz typ zasobów, które chcesz dodać do projektu.  
  
### <a name="to-create-a-new-resource-in-solution-explorer"></a>Aby utworzyć nowy zasób w Eksploratorze rozwiązań  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder projektu i wybierz **Dodaj**, następnie kliknij przycisk **dodawania zasobów** menu skrótów.  
  
     Jeśli plik .rc nie jest już ma w projekcie, będzie utworzyć ten krok. Można następnie powtórz ten krok, aby dodać nowy plik .rc określonych typów zasobów.  
  
2.  W [okno dialogowe dodawania zasobów](../windows/add-resource-dialog-box.md), wybierz typ zasobów, które chcesz dodać do projektu.  
  
### <a name="to-create-a-new-resource-in-class-view"></a>Aby utworzyć nowy zasób w widoku klas  
  
1.  W [widoku klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), kliknij prawym przyciskiem myszy klasy i wybierz **Dodaj**, następnie kliknij przycisk **dodawania zasobów** z menu skrótów.  
  
2.  W [okno dialogowe dodawania zasobów](../windows/add-resource-dialog-box.md), wybierz typ zasobów, które chcesz dodać do projektu.  
  
### <a name="to-create-a-new-resource-from-the-project-menu"></a>Aby utworzyć nowy zasób z menu projektu  
  
1.  Z **projektu** menu, wybierz **dodawania zasobów**.  
  
 Podczas tworzenia nowego zasobu, Visual C++ przypisuje do niego, na przykład IDD_Dialog1 unikatową nazwę. Ten identyfikator zasobu można dostosować, edytując właściwości dla zasobu w edytorze zasobów lub w [okna właściwości](/visualstudio/ide/reference/properties-window).  
  
 Zasób zostanie utworzony nowy zasób domyślne (zasób, który nie jest oparty na szablonie) lub jako zasób deseniem po [szablonu](../windows/how-to-use-resource-templates.md).  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.*  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)   
 [Okno dialogowe dodawania zasobów](../windows/add-resource-dialog-box.md)