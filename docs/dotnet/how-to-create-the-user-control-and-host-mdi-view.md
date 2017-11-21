---
title: "Porady: Tworzenie formantu użytkownika i hostowanie widoku MDI | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 298a08689d6c4aa69d4a52af5fad965e3e353b5c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Porady: tworzenie kontrolki użytkownika i hostowanie widoku MDI
Poniższe kroki pokazują, jak utworzyć kontrolkę użytkownika platformy .NET Framework, tworzenie kontrolki użytkownika w bibliotece klas formantu (w szczególności Projekt Biblioteka formantów systemu Windows) i następnie skompilować projektu do zestawu. Formant mogą być następnie używane z aplikacji MFC, która używa klas pochodnych [cview — klasa](../mfc/reference/cview-class.md) i [CWinFormsView klasy](../mfc/reference/cwinformsview-class.md).  
  
 Uzyskać informacji o sposobie Tworzenie formantu użytkownika formularzy systemu Windows i tworzenia biblioteki klas kontroli, zobacz [porady: tworzenie kontrolki użytkownika](/dotnet/framework/winforms/controls/how-to-author-composite-controls).  
  
> [!NOTE]
>  W niektórych przypadkach formanty formularzy systemu Windows, takich jak formantu siatki innych firm może nie działać niezawodnie w przypadku hostowania w aplikacji MFC. Obejście tego problemu zalecane jest umieszczenie formantu użytkownika formularzy systemu Windows w aplikacji MFC i innych firm formant siatki w formancie użytkownika.  
  
 W tej procedurze założono, że utworzono Projekt Biblioteka formantów formularzy systemu Windows o nazwie WindowsFormsControlLibrary1, zgodnie z procedurą w [porady: Tworzenie formantu użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC  
  
1.  Utwórz projekt aplikacji MFC.  
  
     Na **pliku** menu, wybierz opcję **nowy**, a następnie kliknij przycisk **projektu**. W **Visual C++** folderu, wybierz opcję **aplikacji MFC**.  
  
     W **nazwa** wprowadź `MFC02` i zmienić **rozwiązania** ustawienie **dodać do rozwiązania**. Kliknij przycisk **OK**.  
  
     W **Kreator aplikacji MFC**Zaakceptuj wszystkie ustawienia domyślne, a następnie kliknij przycisk **Zakończ**. Spowoduje to utworzenie aplikacji MFC z interfejsem wielu dokumentów.  
  
2.  Konfigurowanie projektu do obsługi środowiska uruchomieniowego języka wspólnego (CLR).  
  
     W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `MFC01` węzeł projektu i wybierz **właściwości** z menu kontekstowego. **Strony właściwości** zostanie wyświetlone okno dialogowe.  
  
     W obszarze **właściwości konfiguracji**, wybierz pozycję **ogólne**. W obszarze **domyślne projektu** sekcji, ustaw **Obsługa środowisko uruchomieniowe języka wspólnego** do **obsługuje wspólnego języka środowiska uruchomieniowego (/ clr)**.  
  
     W obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** i kliknij przycisk **ogólne** węzła. Ustaw **Format informacji debugowania** do **(/Zi) baza danych programu**.  
  
     Kliknij przycisk **generowania kodu** węzła. Ustaw **włączyć minimalna ponowna kompilacja** do **nr (/ Gm-)**. Również ustawić **podstawowe Sprawdzanie czasu wykonania** do **domyślne**.  
  
     Kliknij przycisk **OK** Aby zastosować zmiany.  
  
3.  W pliku stdafx.h Dodaj następujący wiersz:  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
4.  Dodaj odwołanie do formantu .NET.  
  
     W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `MFC02` węzeł projektu i wybierz **Dodaj**, **odwołania**. W **strony właściwości**, kliknij przycisk **Dodaj nowe odwołanie**, wybierz WindowsFormsControlLibrary1 (w obszarze **projekty** kartę) i kliknij przycisk **OK** . To spowoduje dodanie odwołania w formie [/FU](../build/reference/fu-name-forced-hash-using-file.md) — opcja kompilatora, aby program zostanie skompilowany; kopiuje również WindowsFormsControlLibrary1.dll do `MFC02` projektu katalogu, dzięki czemu program będzie uruchamiany.  
  
5.  W pliku stdafx.h Znajdź ten wiersz:  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     Dodaj następujące wiersze powyżej:  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  Modyfikowanie klasy widok, tak, aby dziedziczyła ona z [CWinFormsView](../mfc/reference/cwinformsview-class.md).  
  
     W MFC02View.h, Zastąp [CView](../mfc/reference/cview-class.md) z [CWinFormsView](../mfc/reference/cwinformsview-class.md) tak, aby kod wygląda następująco:  
  
    ```  
    class CMFC02View : public CWinFormsView  
    {  
    };  
    ```  
  
     Jeśli chcesz dodać do aplikacji MDI dodatkowe widoki, należy wywołać [CWinApp::AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) dla każdego tworzenia widoku.  
  
7.  Zmodyfikuj plik MFC02View.cpp Zmień CView CWinFormsView w mapie implement_dyncreate — makro i komunikat i Zastąp istniejące pustego konstruktora konstruktora pokazano poniżej:  
  
    ```  
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)  
  
    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)   
    {  
    }  
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)  
    //leave existing body as is  
    END_MESSAGE_MAP()  
    ```  
  
8.  Tworzenie i uruchamianie projektu.  
  
     W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy MFC02 i wybierz **Ustaw jako projekt startowy**.  
  
     Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Na **debugowania** menu, kliknij przycisk **uruchomienie bez debugowania**.  
  
## <a name="see-also"></a>Zobacz też  
 [Hostowanie formantu użytkownika formularzy systemu Windows jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)