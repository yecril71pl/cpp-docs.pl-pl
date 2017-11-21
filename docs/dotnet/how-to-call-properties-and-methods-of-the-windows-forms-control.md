---
title: "Porady: wywoływanie właściwości i metod interfejsu Windows Forms kontrolować | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- method calls, Windows Forms
- calling methods, Windows Forms control
- calling properties, Windows Forms control
- Windows Forms controls [C++], methods
- calling properties
- Windows Forms controls [C++], properties
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 28e6d025d6c2aa485b5687117d64afeb7e402a79
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>Porady: wywoływanie właściwości i metod formantu interfejsu Windows Forms
Ponieważ [CWinFormsView::GetControl](../mfc/reference/cwinformsview-class.md#getcontrol) zwraca wskaźnik do <xref:System.Windows.Forms.Control?displayProperty=fullName>, a nie wskaźnikiem do `WindowsControlLibrary1::UserControl1`, zaleca się dodać elementu członkowskiego typu kontrolki użytkownika i zainicjować go w [IView::OnInitialUpdate ](../mfc/reference/iview-interface.md#oninitialupdate). Teraz można wywołać metody i właściwości za pomocą `m_ViewControl`.  
  
 W tym temacie założono wcześniej zakończył [porady: Tworzenie formantu użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) i [porady: Tworzenie formantu użytkownika i widoku MDI hosta](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC  
  
1.  Otwórz aplikację MFC utworzony w [porady: Tworzenie formantu użytkownika i widoku MDI hosta](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
2.  Dodaj następujący wiersz do sekcji publicznego zastąpienia `CMFC02View` deklaracji w MFC02View.h klasy.  
  
     `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`  
  
3.  Dodaj zastąpienie dla OnInitialupdate.  
  
     Wyświetl **właściwości** okna (F4). W **widoku klasy** (CTRL + SHIFT + C), wybierz klasę CMFC02View. W **właściwości** okna, wybierz ikonę dla zastąpień. Scoll w dół na liście, aby OnInitialUpdate. Kliknij na rozwijanej liście, a następnie wybierz \<Dodaj >. W MFC02View.cpp. Upewnij się, że treść funkcji OnInitialUpdate wygląda następująco:  
  
    ```  
    CWinFormsView::OnInitialUpdate();  
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());  
    m_ViewControl->textBox1->Text = gcnew System::String("hi");  
    ```  
  
4.  Tworzenie i uruchamianie projektu.  
  
     Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Na **debugowania** menu, kliknij przycisk **uruchomienie bez debugowania**.  
  
     Zwróć uwagę, czy pole tekstowe teraz jest inicjowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Hostowanie formantu użytkownika formularzy systemu Windows jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)