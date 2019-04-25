---
title: Hostowanie kontrolki użytkownika formularza systemu Windows w oknie dialogowym MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 56cf00da71fe6c47e39de2a8fc06df572a301a61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222991"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hostowanie kontrolki użytkownika formularza systemu Windows w oknie dialogowym MFC

Obsługuje formant programu Windows Forms jako specjalny rodzaj kontrolki ActiveX MFC i komunikuje się za pomocą kontrolki przy użyciu interfejsów ActiveX i właściwości i metod <xref:System.Windows.Forms.Control> klasy. Zalecamy użycie systemu .NET Framework, właściwości i metod do działania na formancie.

Dla przykładowej aplikacji, który pokazuje formularze Windows używane z biblioteką MFC, zobacz [MFC i integracji formularzy Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

> [!NOTE]
>  W bieżącej wersji `CDialogBar` obiektu nie może obsługiwać kontrolek formularzy Windows Forms.

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: tworzenie kontrolki użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Instrukcje: Czy danych DDX/DDV powiązania z Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Instrukcje: wychwytywanie zdarzeń interfejsu Windows Forms z klas natywnych języka C++](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Tematy pomocy

[Klasa CWinFormsControl](../mfc/reference/cwinformscontrol-class.md) &#124; [klasa CDialog](../mfc/reference/cdialog-class.md) &#124; [klasa CWnd](../mfc/reference/cwnd-class.md)&#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Zobacz także

[Używanie kontrolki użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Różnice w programie Windows Forms/MFC programowania](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hostowanie kontrolki użytkownika interfejsu Windows Forms jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hostowanie kontrolki użytkownika formularza systemu Windows jako okna dialogowego MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
