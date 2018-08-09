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
ms.openlocfilehash: b288e97030cad7e38caf19fb47f7a058c3ead61d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643111"
---
# <a name="switching-between-dialog-box-controls-and-code"></a>Przełączanie między kontrolkami okna dialogowego i kodem
W aplikacjach MFC można kliknąć dwukrotnie na formantów okna dialogowego, aby przejść do swój kod procedury obsługi lub szybko utworzyć szkieletu funkcje obsługi.  
  
 Dzięki nim wybrany jakiś formant, kliknij przycisk **ControlEvents** przycisk lub **wiadomości** znajdujący się w [okno właściwości](/visualstudio/ide/reference/properties-window) Aby wyświetlić pełną listę Windows komunikaty i zdarzenia dostępne dla wybranego elementu. Wybierz z listy, aby utworzyć lub edytować funkcje programu obsługi.  
  
### <a name="to-jump-to-code-from-the-dialog-editor"></a>Aby przejść do kodu z edytora okien dialogowych  
  
1.  Kliknij dwukrotnie formantu w oknie dialogowym, aby przejść do deklaracji pod kątem komunikat ostatnio zaimplementowano funkcji obsługi. (Dla oparty na bibliotece ATL klasy okien dialogowych, możesz zawsze przejść do definicji konstruktora.)  
  
### <a name="to-view-events-for-a-control"></a>Aby wyświetlić zdarzenia kontrolki  
  
1.  Dzięki nim wybrany jakiś formant, kliknij przycisk **ControlEvents** znajdujący się w [okno właściwości](/visualstudio/ide/reference/properties-window).  
  
    > [!NOTE]
    >  Klikając **ControlEvents** przycisk, kiedy *okno dialogowe* ma fokus udostępnia listę wszystkich kontrolek w oknie dialogowym, które można następnie rozszerzyć do zdarzeń dla poszczególnych formantów edycji.  
  
     Gdy jeden formant ma fokus w oknie dialogowym, można go prawym przyciskiem myszy i wybrać **dodać program obsługi zdarzeń** z menu skrótów. Dzięki temu można określić klasę, do którego jest dodawany program obsługi. Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi zdarzeń](../ide/adding-an-event-handler-visual-cpp.md).  
  
### <a name="to-view-messages-for-a-dialog-box"></a>Aby wyświetlić wiadomości dla okna dialogowego  
  
1.  Wybrane okno dialogowe, kliknij **wiadomości** znajdujący się w [okno właściwości](/visualstudio/ide/reference/properties-window).  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor okien dialogowych](../windows/dialog-editor.md)