---
title: Grupowanie przycisków radiowych w oknie dialogowym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.grouping
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls, grouping radio buttons
- grouping controls
- radio buttons, grouping on dialog boxes
ms.assetid: 3cc43f9e-56c8-4faa-9930-ce81733c69de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aee3245a65ccdccc32b40c313eecdd45cb3ea8bf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879331"
---
# <a name="grouping-radio-buttons-on-a-dialog-box"></a>Grupowanie przycisków radiowych w oknie dialogowym
Po dodaniu przycisków radiowych do okna dialogowego potraktować je jako grupę, przez ustawienie właściwości grupy w oknie dialogowym Właściwości przycisku pierwszej w grupie. Identyfikator formantu dla tego przycisku radiowego pojawia się w [Kreator dodawania zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md), co umożliwia dodawanie zmiennej członkowskiej w grupie przycisków radiowych.  
  
 Może mieć więcej niż jedna grupa przycisków radiowych w oknie dialogowym, a każda grupa powinny zostać dodane przy użyciu poniższej procedury.  
  
### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Aby dodać grupy przycisków radiowych do okna dialogowego  
  
1.  Wybierz kontrolkę przycisku radiowego w [okno przybornika](/visualstudio/ide/reference/toolbox) i kliknij pozycję w oknie dialogowym, na którym chcesz umieścić kontrolkę.  
  
2.  Powtórz krok 1, aby dodać dowolną liczbę przycisków radiowych, zgodnie z potrzebami. Upewnij się, że w grupie przycisków radiowych są kolejne w kolejności tabulacji (Aby uzyskać więcej informacji, zobacz [zmiana kolejności formanty karty](../windows/changing-the-tab-order-of-controls.md)).  
  
3.  W [okna właściwości](/visualstudio/ide/reference/properties-window)ustaw **grupy** właściwość *pierwszy* przycisku radiowego w kolejności tabulacji na **True**.  
  
     Zmiana **grupy** właściwości **True** dodaje ws_group — styl do przycisku wpisu w obiekcie okna dialogowego skryptu zasobu i zapewnia, że użytkownik można wybrać tylko jeden przycisk radiowy naraz w przycisku grupy (po kliknięciu przycisku radiowego co inne osoby w grupie zostaną wyczyszczone).  
  
    > [!NOTE]
    >  Tylko pierwszy przycisk radiowy w grupie powinny mieć **grupy** ustawioną właściwość **True**. Jeśli masz dodatkowe funkcje kontroli, które nie są częścią grupy przycisk Ustaw **grupy** właściwości pierwszego formantu *jest spoza grupy* do **True** również. Pierwszą kontrolkę spoza grupy można szybko określić, naciskając klawisze CTRL + D, aby wyświetlić kolejność tabulacji.  
  
### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Aby dodać zmiennej członka w grupie przycisków radiowych  
  
1.  Kliknij prawym przyciskiem myszy pierwszy kontrolkę przycisku radiowego w kolejności tabulacji (formantu dominującego i z **grupy** właściwość, ustaw wartość True).  
  
2.  Wybierz **Dodaj zmienną** z menu skrótów.  
  
3.  W [Kreator dodawania zmiennej członkowskiej](../ide/add-member-variable-wizard.md), wybierz pozycję **zmienna sterująca** pole wyboru, a następnie wybierz **wartość** przycisk radiowy.  
  
4.  W **nazwa zmiennej** wpisz nazwę nowej zmiennej elementu członkowskiego.  
  
5.  W **typ zmiennej** pola listy, wybierz opcję **int** lub typ **int**.  
  
6.  Można również zmodyfikować swój kod, aby określić przycisku radiowego, która powinna zostać wyświetlona wybrane. Na przykład m_radioBox1 = 0; wybiera pierwszy przycisk radiowy w grupie.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Rozmieszczenie formantów w oknach dialogowych](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)   
 [Kontrolki](../mfc/controls-mfc.md)

