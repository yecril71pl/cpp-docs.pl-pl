---
title: 'Porady: tworzenie zasobu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [Visual Studio], creating
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b44156ae26d77247a909e45061b00a6a1d892d79
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016931"
---
# <a name="how-to-create-a-resource"></a>Porady: tworzenie zasobu
> [!NOTE]
>  **Widok zasobów** nie jest obsługiwana w wersji Express.  
  
### <a name="to-create-a-new-resource-in-resource-view"></a>Aby utworzyć nowy zasób w widoku zasobu  
  
1.  Fokus jest ustawiony w pliku .rc w [widok zasobów](../windows/resource-view-window.md), kliknij przycisk **Edytuj** menu i wybierz polecenie **Dodaj zasób** (lub kliknij prawym przyciskiem myszy plik .rc w **widok zasobów** i wybierz polecenie **Dodaj zasób** z menu skrótów).  
  
     > [!NOTE] 
     > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W [Dodaj zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz typ zasobu, które chcesz dodać do projektu.  
  
### <a name="to-create-a-new-resource-in-solution-explorer"></a>Aby utworzyć nowy zasób w Eksploratorze rozwiązań  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder projektu i wybierz polecenie **Dodaj**, następnie kliknij przycisk **Dodaj zasób** w menu skrótów.  
  
     Jeśli nie masz już plik .rc w projekcie, ten krok spowoduje utworzenie jednego. Następnie możesz powtórzyć ten krok, aby dodać określonych typów zasobów do nowego pliku .rc.  
  
2.  W [Dodaj zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz typ zasobu, które chcesz dodać do projektu.  
  
### <a name="to-create-a-new-resource-in-class-view"></a>Aby utworzyć nowy zasób w widoku klas  
  
1.  W [Widok klas](http://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925), kliknij prawym przyciskiem myszy klasy i wybierz polecenie **Dodaj**, następnie kliknij przycisk **Dodaj zasób** z menu skrótów.  
  
2.  W [Dodaj zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz typ zasobu, które chcesz dodać do projektu.  
  
### <a name="to-create-a-new-resource-from-the-project-menu"></a>Aby utworzyć nowy zasób z menu projektu  
  
1.  Z **projektu** menu, wybierz **Dodaj zasób**.  
  
 Podczas tworzenia nowego zasobu, Visual C++ przypisze unikatową nazwę, na przykład `IDD_Dialog1`. Tego Identyfikatora zasobu można dostosować, edytując właściwości zasobu w edytorze skojarzonego zasobu lub w [okno właściwości](/visualstudio/ide/reference/properties-window).  
  
 Można utworzyć zasobu jako nowego zasobu domyślnego (zasób, który nie jest oparty na szablonie) lub jako zasób deseniem po [szablonu](../windows/how-to-use-resource-templates.md).  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*.

## <a name="requirements"></a>Wymagania    
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)   
 [Dodawanie zasobu, okno dialogowe](../windows/add-resource-dialog-box.md)