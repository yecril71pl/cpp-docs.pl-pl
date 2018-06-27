---
title: 'Wskazówki: Używanie MFC nowe powłoki kontrolki | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: f349c955724b66ccc8cb1b19fc826ca0b8354258
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951952"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Wskazówki: używanie nowych formantów powłoki MFC
W tym przewodniku utworzysz aplikację, która jest podobny Eksploratora plików. Utworzysz okna, który zawiera dwa okienka. W okienku po lewej stronie będzie zawierać [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) obiekt, który wyświetla pulpitu w hierarchiczny widok. Okienku po prawej stronie będzie zawierać [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) który zawiera pliki w folderze, który wybrano w okienku po lewej stronie.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku przyjęto założenie, że po skonfigurowaniu [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] do używania **ogólne ustawienia środowiska deweloperskiego**. Jeśli używane są ustawienia różnych programowanie, niektóre [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] systemu windows, których używamy w tym przewodniku mogą nie być wyświetlane domyślnie.  
  
### <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Aby utworzyć nową aplikację MFC za pomocą Kreatora aplikacji MFC  
  
1.  Użyj **Kreator aplikacji MFC** do utworzenia nowej aplikacji MFC. Aby uruchomić kreatora, z **pliku** menu wybierz opcję **nowy**, a następnie wybierz **projektu**. **Nowy projekt** wyświetli się okno dialogowe.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C++** w węźle **typy projektów** okienka, a następnie wybierz **MFC**. Następnie w **szablony** okienku wybierz **aplikacji MFC**. Wpisz nazwę projektu, takie jak *MFCShellControls* i kliknij przycisk **OK**. **Kreator aplikacji MFC** będą wyświetlane.  
  
3.  W **Kreator aplikacji MFC** okno dialogowe, kliknij przycisk **dalej**. **Typu aplikacji** pojawi się okienko.  
  
4.  Na **typu aplikacji** okienku w obszarze **typu aplikacji**, wyczyść **dokumenty na kartach** opcji. Następnie wybierz pozycję **pojedynczego dokumentu** i wybierz **wsparcie dla architektury dokument/widok**. W obszarze **projektu styl**, wybierz pozycję **programu Visual Studio**i z **styl wizualny i kolory** listy rozwijanej wybierz listy **Office 2007 (motyw niebieski)**. Pozostaw inne opcje są one. Kliknij przycisk **dalej** do wyświetlenia **Obsługa dokumentów złożonych** okienka.  
  
5.  Na **Obsługa dokumentów złożonych** okienku wybierz **Brak**. Kliknij przycisk **dalej** do wyświetlenia **ciągi szablonu dokumentu** okienka.  
  
6.  Nie należy wprowadzać żadnych zmian do **ciągi szablonu dokumentu** okienka. Kliknij przycisk **dalej** do wyświetlenia **obsługi bazy danych** okienka.  
  
7.  Na **obsługi bazy danych** okienku wybierz **Brak** , ponieważ ta aplikacja nie używa bazy danych. Kliknij przycisk **dalej** do wyświetlenia **funkcje interfejsu użytkownika** okienka.  
  
8.  Na **funkcje interfejsu użytkownika** okienka, upewnij się, że **użyj paska menu i paska narzędzi** opcja jest zaznaczona. Pozostaw inne opcje są one. Kliknij przycisk **dalej** do wyświetlenia **funkcje zaawansowane** okienka.  
  
9. Na **funkcje zaawansowane** okienku w obszarze **zaawansowane funkcje**, wybierz tylko **formantów ActiveX** i **wspólnej manifestu kontroli**. W obszarze **zaawansowanego okienka ramki**, wybierz tylko **okienka nawigacji** opcji. Spowoduje to utworzenie w okienku z lewej strony okna z `CMFCShellTreeCtrl` już osadzonych. Kliknij przycisk **dalej** do wyświetlenia **wygenerowane klasy** okienka.  
  
