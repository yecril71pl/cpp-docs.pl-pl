---
title: Przełączanie między kontrolkami okna dialogowego i kodem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog editor, accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog editor, switching between controls and code
ms.assetid: 7da73815-b853-4203-ba45-bbe570695122
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ffcb4621bf0005e6b22991da7a2dde9372afa6c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891925"
---
# <a name="switching-between-dialog-box-controls-and-code"></a>Przełączanie między kontrolkami okna dialogowego i kodem
W aplikacjach MFC możesz kliknąć dwukrotnie na formanty okna dialogowego, aby przejść do ich obsługi kodu lub do szybkiego tworzenia szkieletu funkcje programu obsługi.  
  
 Za pomocą formantu zaznaczone, kliknij przycisk **ControlEvents** przycisk lub **wiadomości** przycisk [okna właściwości](/visualstudio/ide/reference/properties-window) Aby wyświetlić listę wszystkich komunikatów systemu Windows i zdarzenia dostępna dla wybranego elementu. Wybierz z listy, aby utworzyć lub edytować funkcje programu obsługi.  
  
### <a name="to-jump-to-code-from-the-dialog-editor"></a>Aby przejść do kodu z edytora okien dialogowych  
  
1.  Kliknij dwukrotnie formantu w oknie dialogowym, aby przejść do deklaracji pod kątem jego obsługa funkcji ostatnio zaimplementowanym komunikatów. (Dla klasy oparty na ATL okien dialogowych, możesz zawsze przejść do definicji konstruktora.)  
  
### <a name="to-view-events-for-a-control"></a>Aby wyświetlić zdarzenia dla formantu  
  
1.  Za pomocą formantu zaznaczone, kliknij przycisk **ControlEvents** przycisk [okna właściwości](/visualstudio/ide/reference/properties-window).  
  
    > [!NOTE]
    >  Kliknięcie przycisku **ControlEvents** przycisku, gdy *okno dialogowe* ma fokus udostępnia listę wszystkich kontrolek w oknie dialogowym, które następnie można rozszerzyć do edycji zdarzenia dla pojedynczych formantów.  
  
     Jeśli jeden formant ma fokus w oknie dialogowym, można kliknij go prawym przyciskiem myszy i wybierz **Dodaj program obsługi zdarzeń** z menu skrótów. Dzięki temu można określić klasę, do którego jest dodawany program obsługi. Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi zdarzeń](../ide/adding-an-event-handler-visual-cpp.md).  
  
### <a name="to-view-messages-for-a-dialog-box"></a>Aby wyświetlić wiadomości dla okna dialogowego  
  
1.  Okno dialogowe zaznaczone, kliknij **wiadomości** przycisku na [okno właściwości](/visualstudio/ide/reference/properties-window).  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor okien dialogowych](../windows/dialog-editor.md)

