---
title: Hostowanie kontrolki użytkownika formularza systemu Windows w oknie dialogowym MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 1a688870f4700e8e3b935245f2c9243f8d5aa823
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73704090"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hostowanie kontrolki użytkownika formularza systemu Windows w oknie dialogowym MFC

MFC obsługuje kontrolkę Windows Forms jako specjalny rodzaj kontrolki ActiveX i komunikuje się z kontrolką przy użyciu interfejsów ActiveX oraz właściwości i metod klasy <xref:System.Windows.Forms.Control>. Zalecamy używanie .NET Framework właściwości i metod do działania na formancie.

Aby uzyskać przykładową aplikację, która zawiera Windows Forms używane z MFC, zobacz [integrację MFC i Windows Forms](https://www.microsoft.com/en-us/download/details.aspx?id=2113).

> [!NOTE]
>  W bieżącej wersji obiekt `CDialogBar` nie może hostować formantów Windows Forms.

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: tworzenie kontrolki użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Instrukcje: wykonywanie powiązania danych DDX/DDV za pomocą Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Instrukcje: wychwytywanie zdarzeń interfejsu Windows Forms z klas natywnych języka C++](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Tematy pomocy

&#124; Klasa [CWinFormsControl](../mfc/reference/cwinformscontrol-class.md) klasy [CDialog](../mfc/reference/cdialog-class.md) &#124; klasy [CWnd](../mfc/reference/cwnd-class.md) &#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Zobacz także

[Używanie kontrolki użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Różnice w programowaniu Windows Forms/MFC](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hostowanie kontrolki użytkownika interfejsu Windows Forms jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hostowanie kontrolki użytkownika formularza systemu Windows jako okna dialogowego MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
