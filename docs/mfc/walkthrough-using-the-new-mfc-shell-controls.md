---
title: 'Przewodnik: Używanie nowych MFC powłoki kontrolki | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81925cfa31c394a1b307a184388fb0d331d31fdd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432493"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Wskazówki: używanie nowych formantów powłoki MFC

W tym instruktażu utworzysz aplikację, podobny Eksploratora plików. Utworzysz okno które zawiera dwa okienka. W okienku po lewej stronie będzie zawierać [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) obiekt, który wyświetla hierarchiczny widok pulpitu. W okienku po prawej stronie będzie zawierać [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) przedstawiająca pliki w folderze, który wybrano w okienku po lewej stronie.

## <a name="prerequisites"></a>Wymagania wstępne

W tym przewodniku przyjęto założenie, że po skonfigurowaniu programu Visual Studio do użycia **ogólnych ustawieniach projektowych**. Jeśli używasz ustawienia tworzenia różnych niektóre okna programu Visual Studio, których używa w tym przewodniku mogą nie być wyświetlane domyślnie.

### <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Aby utworzyć nową aplikację MFC przy użyciu Kreatora aplikacji MFC

1. Użyj **Kreator aplikacji MFC** do utworzenia nowej aplikacji MFC. Aby uruchomić kreatora z **pliku** menu wybierz opcję **nowy**, a następnie wybierz pozycję **projektu**. **Nowy projekt** pojawi się okno dialogowe.

2. W **nowy projekt** okna dialogowego rozwiń **Visual C++** w węźle **typów projektów** okienka, a następnie wybierz **MFC**. Następnie w **szablony** okienku wybierz **aplikacji MFC**. Wpisz nazwę dla projektu, takie jak `MFCShellControls` i kliknij przycisk **OK**. **Kreator aplikacji MFC** będą wyświetlane.

3. W **Kreator aplikacji MFC** okno dialogowe, kliknij przycisk **dalej**. **Typ aplikacji** zostanie wyświetlone okienko.

4. Na **typ aplikacji** okienku w obszarze **typ aplikacji**, wyczyść **dokumenty z zakładkami** opcji. Następnie wybierz pozycję **pojedynczego dokumentu** i wybierz **Obsługa architektury dokument/widok**. W obszarze **projektu styl**, wybierz opcję **programu Visual Studio**i z **styl wizualny i kolory** listy rozwijanej listy wybierz **Office 2007 (motyw niebieski)**. Pozostaw inne opcje, ponieważ są one. Kliknij przycisk **dalej** do wyświetlenia **Obsługa dokumentów złożonych** okienka.

5. Na **Obsługa dokumentów złożonych** okienku wybierz **Brak**. Kliknij przycisk **dalej** do wyświetlenia **ciągi szablonu dokumentu** okienka.

6. Nie wprowadzaj żadnych zmian w **ciągi szablonu dokumentu** okienka. Kliknij przycisk **dalej** do wyświetlenia **obsługi bazy danych** okienka.

7. Na **obsługi bazy danych** okienku wybierz **Brak** , ponieważ ta aplikacja nie korzysta z bazy danych. Kliknij przycisk **dalej** do wyświetlenia **funkcje interfejsu użytkownika** okienka.

8. Na **funkcje interfejsu użytkownika** okienka, upewnij się, że **użyj paska menu i paska narzędzi** opcja jest zaznaczona. Pozostaw inne opcje, ponieważ są one. Kliknij przycisk **dalej** do wyświetlenia **funkcje zaawansowane** okienka.

9. Na **funkcje zaawansowane** okienku w obszarze **zaawansowane funkcje**, wybierz tylko **formantów ActiveX** i **manifestu wspólnej kontroli**. W obszarze **zaawansowane okienka ramki**, wybierz tylko **okienka nawigacji** opcji. Spowoduje to pracę kreatora, aby utworzyć w okienku po lewej stronie okna z `CMFCShellTreeCtrl` już osadzonych. Kliknij przycisk **dalej** do wyświetlenia **wygenerowane klasy** okienka.

10. Nie zamierzamy wprowadzić zmiany w **wygenerowane klasy** okienka. W związku z tym, kliknij przycisk **Zakończ** do utworzenia Twojego nowego projektu MFC.

11. Sprawdź, czy aplikacja została pomyślnie utworzona, tworząc i uruchamiając go. Aby skompilować aplikację, z **kompilacji** menu wybierz opcję **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom aplikację, wybierając **Rozpocznij debugowanie** z **debugowania** menu.

   Kreator automatycznie tworzy aplikację, która ma standardowy pasek menu, standardowy pasek narzędzi, pasek stanu standardowe i paska Outlook po lewej stronie okna z **folderów** widoku i **kalendarza** widoku .

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Aby dodać formant listy powłoki do widoku dokumentu

1. W tej sekcji dodasz wystąpienie `CMFCShellListCtrl` do widoku, utworzony przez kreatora. Otwórz plik nagłówka w widoku, klikając dwukrotnie MFCShellControlsView.h w **Eksploratora rozwiązań**.

   Znajdź `#pragma once` dyrektywę w górnej części pliku nagłówka. Natychmiast poniżej go Dodaj ten kod, aby uwzględnić plik nagłówka dla `CMFCShellListCtrl`:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Teraz Dodaj zmienną składową typu `CMFCShellListCtrl`. Po pierwsze Znajdź poniższy komentarz w pliku nagłówka:

   ```cpp
   // Generated message map functions
   ```

   Bezpośrednio nad tym komentarzem, Dodaj następujący kod:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