10. Nie zamierzamy wprowadzać żadnych zmian do **wygenerowane klasy** okienka. W związku z tym kliknij **Zakończ** do utworzenia nowego projektu MFC.  
  
11. Sprawdź, czy aplikacja została pomyślnie utworzona tworzenia i uruchamiania go. Do skompilowania aplikacji, z **kompilacji** menu wybierz opcję **Kompiluj rozwiązanie**. Aplikacja utworzy pomyślnie, uruchom aplikację wybierając **Rozpocznij debugowanie** z **debugowania** menu.  
  
     Kreator automatycznie tworzy aplikację, która ma paska menu standardowego, standardowym pasku narzędzi, pasek stanu standardowe i paska Outlook z lewej strony okna z **folderów** widoku i **kalendarza** widoku .  
  
### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Aby dodać kontrolki listy powłoki do widoku dokumentu  
  
1.  W tej sekcji dodasz wystąpienia `CMFCShellListCtrl` do widoku utworzony przez kreatora. Otwórz plik nagłówka widoku, klikając MFCShellControlsView.h w **Eksploratora rozwiązań**.  
  
     Zlokalizuj `#pragma once` dyrektywy w górnej części pliku nagłówka. Natychmiast underneath go Dodaj ten kod, aby uwzględnić plik nagłówka `CMFCShellListCtrl`:  
  
 ```  
    #include <afxShellListCtrl.h>  
 ```  
  
     Teraz dodać zmiennej członka typu `CMFCShellListCtrl`. Po pierwsze Znajdź poniższy komentarz w pliku nagłówka:  
  
 ``` 
    // Generated message map functions  
 ```  
  
     Natychmiast powyżej tego komentarza, Dodaj ten kod:  
  
 ```  
    private: 
    CMFCShellListCtrl m_wndList;  
 ```  
  
2.  **Kreator aplikacji MFC** już utworzone `CMFCShellTreeCtrl` obiektu w `CMainFrame` klasy, ale jest chroniony element członkowski. Firma Microsoft będą uzyskiwać dostęp do tego obiektu później. W związku z tym teraz utworzyć metody dostępu dla niego. Otwórz plik nagłówka MainFrm.h, klikając go w **Eksploratora rozwiązań**. Znajdź następujący komentarza:  
  
 ``` 
    // Attributes  
 ```  
  
     Natychmiast w nim, należy dodać następujące deklaracji metody:  
  
 ```  
    public: 
    CMFCShellTreeCtrl& GetShellTreeCtrl();
 ```  
  
     Następnie otwórz plik źródłowy MainFrm.cpp przez dwukrotne kliknięcie w **Eksploratora rozwiązań**. W dolnej części tego pliku Dodaj następującą definicję metody:  
  
 ```  
    CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()  
    {  
        return m_wndTree;  
    }  
 ```  
  
3.  Teraz możemy zaktualizować `CMFCShellControlsView` klasy do obsługi komunikatów systemu windows WM_CREATE. Otwórz plik nagłówka MFCShellControlsView.h i kliknij w tym wierszu kodu:  
  
 ```  
    class CMFCShellControlsView : public CView  
 ```  
  
     Następnie w **właściwości** okna, kliknij przycisk **wiadomości** ikony. Przewiń w dół do momentu znalezienia WM_CREATE wiadomości. Wybierz z listy rozwijanej obok WM_CREATE,  *\<Dodaj > OnCreate*. Tworzy program obsługi komunikatów w firmie Microsoft i automatycznie aktualizuje mapy komunikatów MFC.  
  
     W `OnCreate` metody teraz utworzymy naszych `CMFCShellListCtrl` obiektu. Znajdź `OnCreate` definicji metody w MFCShellControlsView.cpp plik źródłowy i zastąp jego implementacja następującym kodem:  
  
 ```  
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)  
    {  
        if (CView::OnCreate(lpCreateStruct) == -1)  
            return -1;  
     
        CRect rectDummy (0, 0, 0, 0);
    
        m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT, rectDummy, this, 1);
    
        return 0;  
    }  
 ```  
  
