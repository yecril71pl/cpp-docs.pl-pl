---
title: "Formant użytkownika przy użyciu systemu Windows formularza w MFC | Dokumentacja firmy Microsoft"
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
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e836730942b3293ff8adc6aa7f8c75f4d2376cc1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Używanie formantu użytkownika formularza systemu Windows w MFC
Przy użyciu klasy obsługi formularzy systemu Windows MFC, może obsługiwać formanty formularzy systemu Windows w aplikacjach MFC jako formant ActiveX w obrębie okna dialogowe MFC lub widoków. Ponadto formularzy Windows forms może być obsługiwany jako okna dialogowe MFC.  
  
 W poniższych sekcjach opisano sposób:  
  
-   Hostowanie kontrolki formularza systemu Windows, w oknie dialogowym MFC.  
  
-   Hostowanie formantu użytkownika formularzy systemu Windows jako widoku MFC.  
  
-   Host formularza formularzy systemu Windows jako okna dialogowego MFC.  
  
> [!NOTE]
>  Formularze systemu Windows MFC integracji działa tylko w projektach połączone dynamicznie z MFC (projekty, w których zdefiniowano AFXDLL).  
  
> [!NOTE]
>  Podczas kompilowania aplikacji za pomocą prywatnego kopiowania (zmodyfikowany) interfejsów formularzy systemu Windows MFC DLL (mfcmifc80.dll), nie będzie można instalować w pamięci GAC, jeśli nie można zastąpić klucz Microsoft klucz dostawcy. Aby uzyskać więcej informacji na podpisywanie zestawu, zobacz [programowanie za pomocą zestawów](/dotnet/framework/app-domains/programming-with-assemblies) i [silnych nazwach (podpisywanie zestawów) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).  
  
 Dla przykładowych aplikacji przy użyciu formularzy systemu Windows, temacie [BirthdayPicker próbki: przedstawiono zasoby platformy .NET w formularzach systemu Windows](http://msdn.microsoft.com/en-us/ac932aed-5502-4667-be29-709bca435317), [próbki Kalkulator: Kalkulator Pocket formularzy systemu Windows](http://msdn.microsoft.com/en-us/2283b516-3b7e-45f2-80c4-fdcfb366ce25)i [ Przykład bazgrołów: MDI rysunku aplikacji](http://msdn.microsoft.com/en-us/f025da3e-659b-4222-b991-554a1b8b2358).  
  
 Dla przykładowej aplikacji, która zawiera formularze systemu Windows używana z MFC, zobacz [MFC i integracja z formularzy systemu Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
 Aplikacja MFC używa formularzy systemu Windows, należy ponownie rozesłać mfcmifc90.dll z aplikacją. Aby uzyskać więcej informacji, zobacz [redystrybuowanie biblioteki MFC](../ide/redistributing-the-mfc-library.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Hostowanie formantu użytkownika formularza systemu Windows w oknie dialogowym MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)  
  
 [Hostowanie formantu użytkownika formularzy systemu Windows jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)  
  
 [Hostowanie formantu użytkownika formularza systemu Windows jako okna dialogowego MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)  
  
## <a name="reference"></a>Tematy pomocy  
 [Klasa CWinFormsControl](../mfc/reference/cwinformscontrol-class.md)  
  
 [Klasa CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md)  
  
 [Klasa CWinFormsView](../mfc/reference/cwinformsview-class.md)  
  
 [Interfejs ICommandSource](../mfc/reference/icommandsource-interface.md)  
  
 [Interfejs obiektu ICommandTarget](../mfc/reference/icommandtarget-interface.md)  
  
 [Interfejs ICommandUI](../mfc/reference/icommandui-interface.md)  
  
 [Interfejs IView](../mfc/reference/iview-interface.md)  
  
 [Commandhandler — obiekt](../atl/commandhandler.md)  
  
 [Ddx_managedcontrol —](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)  
  
 [Uicheckstate —](../mfc/reference/uicheckstate-enumeration.md)  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Formularze systemu Windows](/dotnet/framework/winforms/index)  
  
 [Formanty formularzy systemu Windows](/dotnet/framework/winforms/controls/index)  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)   
 [Widoki formularzy](../mfc/form-views-mfc.md)