---
title: 'Porady: Dodawanie polecenia routingu do Windows formantu formularzy | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5161e23d17283ba1495baf6fcb201943f8b6ae12
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422418"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>Porady: dodawanie routingu poleceń do formantu interfejsu Windows Forms

[CWinFormsView](../mfc/reference/cwinformsview-class.md) kieruje polecenia i komunikaty interfejsu użytkownika aktualizacji poleceń do formantu użytkownika, aby zezwolić na obsługę jego poleceń MFC (na przykład ramek elementów menu i przycisków paska narzędzi).

Formant użytkownika używa [ICommandTarget::Initialize](../mfc/reference/icommandtarget-interface.md#initialize) do przechowywania odwołania do obiektu źródła polecenia w `m_CmdSrc`, jak pokazano w poniższym przykładzie. Aby użyć `ICommandTarget` należy dodać odwołanie do mfcmifc80.dll.

`CWinFormsView` obsługuje wiele wspólnych powiadomień widoku MFC, przekazując je do zarządzanego formantu użytkownika. Te powiadomienia obejmują [OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate), [OnUpdate](../mfc/reference/iview-interface.md#onupdate) i [OnActivateView](../mfc/reference/iview-interface.md#onactivateview) metody.

W tym temacie założono, że została już ukończona [porady: tworzenie kontrolki użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) i [porady: tworzenie kontrolki użytkownika i hosta widoku MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC

1. Otwórz bibliotekę kontrolek formularzy Windows utworzone w [porady: tworzenie kontrolki użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

1. Dodaj odwołanie do mfcmifc80.dll, co można zrobić, klikając prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań**, wybierając opcję **Dodaj**, **odwołania**, a następnie przechodząc do Microsoft Visual Studio 10.0\VC\atlmfc\lib.

1. Otwórz plik UserControl1.Designer.cs i dodaj następującą instrukcję using:

    ```
    using Microsoft.VisualC.MFC;
    ```

1. Ponadto w UserControl1.Designer.cs Zmień ten wiersz:

    ```
    partial class UserControl1
    ```

     Następujące zmiany:

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. Dodaj to jako pierwszy wiersz w definicji klasy dla `UserControl1`:

    ```
    private ICommandSource m_CmdSrc;
    ```

1. Dodaj następujące definicje metody do `UserControl1` (w następnym kroku zostanie utworzony identyfikator formantu MFC):

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

1. Otwórz aplikację MFC, został utworzony w [porady: tworzenie kontrolki użytkownika i hosta widoku MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

1. Dodaj opcję menu, którą będzie wywoływać `singleMenuHandler`.

     Przejdź do **widok zasobów** (Ctrl + Shift + E), rozwiń węzeł **Menu** folder, a następnie kliknij dwukrotnie plik **IDR_MFC02TYPE**. Spowoduje to wyświetlenie Edytora menu.

     Dodaj opcję menu w dolnej części **widoku** menu. Zwróć uwagę na identyfikator opcji menu w **właściwości** okna. Zapisz plik.

     W **Eksploratora rozwiązań**, otwórz plik Resource.h, skopiuj wartość Identyfikatora dla opcji menu dodanej przed chwilą i wklej tę wartość jako pierwszy parametr `m_CmdSrc.AddCommandHandler` wywołania w projekcie języka C# `Initialize` (zastępując —Metoda`32771` w razie potrzeby).

9. Skompiluj i uruchom projekt.

     Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

     Na **debugowania** menu, kliknij przycisk **Uruchom bez debugowania**.

     Wybierz opcję menu, którą dodałeś. Należy zauważyć, że wywoływana jest metoda w pliku .dll.

## <a name="see-also"></a>Zobacz też

[Hostowanie kontrolki użytkownika interfejsu Windows Forms jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Klasa ICommandSource](../mfc/reference/icommandsource-interface.md)<br/>
[Klasa ICommandTarget](../mfc/reference/icommandtarget-interface.md)
