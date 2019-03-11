---
title: 'Instrukcje: Kontrolowanie wywoływanie właściwości i metod interfejsu Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- method calls, Windows Forms
- calling methods, Windows Forms control
- calling properties, Windows Forms control
- Windows Forms controls [C++], methods
- calling properties
- Windows Forms controls [C++], properties
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
ms.openlocfilehash: 61b565839b3f3c24670819fdcf2dde558e3461ac
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743766"
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>Instrukcje: Kontrolowanie wywoływanie właściwości i metod interfejsu Windows Forms

Ponieważ [CWinFormsView::GetControl](../mfc/reference/cwinformsview-class.md#getcontrol) zwraca wskaźnik do <xref:System.Windows.Forms.Control?displayProperty=fullName>, a nie wskaźnik do `WindowsControlLibrary1::UserControl1`, zaleca się dodać elementu członkowskiego typu kontrolki użytkownika i zainicjować go w [IView::OnInitialUpdate ](../mfc/reference/iview-interface.md#oninitialupdate). Teraz można wywołać metody i właściwości, za pomocą `m_ViewControl`.

W tym temacie założono, że została już ukończona [jak: Tworzenie kontrolki użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) i [jak: Tworzenie kontrolki użytkownika i hostowanie widoku MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC

1. Otwórz aplikację MFC, został utworzony w [jak: Tworzenie kontrolki użytkownika i hostowanie widoku MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

1. Dodaj następujący wiersz do sekcji publicznej zastąpienia `CMFC02View` deklaracji w MFC02View.h klasy.

   `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`

1. Dodaj zastąpienie dla OnInitialupdate.

   Wyświetlanie **właściwości** okna (F4). W **Widok klas** (CTRL + SHIFT + C), wybierz klasę CMFC02View. W **właściwości** okna, wybierz ikonę dla zastąpień. Scoll w dół na liście, aby OnInitialUpdate. Kliknij pozycję na liście rozwijanej listy i wybierz przycisk \<Dodaj >. In MFC02View.cpp. Upewnij się, że treści funkcji OnInitialUpdate jest następująca:

    ```
    CWinFormsView::OnInitialUpdate();
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());
    m_ViewControl->textBox1->Text = gcnew System::String("hi");
    ```

1. Skompiluj i uruchom projekt.

   Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

   Na **debugowania** menu, kliknij przycisk **Uruchom bez debugowania**.

   Należy zauważyć, że teraz jest inicjowany w polu tekstowym.

## <a name="see-also"></a>Zobacz także

[Hostowanie kontrolki użytkownika interfejsu Windows Forms jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