2. **Kreator aplikacji MFC** utworzonym `CMFCShellTreeCtrl` obiektu `CMainFrame` klasy, ale jest chroniony element członkowski. Firma Microsoft będzie później dostęp, ten obiekt. Dlatego teraz utworzyć metody dostępu dla niego. Otwórz plik nagłówkowy MainFrm.h, klikając go dwukrotnie **Eksploratora rozwiązań**. Znajdź poniższy komentarz:

   ```cpp
   // Attributes
   ```

   Bezpośrednio pod nim, dodaj następującą deklarację metody:

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   Następnie otwórz plik źródłowy MainFrm.cpp, klikając go dwukrotnie **Eksploratora rozwiązań**. W dolnej części tego pliku Dodaj następującą definicję metody:

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

3. Teraz możemy zaktualizować `CMFCShellControlsView` klasy do obsługi **WM_CREATE** komunikatów systemu windows. Otwórz plik nagłówkowy MFCShellControlsView.h i kliknąć ten wiersz kodu:

    ```cpp
    class CMFCShellControlsView : public CView
    ```

   Następnie w **właściwości** okna, kliknij przycisk **wiadomości** ikony. Przewiń w dół, aż znajdziesz **WM_CREATE** wiadomości. Z listy rozwijanej liście obok **WM_CREATE**, wybierz opcję  **\<Dodaj > OnCreate**. Tworzy program obsługi komunikatów dla nas i automatycznie aktualizuje mapy komunikatów MFC.

   W `OnCreate` metoda teraz utworzymy naszych `CMFCShellListCtrl` obiektu. Znajdź `OnCreate` definicji metody w MFCShellControlsView.cpp pliku źródłowego i zastąp jego implementacja następującym kodem:

    ```cpp
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)
    {
        if (CView::OnCreate(lpCreateStruct) == -1)
            return -1;

        CRect rectDummy (0, 0, 0, 0);

        m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT,
            rectDummy, this, 1);

        return 0;
    }
    ```

4. Powtórz poprzedni krok, ale w przypadku **WM_SIZE** wiadomości. To spowoduje, że widok aplikacji, aby być narysowany ponownie, gdy użytkownik zmieni rozmiar okna aplikacji. Zastąp definicję dla `OnSize` metoda następującym kodem:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

5. Ostatni krok polega na połączeniu `CMFCShellTreeCtrl` i `CMFCShellListCtrl` obiektów przy użyciu [CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) metody. Po wywołaniu tej metody `CMFCShellListCtrl` zostanie automatycznie wyświetlona zawartość elementu wybranego w `CMFCShellTreeCtrl`. Zrobimy to `OnActivateView` metody, która zostanie zastąpiona z [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   W pliku nagłówkowym MFCShellControlsView.h wewnątrz `CMFCShellControlsView` deklaracji klasy, dodaj następującą deklarację metody:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   Następnie dodaj definicję dla tej metody w pliku źródłowym MFCShellControlsView.cpp:

    ```cpp
    void CMFCShellControlsView::OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView)
    {
        if (bActivate&& AfxGetMainWnd() != NULL)
        {
            ((CMainFrame*)AfxGetMainWnd())->GetShellTreeCtrl().SetRelatedList(&m_wndList);
        }

        CView::OnActivateView(bActivate,
            pActivateView,
            pDeactiveView);
    }
    ```

   Ponieważ wywołania metody z `CMainFrame` klasy, możemy dodać `#include` dyrektywę w górnej części pliku źródłowego MFCShellControlsView.cpp:

    ```cpp
    #include "MainFrm.h"
    ```

6. Sprawdź, czy aplikacja została pomyślnie utworzona, tworząc i uruchamiając go. Aby skompilować aplikację, z **kompilacji** menu wybierz opcję **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom go, wybierając **Rozpocznij debugowanie** z **debugowania** menu.

   Zostaną wyświetlone szczegóły dotyczące elementu zaznaczonego w `CMFCShellTreeCtrl` w okienku widoku. Po kliknięciu węzła w `CMFCShellTreeCtrl`, `CMFCShellListCtrl` zostaną automatycznie zaktualizowane. Podobnie jeśli klikniesz dwukrotnie folder, w `CMFCShellListCtrl`, `CMFCShellTreeCtrl` powinny być aktualizowane automatycznie.

   Kliknij prawym przyciskiem myszy dowolny element w drzewie lub kontrolki listy. Należy pamiętać, Pobierz z tego samego menu kontekstowego, tak, jakby były używane rzeczywiste Eksploratora plików.

## <a name="next-steps"></a>Następne kroki

- Kreator utworzył paska Outlook zarówno **folderów** okienka i **kalendarza** okienka. Jego prawdopodobnie nie ma sensu ma **kalendarza** okienka w oknie Eksploratora. Dlatego teraz usunąć okienka.

- `CMFCShellListCtrl` Obsługuje wyświetlanie plików w różnych trybach, takich jak **duże ikony**, **małe ikony**, **listy**, i **szczegóły**. Zaktualizuj aplikację w celu zaimplementowania tej funkcji. Wskazówka: zobacz [przykłady Visual C++](../visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz także

[Przewodniki](../mfc/walkthroughs-mfc.md)
