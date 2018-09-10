---
title: Tworzenie nowego przycisku paska narzędzi (C++) | Dokumentacja firmy Microsoft
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
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0f1ed792407160c1d025dabb3b8cc01a2ebc7330
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314329"
---
# <a name="creating-a-new-toolbar-button-c"></a>Tworzenie nowego przycisku paska narzędzi (C++)

### <a name="to-create-a-new-toolbar-button"></a>Aby utworzyć nowego przycisku paska narzędzi

1. W [widok zasobów](../windows/resource-view-window.md) rozwiń folder zasobów (na przykład Project1.rc).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. Rozwiń **narzędzi** folder i wybierz pasek narzędzi do edycji.

3. Identyfikator należy przypisać pusty przycisk po prawej stronie paska narzędzi. Możesz to zrobić, edytując **identyfikator** właściwość [okno właściwości](/visualstudio/ide/reference/properties-window). Na przykład można podać tej samej opcji menu przycisku paska narzędzi. W tym przypadku użyj pola listy rozwijanej, aby wybrać **identyfikator** opcji menu.

   —lub—

   Wybierz pusty przycisk po prawej stronie paska narzędzi (w **pasek narzędzi widoku** okienko) i rozpocząć rysowania. Domyślny przycisk polecenia identyfikator jest przypisywany (ID_BUTTON\<n >).

Można również skopiuj i Wklej obraz jest jako nowego przycisku paska narzędzi.

### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Aby dodać obraz do paska narzędzi, jak przycisk

1. W [widok zasobów](../windows/resource-view-window.md), Otwórz pasek narzędzi, klikając go dwukrotnie.

2. Następnie otwórz obraz, który chcesz dodać do paska narzędzi.

   > [!NOTE]
   > Jeśli otworzysz go w programie Visual Studio, zostanie on otwarty w **obraz** edytora. Można również otworzyć obrazu w innych programach grafiki.

3. Z **Edytuj** menu, wybierz **kopiowania**.

4. Przejdź do paska narzędzi, klikając jej kartę w górnej części okna źródła.

5. Z **Edytuj** menu, wybierz **Wklej**.

   Obraz pojawi się na pasku narzędzi jako nowy przycisk.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

ATL i MFC

## <a name="see-also"></a>Zobacz też

[Właściwości przycisku paska narzędzi](../windows/toolbar-button-properties.md)  
[Tworzenie, przenoszenie i edytowanie przycisków paska narzędzi](../windows/creating-moving-and-editing-toolbar-buttons.md)  
[Edytor paska narzędzi](../windows/toolbar-editor.md)