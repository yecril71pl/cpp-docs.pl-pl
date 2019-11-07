---
title: Hostowanie kontrolki użytkownika formularza systemu Windows jako okna dialogowego MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
ms.openlocfilehash: 1351f0b2aa4ebc288469231a27c691237b52b1c1
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73704131"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hostowanie kontrolki użytkownika formularza systemu Windows jako okna dialogowego MFC

MFC udostępnia klasy szablonu [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) , dzięki czemu można hostować Windows Formsą kontrolkę użytkownika (<xref:System.Windows.Forms.UserControl>) w modalnym lub niemodalnym oknie dialogowym MFC. `CWinFormsDialog` pochodzi od klasy MFC [CDialog](../mfc/reference/cdialog-class.md), więc okno dialogowe można uruchomić jako modalne lub niemodalne.

Proces, którego `CWinFormsDialog` używa do hostowania kontrolki użytkownika, jest podobny do opisanego w temacie [hostowanie kontrolki użytkownika formularza systemu Windows w oknie dialogowym MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). `CWinFormsDialog` jednak zarządza inicjalizacją i hostem kontrolki użytkownika, aby nie musiała być zaprogramowana ręcznie.

Aby uzyskać przykładową aplikację, która zawiera Windows Forms używane z MFC, zobacz [integrację MFC i Windows Forms](https://www.microsoft.com/en-us/download/details.aspx?id=2113).

### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC

1. Utwórz projekt aplikacji MFC.

   W menu **plik** wybierz pozycję **Nowy**, a następnie kliknij pozycję **projekt**. W folderze **wizualizacji C++**  wybierz pozycję **aplikacja MFC**.

   W polu **Nazwa** wprowadź `MFC03` i zmień ustawienie rozwiązanie na **Dodaj do rozwiązania**. Kliknij przycisk **OK**.

   W **Kreatorze aplikacji MFC**Zaakceptuj wszystkie ustawienia domyślne, a następnie kliknij przycisk **Zakończ**. Spowoduje to utworzenie aplikacji MFC z interfejsem wielu dokumentów.

1. Skonfiguruj projekt.

   W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu **MFC03** , a następnie wybierz polecenie **Właściwości**. Zostanie wyświetlone okno dialogowe **strony właściwości** .

   W oknie dialogowym **strony właściwości** w kontrolce drzewa **Właściwości konfiguracji** wybierz opcję **Ogólne**, a następnie w sekcji **wartości domyślne projektu** Ustaw **obsługę środowiska uruchomieniowego języka wspólnego** na **obsługę środowiska uruchomieniowego języka wspólnego ( /CLR)** . Kliknij przycisk **OK**.

1. Dodaj odwołanie do kontrolki .NET.

   W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu **MFC03** i wybierz polecenie **Dodaj**, **odwołania**. Na **stronie właściwości**kliknij pozycję **Dodaj nowe odwołanie**, wybierz pozycję WindowsControlLibrary1 (na karcie **projekty** ), a następnie kliknij przycisk **OK**. Spowoduje to dodanie odwołania w postaci opcji kompilatora [/Fu](../build/reference/fu-name-forced-hash-using-file.md) , tak aby program skompiluje; Kopiuje także plik WindowsControlLibrary1. dll do katalogu projektu `MFC03`, dzięki czemu program zostanie uruchomiony.

1. Dodaj `#include <afxwinforms.h>` do *PCH. h* (*stdafx. h* w Visual Studio 2017 i starszych) na końcu istniejących instrukcji `#include`.

1. Dodaj nową klasę, która podklasy `CDialog`.

   Kliknij prawym przyciskiem myszy nazwę projektu i Dodaj klasę MFC (o nazwie CHostForWinForm), która jest podklasą `CDialog`. Ponieważ nie potrzebujesz zasobu okna dialogowego, możesz usunąć identyfikator zasobu (wybierz **Widok zasobów**, rozwiń folder **okna dialogowego** i Usuń zasób `IDD_HOSTFORWINFORM`.  Następnie usuń wszystkie odwołania do identyfikatora w kodzie.).

1. Zastąp `CDialog` w plikach CHostForWinForm. h i CHostForWinForm. cpp z `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`.

1. Wywołaj DoModal w klasie CHostForWinForm.

   W MFC03. cpp Dodaj `#include "HostForWinForm.h"`.

   Przed instrukcją Return w definicji CMFC03App:: InitInstance, Dodaj:

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. Skompiluj i Uruchom projekt.

   W menu **kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

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

1. Skompiluj i Uruchom projekt. Po kliknięciu przycisku, który znajduje się w formularzu systemu Windows, zostanie uruchomiony kod w aplikacji MFC.

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

1. Skompiluj i Uruchom projekt.

## <a name="see-also"></a>Zobacz także

<xref:System.Windows.Forms.UserControl?displayProperty=fullName>
[przy użyciu kontrolki użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
