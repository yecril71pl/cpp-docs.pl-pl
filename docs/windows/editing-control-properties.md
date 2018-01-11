---
title: "Edytowanie właściwości formantu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls, editing properties
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2baed8431501bfa5bf68313403c87a1fb9bccb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="editing-control-properties"></a>Edytowanie właściwości formantu
### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Aby edytować właściwości formantu lub formantów  
  
1.  W oknie dialogowym Wybierz formant, który chcesz zmodyfikować.  
  
    > [!NOTE]
    >  W przypadku wybrania wielu formantów wspólnych wybranych formantów właściwości można edytować.  
  
2.  W [okna właściwości](/visualstudio/ide/reference/properties-window), zmień właściwości formantu.  
  
    > [!NOTE]
    >  Podczas ustawiania **mapy bitowej** właściwość przycisk, przycisk radiowy lub równa kontrolkę pola wyboru **True**, styl bs_bitmap — jest zaimplementowany dla formantu. Aby uzyskać więcej informacji, zobacz [style przycisku](../mfc/reference/styles-used-by-mfc.md#button-styles). Na przykład kojarzenia mapę bitową z formantem zobacz [CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Mapy bitowe nie pojawi się formantu podczas pracy w edytorze okien dialogowych zasobów.  
  
### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Aby cofnąć zmiany właściwości formantu  
  
1.  Upewnij się, że kontrolka ma fokus w edytorze okien dialogowych.  
  
2.  Wybierz **Cofnij** z **Edytuj** menu (Jeśli fokus nie jest w formancie, **Cofnij** polecenie jest niedostępne).  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [wskazówki: Lokalizowanie formularzy systemu Windows](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) i [Wskazówki: Korzystanie z zasobów dla lokalizacji ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)

