---
title: 'Porady: wywoływanie właściwości i metod interfejsu Windows Forms kontrolować | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- method calls, Windows Forms
- calling methods, Windows Forms control
- calling properties, Windows Forms control
- Windows Forms controls [C++], methods
- calling properties
- Windows Forms controls [C++], properties
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1d3f8dc2251dbfbcd8155b0edc512a9dc40bacc2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393402"
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>Porady: wywoływanie właściwości i metod formantu interfejsu Windows Forms

Ponieważ [CWinFormsView::GetControl](../mfc/reference/cwinformsview-class.md#getcontrol) zwraca wskaźnik do <xref:System.Windows.Forms.Control?displayProperty=fullName>, a nie wskaźnik do `WindowsControlLibrary1::UserControl1`, zaleca się dodać elementu członkowskiego typu kontrolki użytkownika i zainicjować go w [IView::OnInitialUpdate ](../mfc/reference/iview-interface.md#oninitialupdate). Teraz można wywołać metody i właściwości, za pomocą `m_ViewControl`.

W tym temacie założono, że została już ukończona [porady: tworzenie kontrolki użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) i [porady: tworzenie kontrolki użytkownika i hosta widoku MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC

1. Otwórz aplikację MFC, został utworzony w [porady: tworzenie kontrolki użytkownika i hosta widoku MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

1. Dodaj następujący wiersz do sekcji publicznej zastąpienia `CMFC02View` deklaracji w MFC02View.h klasy.

     `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`

1. Dodaj zastąpienie dla OnInitialupdate.

     Wyświetlanie **właściwości** okna (F4). W **Widok klas** (CTRL + SHIFT + C), wybierz klasę CMFC02View. W **właściwości** okna, wybierz ikonę dla zastąpień. Scoll w dół na liście, aby OnInitialUpdate. Kliknij pozycję na liście rozwijanej listy i wybierz przycisk \<Dodaj >. W MFC02View.cpp. Upewnij się, że treści funkcji OnInitialUpdate jest następująca:

    ```
    CWinFormsView::OnInitialUpdate();
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());
    m_ViewControl->textBox1->Text = gcnew System::String("hi");
    ```

1. Skompiluj i uruchom projekt.

     Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

     Na **debugowania** menu, kliknij przycisk **Uruchom bez debugowania**.

     Należy zauważyć, że teraz jest inicjowany w polu tekstowym.

## <a name="see-also"></a>Zobacz też

[Hostowanie kontrolki użytkownika interfejsu Windows Forms jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)