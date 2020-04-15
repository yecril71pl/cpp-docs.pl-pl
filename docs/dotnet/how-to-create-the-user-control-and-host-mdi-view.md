---
title: 'Porady: tworzenie formantu użytkownika i hostowanie widoku MDI'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 72501ba32d3b8b9a5c5fd8dd0c56f0628642b147
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374469"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Porady: tworzenie formantu użytkownika i hostowanie widoku MDI

Poniższe kroki pokazują, jak utworzyć formant użytkownika platformy .NET Framework, utworzyć formant użytkownika w bibliotece klas sterowania (w szczególności projekt biblioteki sterowania systemu Windows), a następnie skompilować projekt w zestawie. Formant może być następnie używany z aplikacji MFC, która używa klas pochodzących z [CView Class](../mfc/reference/cview-class.md) i [CWinFormsView Class](../mfc/reference/cwinformsview-class.md).

Aby uzyskać informacje dotyczące tworzenia formantu użytkownika formularzy systemu Windows i tworzenia biblioteki klas kontrolnych, zobacz [Jak: Tworzenie formantów użytkownika](/dotnet/framework/winforms/controls/how-to-author-composite-controls).

> [!NOTE]
> W niektórych przypadkach formantów windows forms, takich jak formant siatki innej firmy, może nie zachowywać się niezawodnie, gdy hostowane w aplikacji MFC. Zalecane obejście jest umieszczenie formantu użytkownika formularzy systemu Windows w aplikacji MFC i umieszczenie formantu grid innej firmy wewnątrz formantu użytkownika.

W tej procedurze przyjęto założenie, że utworzono projekt biblioteki formantów formularzy systemu Windows o nazwie WindowsFormsControlLibrary1, zgodnie z procedurą opisaną w temacie [Jak: Tworzenie formantu użytkownika i hosta w oknie dialogowym](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

### <a name="to-create-the-mfc-host-application"></a>Aby utworzyć aplikację hosta MFC

1. Utwórz projekt aplikacji MFC.

   W menu **Plik** wybierz polecenie **Nowy**, a następnie kliknij polecenie **Projekt**. W folderze **Visual C++** wybierz pozycję **Aplikacja MFC**.

   W polu **Nazwa** `MFC02` wprowadź i zmień ustawienie **Rozwiązanie** na **Dodaj do rozwiązania**. Kliknij przycisk **OK**.

   W **Kreatorze aplikacji MFC**zaakceptuj wszystkie wartości domyślne, a następnie kliknij przycisk **Zakończ**. Spowoduje to utworzenie aplikacji MFC z interfejsem wielu dokumentów.

1. Skonfiguruj projekt dla obsługi środowiska wykonawczego języka wspólnego (CLR).

   W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł `MFC01` projektu i wybierz polecenie **Właściwości** z menu kontekstowego. Zostanie wyświetlone okno dialogowe **Strony właściwości.**

   W obszarze **Właściwości konfiguracji**wybierz pozycję **Ogólne**. W sekcji **Domyślne projekt** ustaw **obsługę wspólnego środowiska uruchomieniowego języka** na obsługę środowiska **uruchomieniowego języka wspólnego (/clr).**

   W obszarze **Właściwości konfiguracji**rozwiń węzeł **C/C++** i kliknij węzeł **Ogólne.** Ustaw **format informacji debugowania** na **baza danych programu (/Zi)**.

   Kliknij węzeł **Generowanie kodu.** Ustaw **włącz minimalną przebudowę** na **Nie (/Gm-)**. Ustaw również **podstawowe sprawdzanie środowiska uruchomieniowego** na **domyślne**.

   Kliknij **przycisk OK,** aby zastosować zmiany.

1. W *programie pch.h* (*stdafx.h* w programie Visual Studio 2017 i wcześniejszych) dodaj następujący wiersz:

    ```
    #using <System.Windows.Forms.dll>
    ```

1. Dodaj odwołanie do formantu .NET.

   W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł `MFC02` projektu i wybierz polecenie **Dodaj**, **Odwołania**. Na **stronie Właściwości**kliknij pozycję **Dodaj nowe odwołanie**, wybierz pozycję WindowsFormsControlLibrary1 (w zakładce **Projekty)** i kliknij przycisk **OK**. Spowoduje to dodanie odwołania w postaci opcji kompilatora [/FU,](../build/reference/fu-name-forced-hash-using-file.md) dzięki czemu program zostanie skompilowany; kopiuje również windowsformsControlLibrary1.dll `MFC02` do katalogu projektu, dzięki czemu program zostanie uruchomiony.

1. W stdafx.h, znaleźć tę linię:

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Dodaj te wiersze nad nim:

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Zmodyfikuj klasę widoku tak, aby była dziedziczona z [programu CWinFormsView](../mfc/reference/cwinformsview-class.md).

   W MFC02View.h, zamień [CView](../mfc/reference/cview-class.md) z [CWinFormsView](../mfc/reference/cwinformsview-class.md) tak, aby kod pojawia się w następujący sposób:

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   Jeśli chcesz dodać dodatkowe widoki do aplikacji MDI, musisz wywołać [CWinApp::AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) dla każdego utworzonego widoku.

1. Zmodyfikuj plik MFC02View.cpp, aby zmienić CView na CWinFormsView w IMPLEMENT_DYNCREATE makra i mapy komunikatów i zastąp istniejący pusty konstruktor konstruktorem pokazanym poniżej:

    ```
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)

    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)
    {
    }
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)
    //leave existing body as is
    END_MESSAGE_MAP()
    ```

1. Tworzenie i uruchamianie projektu.

   W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy pozycję MFC02 i wybierz polecenie **Ustaw jako projekt startowy**.

   W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

   W menu **Debugowanie** kliknij przycisk **Start bez debugowania**.

## <a name="see-also"></a>Zobacz też

[Hostowanie kontrolki użytkownika interfejsu Windows Forms jako widoku MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
