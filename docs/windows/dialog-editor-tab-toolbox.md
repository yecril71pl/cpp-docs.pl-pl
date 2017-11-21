---
title: Karta Edytor okien dialogowych, przybornik | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls ino dialog boxes
- custom controls [Visual Studio], dialog boxes
- controls [C++], standard
- Dialog editor, creating controls
- controls [C++], adding to dialog boxes
ms.assetid: 253885c2-dcb9-4d8e-ac9b-805ea31cbf5e
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c897cd0a9e4685cdd3dd202b4831504b9f4c88c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="dialog-editor-tab-toolbox"></a>Karta Edytor okien dialogowych, Przybornik
Karta Edytor okien dialogowych zostanie wyświetlony w [okno przybornika](/visualstudio/ide/reference/toolbox) podczas pracy w edytorze okien dialogowych. Aby dodać kontrolki do Twoje nowe okno dialogowe, przeciągnij formanty z przybornika do okna dialogowego, które tworzysz (Aby uzyskać więcej informacji, zobacz [Dodawanie formantu do okna dialogowego](adding-a-control-to-a-dialog-box.md)). Można przenosić formantów lub zmienić ich rozmiar i kształt.  
  
 Formantów standardowych dostępnych w przyborniku są:  
  
-   [Button — formant](../mfc/reference/cbutton-class.md)  
  
-   [Kontrolka pola wyboru](../mfc/reference/styles-used-by-mfc.md#button-styles)  
  
-   [Kontrolki pola kombi](../mfc/reference/ccombobox-class.md)  
  
-   [Formant edycji](../mfc/reference/cedit-class.md)  
  
-   Pole grupy  
  
-   [Pole listy](../mfc/reference/clistbox-class.md)  
  
-   [Kontrolka przycisku radiowego](../mfc/reference/styles-used-by-mfc.md#button-styles)  
  
-   [Statyczny tekst formantu](../mfc/reference/cstatic-class.md)  
  
-   [Formant obrazu](../mfc/reference/cpictureholder-class.md)  
  
-   [Kontrolki zaawansowanej edycji 2.0](../mfc/using-cricheditctrl.md)  
  
-   [Pasek przewijania](../mfc/reference/cscrollbar-class.md)  
  
 [Formanty standardowe systemu Windows](../mfc/controls-mfc.md) dostępnych w przyborniku zapewniają większą funkcjonalność w aplikacji. Obejmują one:  
  
-   [Kontrolka suwaka](../mfc/slider-control-styles.md)  
  
-   [Pokrętła](../mfc/using-cspinbuttonctrl.md)  
  
-   [Formantu postępu](../mfc/styles-for-the-progress-control.md)  
  
-   [Formantu klawisza dostępu](../mfc/using-a-hot-key-control.md)  
  
-   [Kontrolki listy](../mfc/list-control-and-list-view.md)  
  
-   [Formant drzewa](../mfc/tree-control-styles.md)  
  
-   [Formantu karty](../mfc/tab-controls-and-property-sheets.md)  
  
-   [Formantu animacji](../mfc/using-an-animation-control.md)  
  
-   [Formant wyboru godziny daty](../mfc/creating-the-date-and-time-picker-control.md)  
  
-   [Kontrolowanie kalendarza miesięcznego](../mfc/month-calendar-control-examples.md)  
  
-   [Formant adresu IP](../mfc/reference/cipaddressctrl-class.md)  
  
-   [Rozszerzone pola kombi formantu](../mfc/creating-an-extended-combo-box-control.md)  
  
-   [Formant niestandardowy](custom-controls-in-the-dialog-editor.md)  
  
 Formanty niestandardowe można dodać do okna dialogowego, wybierając **kontrolki niestandardowej** ikonę w przyborniku i przeciągając go z okna dialogowego. Aby dodać kontrolkę Syslink, Dodaj kontrolkę niestandardową, a następnie zmień formantu **klasy** właściwości **Syslink**. Spowoduje to właściwości odświeżyć i wyświetlić właściwości formantu Syslink. Uzyskać dla klasy otoki MFC, zobacz [CLinkCtrl](../mfc/reference/clinkctrl-class.md).  
  
 Możesz także [Dodaj formanty ActiveX do okna dialogowego z](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
 Można również dostosować okno przybornika łatwiejsze do użytku. Aby uzyskać więcej informacji, zobacz [przy użyciu przybornika](/visualstudio/ide/using-the-toolbox).  

 Aby uzyskać więcej informacji o korzystaniu z formantu RichEdit 1.0 z MFC, zobacz [używanie formantu RichEdit 1.0 z MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty](../mfc/controls-mfc.md)   
 [Klasy formantów](../mfc/control-classes.md)   
 [Klasy okien dialogowych](../mfc/dialog-box-classes.md)   
 [Style paska przewijania](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)   
 [Przykłady formantów edycji wzbogaconej](../mfc/rich-edit-control-examples.md)   
 [Dodawanie programów obsługi zdarzeń dla formantów okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [Formanty okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md)

