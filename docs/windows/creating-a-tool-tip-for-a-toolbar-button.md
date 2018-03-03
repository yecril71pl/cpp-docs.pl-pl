---
title: "Tworzenie etykietki narzędzia dla przycisku Toolbar | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- tool tips [C++], adding to toolbar buttons
- "\nin tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor, creating tool tips
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b5bb25a14d68c01c25d9242df89c1183511ca83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-tool-tip-for-a-toolbar-button"></a>Tworzenie etykietki narzędzia dla przycisku paska narzędzi
### <a name="to-create-a-tool-tip"></a>Aby utworzyć etykietki narzędzia  
  
1.  Wybierz przycisk paska narzędzi.  
  
2.  W [okna właściwości](/visualstudio/ide/reference/properties-window)w **monitu** właściwości pola Dodaj opis przycisku po komunikat; na pasku stanu, Dodaj \n i nazwa Porada narzędzia.  
  
 Typowym przykładem etykietka narzędzia, która jest przycisku Drukuj na WordPad:  
  
 1. Otwórz program WordPad.  
  
 2. Umieść wskaźnik myszy nad **drukowania** przycisku paska narzędzi.  
  
 3. Należy zauważyć, że wyraz "Drukuj" teraz jest przestawne w obszarze wskaźnik myszy.  
  
 4. Szukaj na pasku stanu (u dołu okna WordPad) - Zwróć uwagę, że teraz widoczny jest tekst "Drukuje aktywny dokument".  
  
 W kroku 3 "Print" jest "Nazwa Porada narzędzia" i "Drukuje aktywny dokument' z kroku 4 jest"Opis przycisk paska stanu."  
  
 Jeśli chcesz przy użyciu tego efektu **narzędzi** edytor, należy ustawić **monitu** właściwości **Drukuje aktywny document\nPrint**.  
  
> [!NOTE]
>  Można edytować tekst monitu przy użyciu [okna właściwości](/visualstudio/ide/reference/properties-window).  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 MFC i ATL  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie, przenoszenie i edytowanie przycisków paska narzędzi](../windows/creating-moving-and-editing-toolbar-buttons.md)   
 [Edytor paska narzędzi](../windows/toolbar-editor.md)

