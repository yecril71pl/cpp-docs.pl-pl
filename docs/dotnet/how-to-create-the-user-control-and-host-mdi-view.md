---
title: 'Instrukcje: Tworzenie kontrolki użytkownika i hostowanie widoku MDI'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 7d535fce47be5504f6f521cda1267344206287da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387438"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Instrukcje: Tworzenie kontrolki użytkownika i hostowanie widoku MDI

Poniższe kroki pokazują jak utworzyć formant użytkownika .NET Framework, tworzenie kontrolki użytkownika w bibliotece klas formantów (w szczególności Projekt Biblioteka formantów Windows) i następnie skompilować projekt w zespół. Formant może być bezpiecznie spożywane z aplikacji MFC, która używa klas pochodzących od [CView Class](../mfc/reference/cview-class.md) i [klasa CWinFormsView](../mfc/reference/cwinformsview-class.md).

Aby uzyskać informacje o tym, jak utworzyć formant użytkownika interfejsu Windows Forms i utworzyć bibliotekę klas formantów, zobacz [jak: Tworzenie kontrolki użytkownika](/dotnet/framework/winforms/controls/how-to-author-composite-controls).

> [!NOTE]
>  W niektórych przypadkach formanty Windows Forms, takie jak formant siatki innych firm mogą nie zachowywać się niezawodnie w przypadku hostowania w aplikacji MFC. Zalecaną praktyką jest umieszczenie kontrolki użytkownika formularzy Windows w aplikacji MFC i umieszczenie kontrolki siatki innych firm w kontrolce użytkownika.

W tej procedurze założono, że utworzono Projekt Biblioteka formantów systemu Windows Forms o nazwie WindowsFormsControlLibrary1, zgodnie z procedurą w [jak: Tworzenie kontrolki użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC

1. Utwórz projekt aplikacji MFC.

   Na **pliku** menu, wybierz opcję **New**, a następnie kliknij przycisk **projektu**. W **Visual C++** folderu, wybierz **aplikacji MFC**.

   W **nazwa** wprowadź `MFC02` i zmień **rozwiązania** ustawienie **Dodaj do rozwiązania**. Kliknij przycisk **OK**.

   W **Kreator aplikacji MFC**Zaakceptuj wszystkie ustawienia domyślne, a następnie kliknij przycisk **Zakończ**. Tworzy to aplikację MFC z interfejsem wielu dokumentów.

1. Konfigurowanie projektu dla obsługi środowiska uruchomieniowego języka wspólnego (CLR).

   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `MFC01` węzła projektu, a następnie wybierz **właściwości** z menu kontekstowego. **Stron właściwości** pojawi się okno dialogowe.

   W obszarze **właściwości konfiguracji**, wybierz opcję **ogólne**. W obszarze **domyślne wartości projektu** sekcji, ustaw **Obsługa środowiska uruchomieniowego języka wspólnego** do **wsparcie (/ clr)**.

   W obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** i kliknij przycisk **ogólne** węzła. Ustaw **Format informacji o debugowaniu** do **(/Zi) baza danych programu**.

   Kliknij przycisk **generowania kodu** węzła. Ustaw **Włącz minimalną ponowną kompilację** do **nr (/ Gm-)**. Również ustawić **podstawowe sprawdzenia środowiska uruchomieniowego** do **domyślne**.

   Kliknij przycisk **OK** Aby zastosować zmiany.

1. W pliku stdafx.h należy dodać następujący wiersz:

    ```
    #using <System.Windows.Forms.dll>
    ```

1. Dodaj odwołanie do formantu .NET.

   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `MFC02` węzeł projektu i wybierz pozycję **Dodaj**, **odwołania**. W **strona właściwości**, kliknij przycisk **Dodaj nowe odwołanie**, zaznacz pozycję WindowsFormsControlLibrary1 (w obszarze **projektów** karty) i kliknij przycisk **OK** . Dodaje to odwołanie w formie [/FU](../build/reference/fu-name-forced-hash-using-file.md) — opcja kompilatora tak, aby program został skompilowany; kopiuje również WindowsFormsControlLibrary1.dll do `MFC02` katalogu projektu, dzięki czemu program będzie uruchamiany.

1. W pliku stdafx.h Znajdź ten wiersz:

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Dodaj następujące wiersze powyżej:

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Zmodyfikuj widok klasy, tak aby dziedziczył z [CWinFormsView](../mfc/reference/cwinformsview-class.md).

   W MFC02View.h, Zastąp [CView](../mfc/reference/cview-class.md) z [CWinFormsView](../mfc/reference/cwinformsview-class.md) tak, aby kod wygląda następująco:

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   Jeśli chcesz dodać dodatkowe widoki do aplikacji MDI, trzeba będzie wywołać [CWinApp::AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) dla każdego widoku tworzonego.

1. Zmodyfikuj plik MFC02View.cpp, aby zmienić element CView na CWinFormsView w makrze IMPLEMENT_DYNCREATE i mapy komunikatów i Zastąp istniejący pusty konstruktor konstruktorem pokazanym poniżej:

    ```
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)

    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)
    {
    }
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)
    //leave existing body as is
    END_MESSAGE_MAP()
    ```

1. Skompiluj i uruchom projekt.

   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy pozycję MFC02 i wybierz **Ustaw jako projekt startowy**.

   Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

   Na **debugowania** menu, kliknij przycisk **Uruchom bez debugowania**.

## <a name="see-also"></a>Zobacz także

[Hostowanie kontrolki użytkownika interfejsu Windows Forms jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
