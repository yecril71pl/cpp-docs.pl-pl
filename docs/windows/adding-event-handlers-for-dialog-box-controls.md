---
title: "Dodawanie programów obsługi zdarzeń dla formantów okna dialogowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Dialog editor, adding event handlers to controls
- controls [C++], event handlers
- dialog box controls, events
- event handlers, for dialog box controls
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4dd70693ebbdb7b286206f49fab3063c0aa72160
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="adding-event-handlers-for-dialog-box-controls"></a>Dodawanie obsługi zdarzeń dla formantów okna dialogowego
Dla projektu okien dialogowych, które są już skojarzone z klasą możesz można korzystać z niektórych skróty podczas tworzenia procedury obsługi zdarzeń. Może szybko utworzyć programu obsługi dla zdarzenia powiadomień kontroli domyślne lub dla dowolnego odpowiednich komunikatów systemu Windows.  
  
#### <a name="to-create-a-handler-for-the-default-control-notification-event"></a>Aby utworzyć programu obsługi dla zdarzenia powiadomień kontrolki domyślne  
  
1.  Kliknij dwukrotnie formant. Otwiera edytora tekstu.  
  
2.  Dodaj kod obsługi powiadamiania kontrolki w edytorze tekstu.  
  
#### <a name="to-create-a-handler-for-any-applicable-windows-message"></a>Aby utworzyć program obsługi żadnych odpowiednich komunikatów systemu Windows  
  
1.  Kliknij formant, dla którego chcesz obsługiwać zdarzenia z powiadomieniem.  
  
2.  W [okna właściwości](/visualstudio/ide/reference/properties-window), kliknij przycisk **ControlEvents** przycisk, aby wyświetlić listę typowych zdarzeń systemu Windows skojarzony z formantem. Na przykład standardowe **OK** znajdującego się na **o** okno dialogowe wyświetla następujące zdarzenia powiadomień:  
  
 **BN_CLICKED**  
  
 **BN_DOUBLECLICKED**  
  
 **BN_KILLFOCUS**  
  
 **BN_SETFOCUS**  
  
    > [!NOTE]
    >  Alternatywnie okno dialogowe Wybieranie i kliknij przycisk **ControlEvents** przycisk, aby wyświetlić listę typowych zdarzeń systemu Windows dla wszystkich kontrolek w oknie dialogowym.  
  
3.  W **właściwości** okna, kliknij prawy kolumnę obok zdarzenia w celu obsługi, a następnie wybierz nazwę zdarzenia sugerowane powiadomienia (na przykład **OnBnClickedOK** dojść **BN_CLICKED** ).  
  
    > [!NOTE]
    >  Alternatywnie możesz podać nazwę programu obsługi zdarzeń wybrana, a nie wybrana domyślna nazwa programu obsługi zdarzeń.  
  
     Po wybraniu zdarzenia programu Visual Studio otwiera edytor tekstu i wyświetla kod obsługi zdarzenia. Na przykład następujący kod jest dodawany do domyślnie **OnBnClickedOK**:  
  
 ```  
    void CAboutDlg::OnBnClickedOk(void)  
 { *// TODO: Add your control notification handler code here  
 }  
 ```  
  
 Jeśli chcesz dodać procedury obsługi zdarzeń do klasy innej niż jedna implementacja okna dialogowego, użyj [Kreator obsługi zdarzeń](../ide/event-handler-wizard.md). Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi zdarzeń](../ide/adding-an-event-handler-visual-cpp.md).  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
### <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Domyślne zdarzenia formantów](../windows/default-control-events.md)   
 [Definiowanie zmiennych Członkowskich dla formantów okna dialogowego](../windows/defining-member-variables-for-dialog-controls.md)   
 [Formanty okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md)   
 [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)   
 [Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)   
 [Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)   
 [Zastępowanie funkcji wirtualnych](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Handler komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md)

