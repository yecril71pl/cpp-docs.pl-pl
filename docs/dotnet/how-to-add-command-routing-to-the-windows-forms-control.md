---
title: 'Porady: dodawanie routingu poleceń do formantu interfejsu Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
ms.openlocfilehash: ad64a12051c22a0cfca99d3ec9c5abef579902f4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365168"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>Porady: dodawanie routingu poleceń do formantu interfejsu Windows Forms

[CWinFormsView](../mfc/reference/cwinformsview-class.md) trasy poleceń i aktualizacji polecenia komunikaty interfejsu użytkownika do formantu użytkownika, aby umożliwić mu obsługę poleceń MFC (na przykład elementy menu ramki i przyciski paska narzędzi).

Formant użytkownika używa [iCommandTarget::Initialize](../mfc/reference/icommandtarget-interface.md#initialize) do przechowywania odwołania do `m_CmdSrc`obiektu źródłowego polecenia w , jak pokazano w poniższym przykładzie. Aby `ICommandTarget` użyć należy dodać odwołanie do pliku mfcmifc80.dll.

`CWinFormsView`obsługuje kilka typowych powiadomień widoku MFC, przesyłając je do formantu zarządzanego użytkownika. Powiadomienia te obejmują [OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate), [OnUpdate](../mfc/reference/iview-interface.md#onupdate) i [OnActivateView](../mfc/reference/iview-interface.md#onactivateview) metody.

W tym temacie założono, że wcześniej [ukończono: Jak: Tworzenie formantu i hosta użytkownika w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) oraz [jak: Tworzenie kontroli użytkownika i hosta MDI View](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC

1. Otwórz utworzoną bibliotekę formantu formularzy systemu Windows w programie [Jak: Tworzenie formantu użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

1. Dodaj odwołanie do pliku mfcmifc80.dll, co można wykonać, klikając prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań,** wybierając **pozycję Dodaj**, **Odwołanie**, a następnie przeglądając program Microsoft Visual Studio 10.0\VC\atlmfc\lib.

1. Otwórz UserControl1.Designer.cs i dodaj następujące instrukcje za pomocą:

    ```
    using Microsoft.VisualC.MFC;
    ```

1. Ponadto w UserControl1.Designer.cs zmień tę linię:

    ```
    partial class UserControl1
    ```

   wprowadź następujące zmiany:

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. Dodaj to jako pierwszy wiersz definicji klasy dla: `UserControl1`

    ```
    private ICommandSource m_CmdSrc;
    ```

1. Dodaj następujące definicje `UserControl1` metod do (utworzymy identyfikator formantu MFC w następnym kroku):

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

1. Otwórz utworzoną aplikację MFC w [aplikacji Jak: Utwórz formant użytkownika i widok MDI hosta](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

1. Dodaj opcję menu, która `singleMenuHandler`będzie wywoływana .

   Przejdź do **widoku zasobów** (Ctrl+Shift+E), rozwiń folder **Menu,** a następnie kliknij dwukrotnie **IDR_MFC02TYPE**. Spowoduje to wyświetlone edytor menu.

   Dodaj opcję menu u dołu menu **Widok.** Zwróć uwagę na identyfikator opcji menu w oknie **Właściwości.** Zapisz plik.

   W **Eksploratorze rozwiązań**otwórz plik Resource.h, skopiuj wartość identyfikatora dla właśnie dodanej opcji menu i wklej tę wartość jako pierwszy parametr do `m_CmdSrc.AddCommandHandler` wywołania w `Initialize` metodzie projektu C# (zastępując `32771` w razie potrzeby).

1. Tworzenie i uruchamianie projektu.

   W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

   W menu **Debugowanie** kliknij przycisk **Start bez debugowania**.

   Wybierz dodaną opcję menu. Należy zauważyć, że metoda w .dll jest wywoływana.

## <a name="see-also"></a>Zobacz też

[Hostowanie kontrolki użytkownika interfejsu Windows Forms jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Klasa ICommandSource](../mfc/reference/icommandsource-interface.md)<br/>
[Klasa ICommandTarget](../mfc/reference/icommandtarget-interface.md)
