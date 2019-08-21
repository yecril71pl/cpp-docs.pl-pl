---
title: Hostowanie kontrolki użytkownika formularza systemu Windows jako okna dialogowego MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
ms.openlocfilehash: 96730cb3902674373e3e2429b7bc51cbbe257ff3
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630840"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hostowanie kontrolki użytkownika formularza systemu Windows jako okna dialogowego MFC

MFC udostępnia klasy szablonu [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) , dzięki czemu można hostować Windows Formsą kontrolkę użytkownika<xref:System.Windows.Forms.UserControl>() w modalnym lub niemodalnym oknie dialogowym MFC. `CWinFormsDialog`jest pochodną klasy MFC [CDialog](../mfc/reference/cdialog-class.md), więc okno dialogowe można uruchomić jako modalne lub niemodalne.

Proces wykorzystywany przez `CWinFormsDialog` program do hostowania kontrolki użytkownika jest podobny do opisanego w temacie [hostowanie kontrolki użytkownika formularza systemu Windows w oknie dialogowym MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). `CWinFormsDialog` Jednak zarządza inicjalizacją i hostem kontrolki użytkownika, aby nie musiała być zaprogramowana ręcznie.

Aby uzyskać przykładową aplikację, która zawiera Windows Forms używane z MFC, zobacz [integrację MFC i Windows Forms](https://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC

1. Utwórz projekt aplikacji MFC.

   W menu **plik** wybierz pozycję **Nowy**, a następnie kliknij pozycję **projekt**. W folderze  **C++ wizualizacji** wybierz pozycję **aplikacja MFC**.

   W polu **Nazwa** wprowadź `MFC03` i zmień ustawienie rozwiązanie na **Dodaj do rozwiązania**. Kliknij przycisk **OK**.

   W **Kreatorze aplikacji MFC**Zaakceptuj wszystkie ustawienia domyślne, a następnie kliknij przycisk **Zakończ**. Spowoduje to utworzenie aplikacji MFC z interfejsem wielu dokumentów.

1. Skonfiguruj projekt.

   W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu **MFC03** , a następnie wybierz polecenie **Właściwości**. Zostanie wyświetlone okno dialogowe **strony właściwości** .

   W oknie dialogowym **strony właściwości** w kontrolce drzewa **Właściwości konfiguracji** wybierz opcję **Ogólne**, a następnie w sekcji **wartości domyślne projektu** Ustaw **obsługę środowiska uruchomieniowego języka wspólnego** na **obsługę środowiska uruchomieniowego języka wspólnego ( /CLR)** . Kliknij przycisk **OK**.

1. Dodaj odwołanie do kontrolki .NET.

   W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu **MFC03** i wybierz polecenie **Dodaj**, **odwołania**. Na **stronie właściwości**kliknij pozycję **Dodaj nowe odwołanie**, wybierz pozycję WindowsControlLibrary1 (na karcie **projekty** ), a następnie kliknij przycisk **OK**. Spowoduje to dodanie odwołania w postaci opcji kompilatora [/Fu](../build/reference/fu-name-forced-hash-using-file.md) , tak aby program skompiluje; Kopiuje także plik WindowsControlLibrary1. dll do `MFC03` katalogu projektu, dzięki czemu program zostanie uruchomiony.

1. Dodaj `#include <afxwinforms.h>` do *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i starszych) na końcu istniejących `#include` instrukcji.

1. Dodaj nową klasę podklas `CDialog`.

   Kliknij prawym przyciskiem myszy nazwę projektu i Dodaj klasę MFC (o nazwie CHostForWinForm) podklasy `CDialog`. Ponieważ nie potrzebujesz zasobu okna dialogowego, możesz usunąć identyfikator zasobu (wybierz **Widok zasobów**, rozwiń folder **okna dialogowego** i Usuń `IDD_HOSTFORWINFORM` zasób.  Następnie usuń wszystkie odwołania do identyfikatora w kodzie.).

1. Zastąp `CDialog` w plikach CHostForWinForm. h i CHostForWinForm. cpp `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`przy użyciu.

1. Wywołaj DoModal w klasie CHostForWinForm.

   W MFC03. cpp, Dodaj `#include "HostForWinForm.h"`.

   Przed instrukcją Return w definicji CMFC03App:: InitInstance, Dodaj:

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. Skompiluj i uruchom projekt.

   Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

   W menu **debugowanie** kliknij polecenie **Uruchom bez debugowania**.

   Następnie dodasz kod do monitorowania stanu kontrolki na Windows Forms z aplikacji MFC.

1. Dodaj program obsługi dla OnInitDialog.

   Wyświetlanie okna **Właściwości** (F4). W **Widok klasy**wybierz pozycję CHostForWinForm. W oknie **Właściwości** wybierz pozycję zastąpienia i w wierszu dla OnInitDialog kliknij kolumnę po lewej stronie i wybierz pozycję \< Dodaj >. Spowoduje to dodanie następującego wiersza do CHostForWinForm. h:

    ```cpp
    virtual BOOL OnInitDialog();
    ```

1. Zdefiniuj OnInitDialog (w CHostForWinForm. cpp) w następujący sposób:

    ```cpp
    BOOL CHostForWinForm::OnInitDialog() {
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);
       return TRUE;
    }
    ```

1. Następnie Dodaj procedurę obsługi OnButton1. Dodaj następujące wiersze do publicznej sekcji klasy CHostForWinForm w CHostForWinForm. h:

    ```cpp
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );

    BEGIN_DELEGATE_MAP( CHostForWinForm )
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );
    END_DELEGATE_MAP()
    ```

   W CHostForWinForm. cpp Dodaj następującą definicję:

    ```cpp
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )
    {
       System::Windows::Forms::MessageBox::Show("test");
    }
    ```

1. Skompiluj i uruchom projekt. Po kliknięciu przycisku, który znajduje się w formularzu systemu Windows, zostanie uruchomiony kod w aplikacji MFC.

    Następnie dodasz kod do wyświetlania z kodu MFC wartości w polu tekstowym w formularzu systemu Windows.

1. W sekcji Public klasy CHostForWinForm w CHostForWinForm. h Dodaj następującą deklarację:

    ```cpp
    CString m_sEditBoxOnWinForm;
    ```

1. W definicji DoDataExchange w CHostForWinForm. cpp Dodaj następujące trzy wiersze na końcu funkcji:

    ```cpp
    if (pDX->m_bSaveAndValidate)
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);
    else
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);
    ```

1. W definicji OnButton1 w CHostForWinForm. cpp Dodaj następujące trzy wiersze na końcu funkcji:

    ```cpp
    this->UpdateData(TRUE);
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);
    System::Windows::Forms::MessageBox::Show(z);
    ```

1. Skompiluj i uruchom projekt.

## <a name="see-also"></a>Zobacz także

<xref:System.Windows.Forms.UserControl?displayProperty=fullName>
[Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
