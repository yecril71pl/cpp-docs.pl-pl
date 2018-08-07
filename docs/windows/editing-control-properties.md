---
title: Edytowanie właściwości kontrolki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls, editing properties
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa1283f90560390f8fc14ee13d1ab022bbeeff11
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39568865"
---
# <a name="editing-control-properties"></a>Edytowanie właściwości formantu
### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Edytowanie właściwości kontrolki lub kontrolki  
  
1.  W oknie dialogowym Wybierz formant, który chcesz zmodyfikować.  
  
    > [!NOTE]
    >  Jeśli wybierzesz wielu formantów, można edytować tylko właściwości wspólne dla wybranych kontrolek.  
  
2.  W [okno właściwości](/visualstudio/ide/reference/properties-window), zmień właściwości formantu.  
  
    > [!NOTE]
    >  Po ustawieniu **mapy bitowej** właściwości dla przycisku, przycisk radiowy lub kontrolka pola wyboru równa **True**, styl BS_BITMAP został zaimplementowany dla formantu. Aby uzyskać więcej informacji, zobacz [style przycisku](../mfc/reference/styles-used-by-mfc.md#button-styles). Na przykład kojarzenia mapę bitową z kontrolką zobacz [CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Mapy bitowe nie będą wyświetlane na Twoją kontrolą, podczas pracy w edytorze zasobów okien dialogowych.  
  
### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Aby cofnąć zmiany do właściwości kontrolki  
  
1.  Upewnij się, że kontrolka ma fokus w edytorze okien dialogowych.  
  
2.  Wybierz **Cofnij** z **Edytuj** menu (Jeśli zespół nie znajduje się na kontrolki, **Cofnij** polecenie jest niedostępne).  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Instruktaż: Lokalizowanie interfejsów Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5) i [Wskazówki: Korzystanie z zasobów for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
## <a name="requirements"></a>Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)