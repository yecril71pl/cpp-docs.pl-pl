---
title: Formant użytkownika przy użyciu systemu Windows formularza w MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/08/2018
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8ceb424d6c5061ac5ccafc62d8748be4de3ab3d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33174316"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Używanie formantu użytkownika formularza systemu Windows w MFC

Przy użyciu klasy obsługi formularzy systemu Windows MFC, może obsługiwać formanty formularzy systemu Windows w aplikacjach MFC jako formant ActiveX w obrębie okna dialogowe MFC lub widoków. Ponadto formularzy Windows forms może być obsługiwany jako okna dialogowe MFC.

W poniższych sekcjach opisano sposób:

- Hostowanie kontrolki formularza systemu Windows, w oknie dialogowym MFC.

- Hostowanie formantu użytkownika formularzy systemu Windows jako widoku MFC.

- Host formularza formularzy systemu Windows jako okna dialogowego MFC.

> [!NOTE]
> Formularze systemu Windows MFC integracji działa tylko w projektach połączone dynamicznie z MFC (projekty, w którym `_AFXDLL` jest zdefiniowana).

> [!NOTE]
> Podczas kompilowania aplikacji za pomocą prywatnego kopiowania (zmodyfikowany) interfejsów formularzy systemu Windows MFC DLL (mfcmifc80.dll), nie będzie można instalować w pamięci GAC, jeśli nie można zastąpić klucz Microsoft klucz dostawcy. Aby uzyskać więcej informacji na podpisywanie zestawu, zobacz [programowanie za pomocą zestawów](/dotnet/framework/app-domains/programming-with-assemblies) i [silnych nazwach (podpisywanie zestawów) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Dla przykładowych aplikacji przy użyciu formularzy systemu Windows, temacie [BirthdayPicker próbki: przedstawiono zasoby platformy .NET w formularzach systemu Windows](http://msdn.microsoft.com/ac932aed-5502-4667-be29-709bca435317), [próbki Kalkulator: Kalkulator Pocket formularzy systemu Windows](http://msdn.microsoft.com/2283b516-3b7e-45f2-80c4-fdcfb366ce25)i [ Przykład bazgrołów: MDI rysunku aplikacji](http://msdn.microsoft.com/f025da3e-659b-4222-b991-554a1b8b2358).

Dla przykładowej aplikacji, która zawiera formularze systemu Windows używana z MFC, zobacz [MFC i integracja z formularzy systemu Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

Aplikacja MFC używa formularzy systemu Windows, należy ponownie rozesłać mfcmifc80.dll z aplikacją. Aby uzyskać więcej informacji, zobacz [redystrybuowanie biblioteki MFC](../ide/redistributing-the-mfc-library.md).

## <a name="in-this-section"></a>W tej sekcji

[Hostowanie kontrolki użytkownika formularza systemu Windows w oknie dialogowym MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)

[Hostowanie kontrolki użytkownika interfejsu Windows Forms jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

[Hostowanie kontrolki użytkownika formularza systemu Windows jako okna dialogowego MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)

## <a name="reference"></a>Tematy pomocy

[Klasa CWinFormsControl](../mfc/reference/cwinformscontrol-class.md)

[Klasa CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md)

[Klasa CWinFormsView](../mfc/reference/cwinformsview-class.md)

[Klasa ICommandSource](../mfc/reference/icommandsource-interface.md)

[Klasa ICommandTarget](../mfc/reference/icommandtarget-interface.md)

[Klasa ICommandUI](../mfc/reference/icommandui-interface.md)

[Interfejs IView](../mfc/reference/iview-interface.md)

[CommandHandler](../atl/commandhandler.md)

[Ddx_managedcontrol —](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)

[Uicheckstate —](../mfc/reference/uicheckstate-enumeration.md)

## <a name="related-sections"></a>Sekcje pokrewne

[Windows Forms](/dotnet/framework/winforms/index)

[Kontrolki formularzy Windows Forms](/dotnet/framework/winforms/controls/index)

## <a name="see-also"></a>Zobacz także

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)  
[Widoki formularzy](../mfc/form-views-mfc.md)  
