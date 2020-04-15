---
title: Hostowanie kontrolki użytkownika formularza systemu Windows w oknie dialogowym MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 2704e04df3792edfee6c39f597fcbe71b6ce51b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374483"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hostowanie kontrolki użytkownika formularza systemu Windows w oknie dialogowym MFC

MFC hostuje formant Windows Forms jako specjalny rodzaj formantu ActiveX i komunikuje się z <xref:System.Windows.Forms.Control> formantem przy użyciu interfejsów ActiveX oraz właściwości i metod klasy. Zaleca się, aby używać .NET Framework właściwości i metody do działania na formancie.

Dla przykładowej aplikacji, która pokazuje formularze systemu Windows używane z MFC, zobacz [MFC i Integracji formularzy systemu Windows](https://www.microsoft.com/download/details.aspx?id=2113).

> [!NOTE]
> W bieżącym wydaniu `CDialogBar` obiekt nie może obsługiwać formantów windows forms.

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: tworzenie kontrolki użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Jak: Do powiązania danych DDX/DDV z formularzami systemu Windows](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Instrukcje: wychwytywanie zdarzeń interfejsu Windows Forms z klas natywnych języka C++](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Dokumentacja

[CWinFormsControl Klasa](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog Klasa](../mfc/reference/cdialog-class.md) &#124; [CWnd klasa](../mfc/reference/cwnd-class.md) &#124;<xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Zobacz też

[Używanie kontrolki użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Różnice w programowaniu formularzy/MFC systemu Windows](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hostowanie kontrolki użytkownika interfejsu Windows Forms jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hostowanie kontrolki użytkownika formularza systemu Windows jako okna dialogowego MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
