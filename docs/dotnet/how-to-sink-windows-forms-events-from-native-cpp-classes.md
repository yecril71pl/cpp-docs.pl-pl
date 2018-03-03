---
title: "Porady: obiekt Sink zdarzenia Windows Forms z klas natywnych języka C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- event handling, managed/native interop
- event handling, sinking .NET in C++
- event handling, .NET/native interop
- event handling, Windows Forms in C++
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2dd3778dad837ffe23d17b58b4e579844dc71f40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-sink-windows-forms-events-from-native-c-classes"></a>Porady: wychwytywanie zdarzeń interfejsu Windows Forms z klas natywnych języka C++
Można włączyć macierzystych klas C++ odbierać wywołań zwrotnych z zarządzanego zdarzenia wywoływane z formanty formularzy systemu Windows lub innej formy w formacie mapy makr MFC. Wychwytywanie zdarzeń w widoków i okien dialogowych jest podobny do tego samego zadania dla formantów czynności.  
  
 W tym celu należy:  
  
-   Dołącz `OnClick` obsługi zdarzeń do sterowania przy użyciu [make_delegate —](../mfc/reference/delegate-and-interface-maps.md#make_delegate).  
  
-   Tworzenie przy użyciu mapy delegata [begin_delegate_map —](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map), [end_delegate_map —](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map), i [event_delegate_entry —](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry).  
  
 W tym przykładzie kontynuuje pracę, jak w [porady: czy powiązania danych DDX/ddv za pomocą interfejsu Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).  
  
 Teraz, spowodują powiązania formantu MFC (`m_MyControl`) z obiektem delegowanym zdarzeń zarządzanego programu obsługi o nazwie `OnClick` dla zarządzanej <xref:System.Windows.Forms.Control.Click> zdarzeń.  
  
### <a name="to-attach-the-onclick-event-handler"></a>Aby dołączyć program obsługi zdarzeń:  
  
1.  Dodaj następujący kod do implementacji BOOL CMFC01Dlg::OnInitDialog:  
  
    ```  
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );  
    ```  
  
2.  Dodaj następujący kod do sekcji publicznej w deklaracji klasy CMFC01Dlg: cdialog — publiczny.  
  
    ```  
    // delegate map  
    BEGIN_DELEGATE_MAP( CMFC01Dlg )  
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )  
    END_DELEGATE_MAP()  
  
    void OnClick( System::Object^ sender, System::EventArgs^ e );  
    ```  
  
3.  Na koniec należy dodać implementację `OnClick` do CMFC01Dlg.cpp:  
  
    ```  
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)  
    {  
        AfxMessageBox(_T("Button clicked"));  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [MAKE_DELEGATE —](../mfc/reference/delegate-and-interface-maps.md#make_delegate)   
 [BEGIN_DELEGATE_MAP —](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)   
 [END_DELEGATE_MAP —](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)   
 [EVENT_DELEGATE_ENTRY —](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)