---
title: Hosting systemu Windows formantu użytkownika jako widoku MFC formularzy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bf9e54b3e2808a232bc13052c885a341cb51297f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137630"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>Hostowanie kontrolki użytkownika interfejsu Windows Forms jako widoku MFC
MFC używa klasy CWinFormsView do hostowania kontrolki użytkownika formularzy systemu Windows w widoku MFC. Widoki formularzy systemu Windows MFC są formantów ActiveX. Kontrola użytkownika jest obsługiwany jako element podrzędny widoku macierzystego i zajmuje całego obszaru klienta natywnego widoku.  
  
 W rezultacie podobny modelu używanego przez [CFormView klasy](../mfc/reference/cformview-class.md). Dzięki temu można korzystać z projektanta formularzy systemu Windows i środowiska uruchomieniowego do tworzenia zaawansowanych widoków opartych na formularzach.  
  
 Ponieważ widoki formularzy systemu Windows MFC formantów ActiveX, nie mają takie same `hwnd` jako widoki MFC. Również nie mogą być przekazywane jako wskaźnik do [CView](../mfc/reference/cview-class.md) widoku. Ogólnie rzecz biorąc należy użyć metod .NET Framework do pracy z widokami formularzy systemu Windows i zmniejszenia zakresu Win32.  
  
 Dla przykładowej aplikacji, która zawiera formularze systemu Windows używana z MFC, zobacz [MFC i integracja z formularzy systemu Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: tworzenie kontrolki użytkownika i hostowanie widoku MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)  
  
 [Instrukcje: dodawanie routingu poleceń do formantu interfejsu Windows Forms](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)  
  
 [Instrukcje: wywoływanie właściwości i metod kontrolki interfejsu Windows Forms](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie formantu użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Instrukcje: tworzenie kontrolek złożonych](/dotnet/framework/winforms/controls/how-to-author-composite-controls)