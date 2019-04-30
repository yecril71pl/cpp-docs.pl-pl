---
title: 'Instrukcje: Tworzenie kontrolki użytkownika i hosta w oknie dialogowym'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
ms.openlocfilehash: bdf7e2f4961a16e6538c7bbcc690ef44ba87fcaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378977"
---
# <a name="how-to-create-the-user-control-and-host-in-a-dialog-box"></a>Instrukcje: Tworzenie kontrolki użytkownika i hosta w oknie dialogowym

Kroki opisane w tym artykule przyjęto założenie, że tworzysz oparty na dialogu ([klasa CDialog](../mfc/reference/cdialog-class.md)) projektu Microsoft Foundation Classes (MFC), ale można również dodać obsługę formantu Windows Forms do istniejącego okna dialogowego MFC.

### <a name="to-create-the-net-user-control"></a>Aby utworzyć formant użytkownika .NET

1. Utwórz projekt Visual C# Windows Biblioteka kontrolek formularzy, o nazwie `WindowsFormsControlLibrary1`.

   Na **pliku** menu, kliknij przycisk **New** a następnie kliknij przycisk **projektu**. W **Visual C#** folderu, wybierz **Biblioteka kontrolek formularzy Windows**.

   Zaakceptuj `WindowsFormsControlLibrary1` nazwę projektu, klikając pozycję **OK**.

   Domyślnie nazwą formantu .NET będzie `UserControl1`.

1. Dodaj formanty podrzędne do `UserControl1`.

   W **przybornika**, otwórz **wszystkie formularze Windows** listy. Przeciągnij **przycisk** kontrolę `UserControl1` powierzchni projektowej.

   Również dodać **TextBox** kontroli.

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie **UserControl1.Designer.cs** aby go otworzyć do edycji. Zmienić deklaracje pola tekstowego i przycisku z `private` do `public`.

1. Skompiluj projekt.

   Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC

1. Utwórz projekt aplikacji MFC.

   Na **pliku** menu, kliknij przycisk **New** a następnie kliknij przycisk **projektu**. W **Visual C++** folderu, wybierz **aplikacji MFC**.

   W **nazwa** wpisz `MFC01`. Zmień ustawienie rozwiązanie na **Dodaj do rozwiązania**. Kliknij przycisk **OK**.

   W **Kreator aplikacji MFC**, jako typ aplikacji wybierz **oparte o okna dialogowe**. Zaakceptuj pozostałe domyślne ustawienia i kliknij przycisk **Zakończ**. Tworzy to aplikację MFC z okna dialogowego MFC.

1. Dodaj formant zastępczy do okna dialogowego MFC.

   Na **widoku** menu, kliknij przycisk **widok zasobów**. W **widok zasobów**, rozwiń węzeł **okna dialogowego** folder i kliknij dwukrotnie plik `IDD_MFC01_DIALOG`. Zasoby dialogowe pojawiają się w **Edytor zasobów**.

   W **przybornika**, otwórz **Edytor okien dialogowych** listy. Przeciągnij **tekst statyczny** formantu do okna dialogowego. **Tekst statyczny** formant będzie służyć jako symbol zastępczy dla formantu .NET Windows Forms. Zmień jej rozmiar do przybliżonego rozmiaru formantu Windows Forms.

   W **właściwości** oknie zmiany **identyfikator** z **tekst statyczny** kontrolę `IDC_CTRL1` i zmień **TabStop** właściwości **True**.

1. Konfigurowanie projektu dla obsługi środowiska uruchomieniowego języka wspólnego (CLR).

   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu MFC01, a następnie kliknij przycisk **właściwości**.

   W **stron właściwości** dialogowego **właściwości konfiguracji**, wybierz opcję **ogólne**. W **domyślne wartości projektu** sekcji, ustaw **Obsługa środowiska uruchomieniowego języka wspólnego** do **wsparcie (/ clr)**.

   W obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** i wybierz **ogólne** węzła. Ustaw **Format informacji o debugowaniu** do **(/Zi) baza danych programu**.

   Wybierz **generowania kodu** węzła. Ustaw **Włącz minimalną ponowną kompilację** do **nr (/ Gm-)**. Również ustawić **podstawowe sprawdzenia środowiska uruchomieniowego** do **domyślne**.

   Kliknij przycisk **OK** Aby zastosować zmiany.

1. Dodaj odwołanie do formantu .NET.

   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu MFC01, a następnie kliknij przycisk **Dodaj**, **odwołania**. Na **strona właściwości**, kliknij przycisk **Dodaj nowe odwołanie**, wybierz opcję **WindowsFormsControlLibrary1** (w obszarze **projektów** karty) i kliknij przycisk **OK**. Dodaje to odwołanie w formie [/FU](../build/reference/fu-name-forced-hash-using-file.md) — opcja kompilatora tak, aby program został skompilowany. Ponadto umieszcza kopię biblioteki WindowsFormsControlLibrary1.dll w folderze projektu \MFC01\, tak aby program będzie uruchamiany.

1. W pliku Stdafx.h Znajdź ten wiersz:

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Nad nim Dodaj następujące wiersze:

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Dodaj kod, aby utworzyć formant zarządzany.

   Najpierw należy zadeklarować zarządzany formant. W pliku MFC01Dlg.h przejdź do deklaracji klasy okna dialogowego i Dodaj element członkowski danych dla kontrolki użytkownika w zakresie chronionym, w następujący sposób.

    ```
    class CMFC01Dlg : public CDialog
    {
       // ...
       // Data member for the .NET User Control:
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;
    ```

   Następnie należy podać implementacja dla zarządzanego formantu. W MFC01Dlg.cpp w oknie dialogowym zastępowania `CMFC01Dlg::DoDataExchange` wygenerowany przez Kreatora aplikacji MFC (nie `CAboutDlg::DoDataExchange`, która znajduje się w tym samym pliku), Dodaj następujący kod do tworzenia zarządzanego formantu i skojarzyć ją z statyczne zastępczym idc_ctrl1.

    ```
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)
    {
       CDialog::DoDataExchange(pDX);
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);
    }
    ```

1. Skompiluj i uruchom projekt.

   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MFC01** a następnie kliknij przycisk **Ustaw jako projekt startowy**.

   Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

   Na **debugowania** menu, kliknij przycisk **Uruchom bez debugowania**. W oknie dialogowym MFC powinien być wyświetlany formantu programu Windows Forms.

## <a name="see-also"></a>Zobacz także

[Hostowanie kontrolki użytkownika formularza systemu Windows w oknie dialogowym MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)