4.  Powtórz poprzedni krok, ale dla WM_SIZE komunikatu. Spowoduje to widoku aplikacji narysowania zawsze, gdy użytkownik zmienia rozmiar okna aplikacji. Zastąp definicję `OnSize` metodę z następującym kodem:  
  
 ```  
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)  
    {  
        CView::OnSize(nType, cx, cy);
    
        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy, SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }  
 ```  
  
5.  Ostatnim krokiem jest podłączenie `CMFCShellTreeCtrl` i `CMFCShellListCtrl` obiektów przy użyciu [CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) metody. Po wywołaniu tej metody `CMFCShellListCtrl` zostanie automatycznie wyświetlona zawartość elementu wybranego w `CMFCShellTreeCtrl`. Spowoduje to wykonanie `OnActivateView` metodę, która zostanie zastąpiona z [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview).  
  
     W pliku nagłówka MFCShellControlsView.h wewnątrz `CMFCShellControlsView` deklaracji klasy, Dodaj następujące deklaracji metody:  
  
 ```  
    protected: 
    virtual void OnActivateView(BOOL bActivate, CView* pActivateView, CView* pDeactiveView);
 ```  
  
     Następnie dodaj definicję dla tej metody w pliku źródłowym MFCShellControlsView.cpp:  
  
 ```  
    void CMFCShellControlsView::OnActivateView(BOOL bActivate, CView* pActivateView, CView* pDeactiveView)   
    {  
        if (bActivate&& AfxGetMainWnd() != NULL)  
        {  
            ((CMainFrame*)AfxGetMainWnd())->GetShellTreeCtrl().SetRelatedList(&m_wndList);
        }  
     
        CView::OnActivateView(bActivate, pActivateView, pDeactiveView);
    }  
 ```  
  
     Ponieważ wywołania metody `CMainFrame` klasy, możemy dodać `#include` dyrektywy w górnej części pliku źródłowego MFCShellControlsView.cpp:  
  
 ```  
    #include "MainFrm.h"  
 ```  
  
6.  Sprawdź, czy aplikacja została pomyślnie utworzona tworzenia i uruchamiania go. Do skompilowania aplikacji, z **kompilacji** menu wybierz opcję **Kompiluj rozwiązanie**. Jeśli aplikacja tworzy się pomyślnie, uruchom go, wybierając **Rozpocznij debugowanie** z **debugowania** menu.  
  
     Powinien zostać wyświetlony szczegóły elementu wybranego w `CMFCShellTreeCtrl` w okienku widoku. Po kliknięciu węzła w `CMFCShellTreeCtrl`, `CMFCShellListCtrl` zostanie automatycznie zaktualizowana. Podobnie jeśli dwukrotnie folder w `CMFCShellListCtrl`, `CMFCShellTreeCtrl` powinien zostać automatycznie zaktualizowany.  
  
     Kliknij prawym przyciskiem myszy dowolny element w drzewie lub w formancie listy. Należy pamiętać, możesz uzyskać tego samego menu kontekstowego tak, jakby były używane rzeczywiste Eksploratora plików.  
  
## <a name="next-steps"></a>Następne kroki  
  
-   Kreator paska Outlook utworzone za pomocą obu **folderów** okienko i **kalendarza** okienka. Prawdopodobnie nie sprawia, że warto mieć **kalendarza** okienka w oknie Eksploratora. W związku z tym teraz usunąć okienka.  
  
-   `CMFCShellListCtrl` Obsługuje wyświetlanie plików w różnych trybach, takich jak **duże ikony**, **małych ikon**, **listy**, i **szczegóły**. Aktualizuj aplikację, aby zaimplementować tę funkcję. Wskazówka: zobacz [Visual C++ — przykłady](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodniki](../mfc/walkthroughs-mfc.md)
