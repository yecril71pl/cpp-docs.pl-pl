---
title: 'Porady: Dodawanie polecenia routingu do systemu Windows formantu formularzy | Dokumentacja firmy Microsoft'
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
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bcd082b22c61e2444d70d936c225e538c2429222
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>Porady: dodawanie routingu poleceń do formantu interfejsu Windows Forms
[CWinFormsView](../mfc/reference/cwinformsview-class.md) kieruje poleceń i polecenia update interfejsu użytkownika wiadomości do kontrolki użytkownika, aby umożliwić jego poleceń MFC (na przykład elementów menu ramki i przycisków paska narzędzi).  
  
 Kontrola użytkownika używa [ICommandTarget::Initialize](../mfc/reference/icommandtarget-interface.md#initialize) do przechowywania odwołanie do obiektu źródłowego polecenia w `m_CmdSrc`, jak pokazano w poniższym przykładzie. Aby użyć `ICommandTarget` należy dodać odwołanie do mfcmifc80.dll.  
  
 `CWinFormsView`obsługuje szereg typowych powiadomienia widoku MFC przez przekazywanie ich do kontrolki użytkownika zarządzanych. Te powiadomienia obejmują [OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate), [OnUpdate](../mfc/reference/iview-interface.md#onupdate) i [OnActivateView](../mfc/reference/iview-interface.md#onactivateview) metody.  
  
 W tym temacie założono wcześniej zakończył [porady: Tworzenie formantu użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) i [porady: Tworzenie formantu użytkownika i widoku MDI hosta](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC  
  
1.  Biblioteka formantów formularzy systemu Windows utworzonego w Otwórz [porady: Tworzenie formantu użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
2.  Dodaj odwołanie do mfcmifc80.dll, co można zrobić, klikając prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań**, wybierając żądane **Dodaj**, **odwołania**, a następnie przechodząc do Microsoft Visual Studio 10.0\VC\atlmfc\lib.  
  
3.  Otwórz UserControl1.Designer.cs i dodaj następującą instrukcję using:  
  
    ```  
    using Microsoft.VisualC.MFC;  
    ```  
  
4.  Ponadto w UserControl1.Designer.cs, należy zmienić ten wiersz:  
  
    ```  
    partial class UserControl1  
    ```  
  
     następujące zmiany:  
  
    ```  
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget  
    ```  
  
5.  Dodaj ją w pierwszym wierszu definicji klasy dla `UserControl1`:  
  
    ```  
    private ICommandSource m_CmdSrc;  
    ```  
  
6.  Dodaj następujące definicje metody do `UserControl1` (w następnym kroku zostanie utworzony identyfikator formantu MFC):  
  
    ```  
    public void Initialize (ICommandSource cmdSrc)  
    {  
       m_CmdSrc = cmdSrc;  
       // need ID of control in MFC dialog and callback function   
       m_CmdSrc.AddCommandHandler(32771, new CommandHandler (singleMenuHandler));  
    }  
  
    private void singleMenuHandler (uint cmdUI)  
    {  
       // User command handler code  
       System.Windows.Forms.MessageBox.Show("Custom menu option was clicked.");  
    }  
    ```  
  
7.  Otwórz aplikację MFC utworzony w [porady: Tworzenie formantu użytkownika i widoku MDI hosta](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
8.  Dodaj opcję menu, która wywoła `singleMenuHandler`.  
  
     Przejdź do **widok zasobów** (Ctrl + Shift + E), rozwiń węzeł **Menu** folder, a następnie kliknij dwukrotnie plik **IDR_MFC02TYPE**. Spowoduje to wyświetlenie Edytora menu.  
  
     Dodaj opcję menu u dołu **widoku** menu. Zwróć uwagę, identyfikator opcji menu w **właściwości** okna. Zapisz plik.  
  
     W **Eksploratora rozwiązań**, otwórz plik Resource.h, skopiuj wartość Identyfikatora opcji menu dodaną i Wklej tej wartości jako pierwszy parametr `m_CmdSrc.AddCommandHandler` wywołań w projekcie C# `Initialize` (zastępując —Metoda`32771` w razie potrzeby).  
  
9. Tworzenie i uruchamianie projektu.  
  
     Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Na **debugowania** menu, kliknij przycisk **uruchomienie bez debugowania**.  
  
     Wybierz opcję menu dodane. Zwróć uwagę, że ma zostać wywołana metoda w biblioteki dll.  
  
## <a name="see-also"></a>Zobacz też  
 [Hostowanie formantu użytkownika formularzy systemu Windows jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [Interfejs ICommandSource](../mfc/reference/icommandsource-interface.md)   
 [Interfejs obiektu ICommandTarget](../mfc/reference/icommandtarget-interface.md)   
 [CommandHandler](http://msdn.microsoft.com/Library/22096734-e074-4aca-8523-4b15590109f9)