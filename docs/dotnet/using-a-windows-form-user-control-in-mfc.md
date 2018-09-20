---
title: Kontrolka użytkownika przy użyciu Windows formularz w MFC | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 4fef169cb0e2386c1629064ad7ea8a1a70a5c517
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382079"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Używanie formantu użytkownika formularza systemu Windows w MFC

Przy użyciu klas pomocy technicznej formularzy Windows w MFC, może obsługiwać kontrolek formularzy Windows Forms w aplikacjach MFC jako formant ActiveX w obrębie okna dialogowe MFC lub widoków. Ponadto formularzy Windows forms może być obsługiwany jako okna dialogowe MFC.

W poniższych sekcjach opisano sposób:

- Hostowanie kontrolki formularzy Windows w oknie dialogowym MFC.

- Hostowanie kontrolki użytkownika Windows Forms jako widoku MFC.

- Hosta formularzy Windows Forms jako okna dialogowego MFC.

> [!NOTE]
> Integracja biblioteki MFC, formularzy Windows działa tylko w projektach, które łączą się dynamicznie z MFC (projekty, w którym `_AFXDLL` jest zdefiniowana).

> [!NOTE]
> W przypadku tworzenia aplikacji za pomocą prywatnej kopii (zmodyfikowany) interfejsy formularzy Windows w MFC DLL (mfcmifc80.dll), nie będzie można zainstalować w GAC, chyba że Zastąp klucz firmy Microsoft przy użyciu własnego klucza dostawcy. Aby uzyskać więcej informacji na temat podpisywanie zestawu, zobacz [programowanie za pomocą zestawów](/dotnet/framework/app-domains/programming-with-assemblies) i [zestawy o silnej nazwach (podpisywanie zestawów) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Jeśli Twoja aplikacja MFC używa Windows Forms, musisz ponownie rozdzielić mfcmifc80.dll z aplikacją. Aby uzyskać więcej informacji, zobacz [redystrybuowanie biblioteki MFC](../ide/redistributing-the-mfc-library.md).

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

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)<br/>
[Widoki formularzy](../mfc/form-views-mfc.md)
