---
title: 'Porady: wychwytywanie zdarzeń interfejsu Windows Forms z klas natywnych języka C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, managed/native interop
- event handling, sinking .NET in C++
- event handling, .NET/native interop
- event handling, Windows Forms in C++
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
ms.openlocfilehash: 1bc601a4dbd7a51695b6964ab4d0ee47531c1b2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555912"
---
# <a name="how-to-sink-windows-forms-events-from-native-c-classes"></a>Porady: wychwytywanie zdarzeń interfejsu Windows Forms z klas natywnych języka C++

Można włączyć macierzystych klas C++ odbierać wywołania zwrotne z zarządzanego zdarzenia wywoływane z kontrolek formularzy Windows Forms lub inne formy z formatem mapy makr MFC. Wychwytywania zdarzeń w widokach i oknach dialogowych jest podobny do tego samego zadania dla formantów czynności.

Aby to zrobić, należy:

- Dołącz `OnClick` programu obsługi zdarzeń do formantu za pomocą [MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate).

- Utwórz mapę delegata za pomocą [BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map), [END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map), i [EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry).

W tym przykładzie kontynuuje pracę, jak w [porady: wykonaj powiązanie danych DDX/DDV za pomocą interfejsu Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

Teraz zostanie skojarzony formant MFC (`m_MyControl`) za pomocą delegata obsługi zdarzeń zarządzanych, o nazwie `OnClick` dla zarządzanej <xref:System.Windows.Forms.Control.Click> zdarzeń.

### <a name="to-attach-the-onclick-event-handler"></a>Aby dołączyć program obsługi zdarzeń:

1. Dodaj następujący kod do implementacji BOOL CMFC01Dlg::OnInitDialog:

    ```
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );
    ```

1. Dodaj następujący kod do sekcji publicznej w deklaracji klasy CMFC01Dlg: CDialog publicznych.

    ```
    // delegate map
    BEGIN_DELEGATE_MAP( CMFC01Dlg )
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )
    END_DELEGATE_MAP()

    void OnClick( System::Object^ sender, System::EventArgs^ e );
    ```

1. Na koniec należy dodać to implementacja `OnClick` do CMFC01Dlg.cpp:

    ```
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)
    {
        AfxMessageBox(_T("Button clicked"));
    }
    ```

## <a name="see-also"></a>Zobacz też

[MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)<br/>
[BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)<br/>
[END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)<br/>
[EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)