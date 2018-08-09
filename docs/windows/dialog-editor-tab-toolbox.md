---
title: Karta Edytor okien dialogowych, przybornik | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls ino dialog boxes
- custom controls [Visual Studio], dialog boxes
- controls [C++], standard
- Dialog editor, creating controls
- controls [C++], adding to dialog boxes
ms.assetid: 253885c2-dcb9-4d8e-ac9b-805ea31cbf5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 40e0a13f9379200ee01e0279f9d069f1d58f3a60
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649425"
---
# <a name="dialog-editor-tab-toolbox"></a>Karta Edytor okien dialogowych, Przybornik
**Edytor okien dialogowych** karta jest wyświetlana w [okno przybornika](/visualstudio/ide/reference/toolbox) podczas pracy **okna dialogowego** edytora. Aby dodać formanty do Twojego nowego okna dialogowego, przeciągnij formanty z **przybornika** do okna dialogowego, który tworzysz (Aby uzyskać więcej informacji, zobacz [Dodawanie formantu do okna dialogowego](adding-a-control-to-a-dialog-box.md)). Możesz przenosić kontrolki lub zmieniać ich rozmiar i kształt.  
  
 Formanty standardowe dostępne w **przybornika** są:  
  
-   [Kontrolka przycisku](../mfc/reference/cbutton-class.md)  
  
-   [Kontrolka pola wyboru](../mfc/reference/styles-used-by-mfc.md#button-styles)  
  
-   [Kontrolka pola kombi](../mfc/reference/ccombobox-class.md)  
  
-   [Edytuj kontrolkę](../mfc/reference/cedit-class.md)  
  
-   Pole grupy  
  
-   [Kontrolka pola listy](../mfc/reference/clistbox-class.md)  
  
-   [Kontrolka przycisku radiowego](../mfc/reference/styles-used-by-mfc.md#button-styles)  
  
-   [Kontrolka tekstu statycznego](../mfc/reference/cstatic-class.md)  
  
-   [Formant obrazu](../mfc/reference/cpictureholder-class.md)  
  
-   [Kontrolka 2.0 edycji wzbogaconej](../mfc/using-cricheditctrl.md)  
  
-   [Pasek przewijania](../mfc/reference/cscrollbar-class.md)  
  
 [Wspólnych formantów Windows](../mfc/controls-mfc.md) dostępne w **przybornika** zapewniają większą funkcjonalność w aplikacji. Obejmują one:  
  
-   [Kontrolka suwaka](../mfc/slider-control-styles.md)  
  
-   [Kontrolki pokrętła](../mfc/using-cspinbuttonctrl.md)  
  
-   [Kontrolki postępu](../mfc/styles-for-the-progress-control.md)  
  
-   [Formantu klawisza dostępu](../mfc/using-a-hot-key-control.md)  
  
-   [Kontrolka listy](../mfc/list-control-and-list-view.md)  
  
-   [Kontrolka drzewa](../mfc/tree-control-styles.md)  
  
-   [Kontrolki karty](../mfc/tab-controls-and-property-sheets.md)  
  
-   [Kontrolki animacji](../mfc/using-an-animation-control.md)  
  
-   [Kontrolka czasu selektora daty](../mfc/creating-the-date-and-time-picker-control.md)  
  
-   [Kontrolowanie kalendarza miesięcznego](../mfc/month-calendar-control-examples.md)  
  
-   [Formant adresu IP](../mfc/reference/cipaddressctrl-class.md)  
  
-   [Rozszerzone formant pola kombi](../mfc/creating-an-extended-combo-box-control.md)  
  
-   [Kontrolka niestandardowa](custom-controls-in-the-dialog-editor.md)  
  
 Można dodać niestandardowe formanty do okna dialogowego wybierając **kontrolki niestandardowej** ikonę **przybornika** i przeciągając je do swojej okna dialogowego. Aby dodać **Syslink** , Dodaj formant niestandardowy, a następnie zmienić formant **klasy** właściwości **Syslink**. Spowoduje to właściwości, aby odświeżyć i Pokaż **Syslink** właściwości formantu. Aby uzyskać informacji na temat klasy otoki MFC, zobacz [CLinkCtrl](../mfc/reference/clinkctrl-class.md).  
  
 Możesz również [Dodawanie kontrolek ActiveX do dialogowym](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
 Można również dostosować **przybornika** okna do użytku łatwiejsze. Aby uzyskać więcej informacji, zobacz [korzystanie z przybornika](/visualstudio/ide/using-the-toolbox).  

 Aby uzyskać więcej informacji na temat korzystania z **RichEdit 1.0** kontrolką MFC, zobacz [używanie formantu RichEdit 1.0 z MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty](../mfc/controls-mfc.md)   
 [Klasy formantów](../mfc/control-classes.md)   
 [Klasy okien dialogowych](../mfc/dialog-box-classes.md)   
 [Style paska przewijania](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)   
 [Przykłady formantów edycji wzbogaconej](../mfc/rich-edit-control-examples.md)   
 [Dodawanie obsługi zdarzeń dla formantów okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [Kontrolki okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md)