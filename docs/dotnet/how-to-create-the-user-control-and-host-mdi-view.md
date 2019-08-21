---
title: 'Instrukcje: Tworzenie kontrolki użytkownika i hostowanie widoku MDI'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 634dd9c1ad2ce9199cec0dfa7ef067bd45f242f6
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630837"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Instrukcje: Tworzenie kontrolki użytkownika i hostowanie widoku MDI

W poniższych krokach przedstawiono sposób tworzenia kontrolki użytkownika .NET Framework, tworzenia kontrolki użytkownika w bibliotece klas formantów (w tym projektu biblioteki formantów systemu Windows), a następnie kompilowania projektu do zestawu. Kontrolka może być następnie używana z poziomu aplikacji MFC, która używa klas pochodnych klasy [CView](../mfc/reference/cview-class.md) i [klasy CWinFormsView](../mfc/reference/cwinformsview-class.md).

Aby uzyskać informacje na temat sposobu tworzenia kontrolki użytkownika Windows Forms i tworzenia biblioteki klas formantów, zobacz [How to: Tworzenie kontrolek](/dotnet/framework/winforms/controls/how-to-author-composite-controls)użytkownika.

> [!NOTE]
>  W niektórych przypadkach Windows Forms kontrolki, takie jak kontrolka siatki innej firmy, mogą nie zachowywać się w sposób niezawodny, gdy jest hostowany w aplikacji MFC. Zalecanym obejściem jest umieszczenie kontrolki użytkownika Windows Forms w aplikacji MFC i umieszczenie kontrolki siatki innej firmy wewnątrz kontrolki użytkownika.

W tej procedurze przyjęto założenie, że utworzono projekt biblioteki formantów Windows Forms o nazwie WindowsFormsControlLibrary1, zgodnie [z procedurą w temacie How to: Utwórz kontrolkę użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC

1. Utwórz projekt aplikacji MFC.

   W menu **plik** wybierz pozycję **Nowy**, a następnie kliknij pozycję **projekt**. W folderze  **C++ wizualizacji** wybierz pozycję **aplikacja MFC**.

   W polu **Nazwa** wprowadź `MFC02` i zmień ustawienie **rozwiązanie** na **Dodaj do rozwiązania**. Kliknij przycisk **OK**.

   W **Kreatorze aplikacji MFC**Zaakceptuj wszystkie ustawienia domyślne, a następnie kliknij przycisk **Zakończ**. Spowoduje to utworzenie aplikacji MFC z interfejsem wielu dokumentów.

1. Skonfiguruj projekt dla obsługi środowiska uruchomieniowego języka wspólnego (CLR).

   W **Eksplorator rozwiązań**kliknij prawym przyciskiem `MFC01` myszy węzeł projektu, a następnie wybierz polecenie **Właściwości** z menu kontekstowego. Zostanie wyświetlone okno dialogowe **strony właściwości** .

   W obszarze **Właściwości konfiguracji**wybierz pozycję **Ogólne**. W sekcji **wartości domyślne projektu** Ustaw **obsługę środowiska uruchomieniowego** CLR na **obsługę środowiska uruchomieniowego CLR (/CLR)** .

   W obszarze **Właściwości konfiguracji**rozwiń węzeł **CC++ /** i kliknij węzeł **Ogólne** . Ustaw **Format informacji debugowania** dla **bazy danych programu (/ZI)** .

   Kliknij węzeł **generowanie kodu** . Ustaw **opcję Włącz minimalną** ponowną kompilację na wartość **no (/GM-)** . Ustaw również **podstawowe testy środowiska uruchomieniowego** na **domyślne**.

   Kliknij przycisk **OK** , aby zastosować zmiany.

1. W obszarze *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i starszych) Dodaj następujący wiersz:

    ```
    #using <System.Windows.Forms.dll>
    ```

1. Dodaj odwołanie do kontrolki .NET.

   W **Eksplorator rozwiązań**kliknij prawym przyciskiem `MFC02` myszy węzeł projektu i wybierz polecenie **Dodaj**, **odwołania**. Na **stronie właściwości**kliknij pozycję **Dodaj nowe odwołanie**, wybierz pozycję WindowsFormsControlLibrary1 (na karcie **projekty** ), a następnie kliknij przycisk **OK**. Spowoduje to dodanie odwołania w postaci opcji kompilatora [/Fu](../build/reference/fu-name-forced-hash-using-file.md) , tak aby program skompiluje; Kopiuje także plik WindowsFormsControlLibrary1. dll do `MFC02` katalogu projektu, dzięki czemu program zostanie uruchomiony.

1. W stdafx. h Znajdź ten wiersz:

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Dodaj te wiersze powyżej:

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Zmodyfikuj klasę widoku, aby dziedziczyć z [CWinFormsView](../mfc/reference/cwinformsview-class.md).

   W MFC02View. h Zastąp wartość [CView](../mfc/reference/cview-class.md) with [CWinFormsView](../mfc/reference/cwinformsview-class.md) , aby kod pojawił się w następujący sposób:

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   Jeśli chcesz dodać dodatkowe widoki do aplikacji MDI, musisz wywołać [CWinApp:: AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) dla każdego tworzonego widoku.

1. Zmodyfikuj plik MFC02View. cpp, aby zmienić CView na CWinFormsView w makrze IMPLEMENT_DYNCREATE i mapie komunikatów i Zastąp istniejący pusty Konstruktor następującym konstruktorem:

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

   W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję MFC02 i wybierz pozycję **Ustaw jako projekt startowy**.

   Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

   W menu **debugowanie** kliknij polecenie **Uruchom bez debugowania**.

## <a name="see-also"></a>Zobacz także

[Hostowanie kontrolki użytkownika interfejsu Windows Forms jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
