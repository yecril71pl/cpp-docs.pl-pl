---
title: "Hosting systemu Windows formant użytkownika w oknie dialogowym MFC formularza | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 311a07b81eb5450853d94332cbc742007546ee8e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hostowanie kontrolki użytkownika formularza systemu Windows w oknie dialogowym MFC
MFC obsługuje formantu formularzy systemu Windows jako specjalny rodzaj formantu ActiveX i komunikuje się za pomocą formantu przy użyciu interfejsów ActiveX i właściwości i metody <xref:System.Windows.Forms.Control> klasy. Zalecane jest użycie .NET Framework właściwości i metod do działania w formancie.  
  
 Dla przykładowej aplikacji, która zawiera formularze systemu Windows używana z MFC, zobacz [MFC i integracja z formularzy systemu Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
> [!NOTE]
>  W bieżącej wersji `CDialogBar` obiektu nie może obsługiwać formanty formularzy systemu Windows.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: Tworzenie formantu użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)  
  
 [Porady: czy powiązanie danych DDX/ddv za pomocą interfejsu Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)  
  
 [Porady: obiekt Sink zdarzenia Windows Forms z klas natywnych języka C++](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)  
  
## <a name="reference"></a>Tematy pomocy  
 [Klasa CWinFormsControl](../mfc/reference/cwinformscontrol-class.md) &#124; [Cdialog — klasa](../mfc/reference/cdialog-class.md) &#124; [Klasa CWnd](../mfc/reference/cwnd-class.md) &#124;<xref:System.Windows.Forms.Control>  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie formantu użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Różnice w programowaniu Windows Forms/MFC](../dotnet/windows-forms-mfc-programming-differences.md)   
 [Hostowanie formantu użytkownika formularzy systemu Windows jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [Hostowanie formantu użytkownika formularza systemu Windows jako okna dialogowego MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)