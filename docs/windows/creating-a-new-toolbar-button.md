---
title: Tworzenie nowego przycisku paska narzędzi | Dokumentacja firmy Microsoft
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
- Toolbar editor, creating buttons
- toolbar buttons (in Toolbar editor), button image
- toolbar buttons (in Toolbar editor), creating
- toolbar buttons (in Toolbar editor)
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d883fbb34fe45be2ad84860ea7564350346749f2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="creating-a-new-toolbar-button"></a>Tworzenie nowego przycisku paska narzędzi
### <a name="to-create-a-new-toolbar-button"></a>Aby utworzyć nowego przycisku paska narzędzi  
  
1.  W [widok zasobów](../windows/resource-view-window.md) rozwiń folder zasobów (na przykład Project1.rc).  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Rozwiń węzeł **narzędzi** i wybierz polecenie narzędzi do edycji.  
  
3.  Identyfikator należy przypisać pusty przycisk na prawym końcu paska narzędzi. Możesz to zrobić, edytując **identyfikator** właściwości w [okna właściwości](/visualstudio/ide/reference/properties-window). Na przykład możesz nadać tym samym identyfikatorze jako opcji menu przycisku paska narzędzi. W takim przypadku użyj listy rozwijanej, aby wybrać **identyfikator** opcji menu.  
  
     —lub—  
  
     Wybierz przycisk puste na prawym końcu paska narzędzi (w okienku widoku paska narzędzi) i rozpocząć rysunku. Identyfikator polecenia przycisk domyślny jest przypisywany (ID_BUTTON\<n >).  
  
 Można skopiować i wkleić obraz na pasku narzędzi jako przycisk Nowy.  
  
#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Aby dodać obraz do paska narzędzi jako przycisk  
  
1.  W [widok zasobów](../windows/resource-view-window.md), Otwórz pasek narzędzi, kliknij go dwukrotnie.  
  
2.  Następnie otwórz folder obraz, który chcesz dodać do paska narzędzi.  
  
    > [!NOTE]
    >  Jeśli obraz jest otwarty w programie Visual Studio, zostanie otwarty w edytorze obrazów. Można również otworzyć obrazu w innych programów graficznych.  
  
3.  Z **Edytuj** menu, wybierz **kopiowania**.  
  
4.  Przejdź do paska narzędzi, klikając jej kartę w górnej części okna źródła.  
  
5.  Z **Edytuj** menu, wybierz **Wklej**.  
  
     Obraz pojawi się na pasku narzędzi przycisk Nowy.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Wymagania  
 MFC i ATL  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości przycisku paska narzędzi](../windows/toolbar-button-properties.md)   
 [Tworzenie, przenoszenie i edytowanie przycisków paska narzędzi](../windows/creating-moving-and-editing-toolbar-buttons.md)   
 [Edytor paska narzędzi](../windows/toolbar-editor.md)

