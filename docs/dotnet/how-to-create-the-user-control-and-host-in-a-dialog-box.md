---
title: "Porady: Tworzenie formantu użytkownika i hosta w oknie dialogowym | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
caps.latest.revision: "29"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cf0372029a6f6f3c2e2d3030d9e04ddcf6483f14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-create-the-user-control-and-host-in-a-dialog-box"></a>Porady: tworzenie kontrolki użytkownika i hosta w oknie dialogowym
Kroki opisane w tym artykule założono, że są tworzone na podstawie okna dialogowego ([cdialog — klasa](../mfc/reference/cdialog-class.md)) projektu Microsoft Foundation Classes (MFC), ale można również dodać obsługę formantu formularzy systemu Windows do istniejącego okna dialogowego MFC.  
  
### <a name="to-create-the-net-user-control"></a>Aby utworzyć kontrolkę użytkownika platformy .NET  
  
1.  Utwórz projekt Visual C# Windows Biblioteka kontrolek formularzy o nazwie `WindowsFormsControlLibrary1`.  
  
     Na **pliku** menu, kliknij przycisk **nowy** , a następnie kliknij przycisk **projektu**. W **Visual C#** folderu, wybierz opcję **Biblioteka formantów formularzy systemu Windows**.  
  
     Zaakceptuj `WindowsFormsControlLibrary1` nazwę projektu, klikając **OK**.  
  
     Domyślnie nazwa formantu .NET będzie `UserControl1`.  
  
2.  Dodawanie formantów podrzędnych z `UserControl1`.  
  
     W **przybornika**, otwórz **wszystkich formularzy systemu Windows** listy. Przeciągnij **przycisk** formant `UserControl1` powierzchnię projektu.  
  
     Dodaj również **pole tekstowe** formantu.  
  
3.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **UserControl1.Designer.cs** go otworzyć do edycji. Zmień deklaracje pole tekstowe i przycisk od `private` do `public`.  
  
4.  Skompiluj projekt.  
  
     Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC  
  
1.  Utwórz projekt aplikacji MFC.  
  
     Na **pliku** menu, kliknij przycisk **nowy** , a następnie kliknij przycisk **projektu**. W **Visual C++** folderu, wybierz opcję **aplikacji MFC**.  
  
     W **nazwa** wpisz `MFC01`. Zmień ustawienie rozwiązania na **dodać do rozwiązania**. Kliknij przycisk **OK**.  
  
     W **Kreator aplikacji MFC**, wybierz typ aplikacji **okno dialogowe na podstawie**. Zaakceptuj pozostałe domyślne ustawienia i kliknij przycisk **Zakończ**. Spowoduje to utworzenie aplikacji MFC, która okna dialogowego MFC.  
  
2.  Dodawanie formantu zastępczego do okna dialogowego MFC.  
  
     Na **widoku** menu, kliknij przycisk **widok zasobów**. W **widok zasobów**, rozwiń węzeł **okna dialogowego** folder i kliknij dwukrotnie `IDD_MFC01_DIALOG`. Zasób okna dialogowego zostanie wyświetlony w **Edytor zasobów**.  
  
     W **przybornika**, otwórz **Edytor okien dialogowych** listy. Przeciągnij **tekst statyczny** formantu zasobu okna dialogowego. **Tekst statyczny** formant będzie służyć jako symbolu zastępczego dla formantu formularzy systemu Windows .NET. Rozmiar około rozmiar formantu formularzy systemu Windows.  
  
     W **właściwości** Zmień **identyfikator** z **tekst statyczny** formant `IDC_CTRL1` i zmienić **TabStop** właściwości **True**.  
  
3.  Konfigurowanie projektu do obsługi środowiska uruchomieniowego języka wspólnego (CLR).  
  
     W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu MFC01, a następnie kliknij przycisk **właściwości**.  
  
     W **strony właściwości** okna dialogowego, w obszarze **właściwości konfiguracji**, wybierz pozycję **ogólne**. W **domyślne projektu** sekcji, ustaw **Obsługa środowisko uruchomieniowe języka wspólnego** do **obsługuje wspólnego języka środowiska uruchomieniowego (/ clr)**.  
  
     W obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** i wybierz **ogólne** węzła. Ustaw **Format informacji debugowania** do **(/Zi) baza danych programu**.  
  
     Wybierz **generowania kodu** węzła. Ustaw **włączyć minimalna ponowna kompilacja** do **nr (/ Gm-)**. Również ustawić **podstawowe Sprawdzanie czasu wykonania** do **domyślne**.  
  
     Kliknij przycisk **OK** Aby zastosować zmiany.  
  
4.  Dodaj odwołanie do formantu .NET.  
  
     W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu MFC01, a następnie kliknij przycisk **Dodaj**, **odwołania**. Na **strony właściwości**, kliknij przycisk **Dodaj nowe odwołanie**, wybierz pozycję **WindowsFormsControlLibrary1** (w obszarze **projekty** kartę) i kliknij przycisk **OK**. To spowoduje dodanie odwołania w formie [/FU](../build/reference/fu-name-forced-hash-using-file.md) — opcja kompilatora, aby program zostanie skompilowany. Również umieszcza kopię WindowsFormsControlLibrary1.dll w folderze projektu \MFC01\ tak, aby program będzie uruchamiany.  
  
5.  W pliku Stdafx.h Znajdź ten wiersz:  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     Powyżej, Dodaj następujące wiersze:  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  Dodaj kod, aby utworzyć zarządzanego formantu.  
  
     Najpierw należy zadeklarować zarządzanego formantu. W MFC01Dlg.h przejdź do deklaracji klasy okien dialogowych i Dodaj element członkowski danych kontrolki użytkownika w zakresie chronione w następujący sposób.  
  
    ```  
    class CMFC01Dlg : public CDialog  
    {  
       // ...  
       // Data member for the .NET User Control:  
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;  
    ```  
  
     Następnie zapewniać implementację zarządzanego formantu. W MFC01Dlg.cpp, w oknie dialogowym zastąpienie `CMFC01Dlg::DoDataExchange` wygenerowany przez Kreatora aplikacji MFC (nie `CAboutDlg::DoDataExchange`, która znajduje się w tym samym pliku), Dodaj następujący kod do tworzenia zarządzanego formantu i skojarzyć go z statycznych symbol zastępczy IDC_CTRL1.  
  
    ```  
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)  
    {  
       CDialog::DoDataExchange(pDX);  
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);  
    }  
    ```  
  
7.  Tworzenie i uruchamianie projektu.  
  
     W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MFC01** , a następnie kliknij przycisk **Ustaw jako projekt startowy**.  
  
     Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Na **debugowania** menu, kliknij przycisk **uruchomienie bez debugowania**. W oknie dialogowym MFC powinien być wyświetlany formantu formularzy systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Hostowanie formantu użytkownika formularza systemu Windows w oknie dialogowym MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)