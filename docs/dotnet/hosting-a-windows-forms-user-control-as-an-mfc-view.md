---
title: Hostowanie formantu użytkownika interfejsu Windows Forms jako widoku MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
ms.openlocfilehash: df193bae541aecf8416056c2b169f0079539d173
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450858"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>Hostowanie formantu użytkownika interfejsu Windows Forms jako widoku MFC

MFC używa klas CWinFormsView do hostowania kontrolki użytkownika Windows Forms w widoku MFC. Widoki formularzy Windows w MFC są formantów ActiveX. Formant użytkownika znajduje się jako element podrzędny elementu natywnego widoku i zajmuje całego obszaru klienta natywnego widoku.

Wynik końcowy przypomina model wykorzystywany przez [klasa CFormView](../mfc/reference/cformview-class.md). Dzięki temu można korzystać z projektanta Windows Forms i środowiska uruchomieniowego, które pozwala tworzyć rozbudowane widoki oparte na formularzach.

Ponieważ widoki formularzy Windows w MFC formantów ActiveX, nie mają takie same `hwnd` jako widoki MFC. Ponadto nie mogą być przekazywane jako wskaźnik do [CView](../mfc/reference/cview-class.md) widoku. Ogólnie rzecz biorąc należy użyć metod .NET Framework do pracy z widokami Windows Forms i zmniejszenia zakresu Win32.

Dla przykładowej aplikacji, który pokazuje formularze Windows używane z biblioteką MFC, zobacz [MFC i integracji formularzy Windows](https://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: tworzenie kontrolki użytkownika i hostowanie widoku MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)

[Instrukcje: dodawanie routingu poleceń do formantu interfejsu Windows Forms](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

[Instrukcje: wywoływanie właściwości i metod kontrolki interfejsu Windows Forms](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)

## <a name="see-also"></a>Zobacz także

[Używanie kontrolki użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Instrukcje: Formanty złożone autora](/dotnet/framework/winforms/controls/how-to-author-composite-controls)
