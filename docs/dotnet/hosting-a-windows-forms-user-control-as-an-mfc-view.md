---
title: Hostowanie formantu użytkownika interfejsu Windows Forms jako widoku MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
ms.openlocfilehash: 9eb157ecbc738e1d7a1c3022d5f156fb590e8f04
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73704125"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>Hostowanie formantu użytkownika interfejsu Windows Forms jako widoku MFC

MFC używa klasy CWinFormsView do hostowania kontrolki użytkownika Windows Forms w widoku MFC. Widoki Windows Forms MFC są kontrolkami ActiveX. Kontrolka użytkownika jest hostowana jako element podrzędny widoku natywnego i zajmuje cały obszar klienta widoku natywnego.

Wynik końcowy przypomina model używany przez [klasę CFormView](../mfc/reference/cformview-class.md). Dzięki temu można korzystać z projektanta Windows Forms i środowiska uruchomieniowego w celu tworzenia zaawansowanych widoków opartych na formularzach.

Ponieważ widoki Windows Forms MFC są kontrolkami ActiveX, nie mają tych samych `hwnd` jako widoków MFC. Nie można ich również przekazywać jako wskaźnika do widoku [CView](../mfc/reference/cview-class.md) . Ogólnie rzecz biorąc, użyj .NET Framework metod do pracy z widokami Windows Forms i zależą od systemu Win32.

Aby uzyskać przykładową aplikację, która zawiera Windows Forms używane z MFC, zobacz [integrację MFC i Windows Forms](https://www.microsoft.com/en-us/download/details.aspx?id=2113).

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: tworzenie kontrolki użytkownika i hostowanie widoku MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)

[Instrukcje: dodawanie routingu poleceń do formantu interfejsu Windows Forms](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

[Instrukcje: wywoływanie właściwości i metod kontrolki interfejsu Windows Forms](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)

## <a name="see-also"></a>Zobacz także

[Używanie kontrolki użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Instrukcje: tworzenie kontrolek złożonych](/dotnet/framework/winforms/controls/how-to-author-composite-controls)
