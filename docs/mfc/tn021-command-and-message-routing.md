---
title: 'Routing TN021: Poleceń i komunikatów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.routing
dev_langs:
- C++
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a1061f4a7d4394cb84c26514795c406f78146df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384959"
---
# <a name="tn021-command-and-message-routing"></a>TN021: routing poleceń i komunikatów
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga opisano architekturę routingu i wysyłania polecenia, a także Tematy zaawansowane w oknie ogólnych komunikatów routingu.  
  
 Zapoznaj się Visual C++ szczegółowe ogólne informacje dotyczące architektury opisanych tutaj, szczególnie różnicy między Windows komunikaty powiadomień dotyczących formantu karty i poleceń. Ta uwaga zakłada znajomości problemy opisane w dokumentacji drukowanej i dotyczy tylko tematy bardzo zaawansowane.  
  
## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Routing poleceń i wysyłania MFC 1.0 z MFC 2.0 rozwoju środowisko funkcji architektury  
 System Windows ma **WM_COMMAND** komunikat, który jest przeciążone w celu zapewnienia powiadomienia polecenia menu, klawisze skrótów i powiadomień dotyczących formantów okna dialogowego.  
  
 MFC 1.0 oparty na który nieco zezwalając programem obsługi (na przykład "OnFileNew") **CWnd** klasy do jest wywoływana w odpowiedzi na określony **WM_COMMAND**. Jest zmiana koloru wraz ze strukturą danych o nazwie mapy komunikatów i powoduje mechanizm bardzo miejsca sprawności polecenia.  
  
 MFC 1.0 w nim również podane dodatkowe funkcje do oddzielania powiadomień dotyczących formantów z komunikaty poleceń. Polecenia są reprezentowane przez identyfikator 16-bitowych, czasami znana jako identyfikatora polecenia. Poleceń zazwyczaj rozpoczyna się od **cframewnd —** (to znaczy menu wybierz opcję lub przetłumaczonego akceleratora) i pobrać kierowane do różnych innych okien.  
  
 MFC 1.0 używany routing poleceń w ograniczonym znaczeniu dla implementacji interfejsu dokumentu wielu (MDI). (Ramki okna MDI delegować poleceń, aby jego aktywne okno potomne MDI).  
  
 Ta funkcja została uogólnione i rozszerzony w MFC 2.0, aby zezwalać na polecenia, które mają być obsługiwane przez większej liczby obiektów (nie tylko obiektów okien). Zapewnia jeden formalny i rozszerzalnej architektury dla routingu wiadomości i ponownie używa polecenia docelowy routingu, nie tylko obsługi poleceń, ale też aktualizowanie obiektów interfejsu użytkownika (takich jak elementy menu i przycisków paska narzędzi) w celu uwzględnienia bieżącej dostępności polecenia .  
  
## <a name="command-ids"></a>Identyfikatory poleceń  
 Aby uzyskać informacje o poleceniu routingu i proces wiązania, zobacz Visual C++. [20 Uwaga techniczna](../mfc/tn020-id-naming-and-numbering-conventions.md) zawiera informacje na temat nazewnictwa identyfikator.  
  
 Używamy ogólnego prefiksu "ID_" dla identyfikatorów poleceń. Identyfikatory poleceń są > = 0x8000. Pasek komunikatów wiersza lub stan wyświetli ciąg opisu polecenia, jeśli istnieje zasób STRINGTABLE o takich samych identyfikatorów, jako identyfikator polecenia.  
  
 Polecenie, które można identyfikator zasobów aplikacji pojawia się w kilku miejscach:  
  
-   W jednym STRINGTABLE zasób, który ma ten sam identyfikator jak monit wiersz wiadomości.  
  
-   W prawdopodobnie wielu MENU zasobów, które są dołączone do elementów menu, które wywołują tego samego polecenia.  
  
-   (Zaawansowane) w oknie dialogowym przycisk polecenia GOSUB.  
  
 W kodzie źródłowym aplikacji polecenie, które można identyfikator pojawia się w kilku miejscach:  
  
-   W ZASOBIE. H (lub inne plik nagłówka symbolu głównego) do definiowania identyfikatory poleceń specyficzne dla aplikacji.  
  
-   Być może w tablicy identyfikator używany do tworzenia paska narzędzi.  
  
-   W **on_command —** makra.  
  
-   Być może w **on_update_command_ui —** makra.  
  
 Obecnie można tylko implementacja MFC, która wymaga identyfikatory poleceń > = 0x8000 jest implementacją GOSUB okien dialogowych/poleceń.  
  
## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>Polecenia GOSUB, przy użyciu polecenia architektury w oknach dialogowych  
 Architektura polecenia routingu i włączenia polecenia dobrze działa z okien ramowych, elementów menu, przycisków paska narzędzi, przycisków paska dialogowego, inne paski sterowania i inne elementy interfejsu użytkownika przeznaczony do aktualizacji na żądanie i tras polecenia lub kontrolować identyfikatorów dla metody main obiekt docelowy polecenia (zazwyczaj głównego okna ramowego). Polecenie głównego obiektu docelowego może kierować powiadomienia polecenie lub formant do innych obiektów docelowych polecenia zależnie od potrzeb.  
  
 Okno dialogowe (modalne i niemodalne) mogą korzystać z niektórych funkcji architektura polecenia po przypisaniu identyfikator formantu okna dialogowego formantu do identyfikator odpowiedniego polecenia. Obsługa w oknach dialogowych nie jest automatyczne, więc należy napisać dodatkowy kod.  
  
 Należy pamiętać, że wszystkie te funkcje działają prawidłowo, Twoje identyfikatory poleceń powinny być > = 0x8000. Ponieważ wiele okien dialogowych można pobrać kierowane do tego samego ramki, udostępnionych poleceń powinna być > = 0x8000, udostępniana IDCs w określonym oknie dialogowym powinny być < = 0x7FFF.  
  
 Normalny przycisk można umieścić w normalnych modalnego okna dialogowego z IDC przycisku ustawiony identyfikator odpowiednie polecenie. Po wybraniu przycisku właściciela okna dialogowego (zazwyczaj głównego okna ramowego) pobiera polecenia, podobnie jak inne polecenia. Jest to polecenie GOSUB, ponieważ zwykle jest używany do innego okna dialogowego (GOSUB pierwszego okna dialogowego)  
  
 Możesz także wywołać funkcję **CWnd::UpdateDialogControls** na Twoje okno dialogowe i przekaż go adres główną ramkę okna. Ta funkcja będzie włączać lub wyłączać formantów okna dialogowego na podstawie tego, czy mają one programy obsługi poleceń w ramce. Ta funkcja jest wywoływana automatycznie dla Ciebie pasków sterowania w pętli bezczynności aplikacji, ale należy wywołać go bezpośrednio do normalnego okna dialogowe, które chcesz użyć tej funkcji.  
  
## <a name="when-onupdatecommandui-is-called"></a>Gdy jest wywoływana on_update_command_ui —  
 Zachowanie stanu włączone zaznaczone, program wszystkich elementów menu cały czas może być kosztowne w praktyce problem. Typowe techniki jest enable/wyboru elementów menu tylko wtedy, gdy użytkownik wybierze opcję menu PODRĘCZNEGO. Implementacja MFC 2.0 **cframewnd —** dojść **WM_INITMENUPOPUP** wiadomości i korzysta z architektury routingu poleceń w celu ustalenia stanów menu za pośrednictwem **ON_UPDATE_COMMAND_ Interfejs użytkownika** programów obsługi.  
  
 **Cframewnd —** obsługuje także **WM_ENTERIDLE** komunikat opisujący bieżący menu wybranego elementu w pasku (znanej także jako wiersz wiadomości) stanu.  
  
 Struktura menu aplikacji, edytowany przez Visual C++, jest używana do reprezentowania polecenia potencjalnych dostępne pod adresem **WM_INITMENUPOPUP** czasu. **On_update_command_ui —** programy obsługi można modyfikować stanu lub tekst elementu menu lub dla zaawansowanych używa (na przykład listy ostatnio używanych plików lub menu podręcznego zleceń OLE), faktycznie zmodyfikować struktury menu przed narysowaniem menu.  
  
 Taki sam sortowania z **on_update_command_ui —** przetwarzania odbywa się paski narzędzi (i innych paski sterowania) po przejściu jego pętli bezczynności aplikacji. Zobacz *informacje dotyczące biblioteki klas* i [31 Uwaga techniczna](../mfc/tn031-control-bars.md) uzyskać więcej informacji na temat paski sterowania.  
  
## <a name="nested-pop-up-menus"></a>Zagnieżdżone menu wyskakujące  
 Jeśli używasz struktury zagnieżdżone menu, można zauważyć, że **on_update_command_ui —** obsługi dla pierwszego elementu menu w menu podręczne jest wywoływana w dwóch różnych przypadkach.  
  
 Najpierw jest wywoływana dla samego menu podręcznym. Jest to konieczne, ponieważ menu wyskakujące nie mają identyfikatorów i używamy identyfikator pierwszego elementu menu wyskakującego menu do odwoływania się do całego menu podręczne. W takim przypadku **m_pSubMenu** zmiennej członkowskiej z **CCmdUI** obiekt będzie mieć wartości NULL i wskaż menu podręczne.  
  
 Po drugie jest ona wywoływana tuż przed elementów menu w menu podręcznym mają być tworzone. W takim przypadku Identyfikatora dotyczy tylko pierwszego elementu menu i **m_pSubMenu** zmiennej członkowskiej z **CCmdUI** obiektu będzie mieć wartości NULL.  
  
 Umożliwia włączenie menu podręczne różne od jego elementy menu, ale wymaga napisanie kodu pamiętać menu. Na przykład w zagnieżdżonych menu o następującej strukturze:  
  
```  
File>  
    New> 
    Sheet (ID_NEW_SHEET)  
    Chart (ID_NEW_CHART)  
```  
  
 Polecenia ID_NEW_SHEET i ID_NEW_CHART można niezależnie włączone lub wyłączone. **Nowy** menu podręczne powinno być włączone, jeśli jeden z dwóch jest włączona.  
  
 Program obsługi poleceń dla ID_NEW_SHEET (pierwsze polecenie w oknie podręcznym) będzie wyglądać mniej więcej tak:  
  
```  
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)  
{  
    if (pCmdUI->m_pSubMenu != NULL)  
 { *// enable entire pop-up for "New" sheet and chart  
    BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;  
 *// CCmdUI::Enable is a no-op for this case,
    so we *//   must do what it would have done.  
    pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex, 
    MF_BYPOSITION |   
 (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

    return; 
 } *// otherwise just the New Sheet command  
    pCmdUI->Enable(m_bCanCreateSheet);

} 
```  
  
 Program obsługi poleceń dla ID_NEW_CHART będzie, program obsługi aktualizacji poleceń i wyglądu coś, takich jak:  
  
```  
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)  
{  
    pCmdUI->Enable(m_bCanCreateChart);

} 
```  
  
## <a name="oncommand-and-onbnclicked"></a>On_command — i ON_BN_CLICKED  
 Makra mapy komunikatów dla **on_command —** i **ON_BN_CLICKED** są takie same. MFC polecenia i kontroli mechanizm routingu powiadomień używa tylko identyfikator polecenia do zdecyduj, gdzie należy kierować do. Kontrolowanie powiadomienia z kontroli kodu powiadomienia o wartości zero (**BN_CLICKED**) są interpretowane jako polecenia.  
  
> [!NOTE]
>  W rzeczywistości wszystkie komunikaty powiadomień dotyczących formantu przejść przez łańcuch programu obsługi poleceń. Na przykład jest technicznie możliwe do pisania obsługi powiadomień sterowania **EN_CHANGE** w klasie dokumentu. Nie jest to zwykle zalecane, ponieważ praktyczne zastosowania tej funkcji są kilka, funkcja ta nie jest obsługiwana przez ClassWizard i korzystanie z funkcji może spowodować wrażliwych kodu.  
  
## <a name="disabling-the-automatic-disabling-of-button-controls"></a>Wyłączanie automatyczne wyłączenie przycisku formantów  
 Jeśli formant przycisk paska dialogowego lub w oknie dialogowym przy użyciu where wywoływania **CWnd::UpdateDialogControls** samodzielnie, zauważysz, że przycisków, które nie mają **on_command —** lub **On_update_command_ui —** obsługi zostanie automatycznie wyłączone dla Ciebie przez platformę. W niektórych przypadkach należy nie ma obsługi, ale można przycisk, aby pozostać włączone. Najprostszym sposobem, aby to osiągnąć jest Dodaj program obsługi poleceń zastępczego (łatwy sposób korzystania z ClassWizard) i nic nie rób w nim.  
  
## <a name="window-message-routing"></a>Routing komunikatów okien  
 Poniżej opisano niektórych bardziej zaawansowanych tematów dotyczących klas MFC i routing komunikatów systemu Windows i innych tematach wpływ je. Tutaj informacje tylko opisano krótko. Zapoznaj się *informacje dotyczące biblioteki klas* szczegółowe informacje dotyczące publicznych interfejsach API. Można znaleźć więcej informacji na temat szczegóły implementacji w kodzie źródłowym biblioteki MFC.  
  
 Zapoznaj się z [17 Uwaga techniczna](../mfc/tn017-destroying-window-objects.md) szczegółowe informacje o oknie oczyszczania, bardzo ważne tematu dla wszystkich **CWnd**-klas pochodnych.  
  
## <a name="cwnd-issues"></a>Problemy z CWnd  
 Funkcja członkowska implementacji **CWnd::OnChildNotify** zapewnia zaawansowany i rozszerzalny architekturę podrzędnych do systemu Windows (znanej także jako formanty) utworzenie punktu zaczepienia lub w przeciwnym razie informowany o wiadomości, poleceń i sterowania powiadomienia wysyłane do ich nadrzędnej (lub "właściciela"). Jeśli okna podrzędnego (/ sterowania) jest C++ **CWnd** obiektu, funkcji wirtualnej **OnChildNotify** jest wywoływana najpierw z parametrami z oryginalnej wiadomości (oznacza to, **MSG**struktury). Okno podrzędne można pozostawić komunikat samodzielnie, jeść go lub modyfikowania komunikat nadrzędnego (rzadki przypadek).  
  
 Wartość domyślna **CWnd** implementacja obsługuje następujące komunikaty i używa **OnChildNotify** haku umożliwia podrzędne systemu windows (formanty) do pierwszego dostępu w komunikacie:  
  
- **WM_MEASUREITEM** i **WM_DRAWITEM** (własnym narysuj)  
  
- **WM_COMPAREITEM** i **WM_DELETEITEM** (własnym narysuj)  
  
- **WM_HSCROLL** i **WM_VSCROLL**  
  
- **WM_CTLCOLOR —**  
  
- **WM_PARENTNOTIFY**  
  
 Można zauważyć **OnChildNotify** haku służy do Zmienianie wiadomości rysowania przez właściciela na własnym rysowania wiadomości.  
  
 Oprócz **OnChildNotify** haku przewijania wiadomości ma dalszych routingu zachowanie. Poniżej więcej informacji znajdziesz na paski przewijania i źródła **WM_HSCROLL** i **WM_VSCROLL** wiadomości.  
  
## <a name="cframewnd-issues"></a>Cframewnd — problemy  
 **Cframewnd —** klasy zawiera większość routing poleceń i interfejs użytkownika aktualizacji wdrożenia. Służy to głównie dla głównego okna ramowego aplikacji (**CWinApp::m_pMainWnd**), ale ma zastosowanie do wszystkich okien ramowych.  
  
 Główną ramkę okna jest okna z paska menu i element nadrzędny paska stanu lub komunikatu wiersza. Można znaleźć w powyższym dyskusji routing poleceń i **WM_INITMENUPOPUP.**  
  
 **Cframewnd —** klasy zapewnia możliwość zarządzania aktywnego widoku. Następujące komunikaty są wysyłane za pośrednictwem widoku aktywnego:  
  
-   Wszystkie komunikaty poleceń (aktywny widok pobiera pierwszy dostępu do nich).  
  
- **WM_HSCROLL** i **WM_VSCROLL** wiadomości z tego samego poziomu przewiń paski (patrz poniżej).  
  
- **WM_ACTIVATE** (i **WM_MDIACTIVATE** dla MDI) Pobierz zamieniło wywołania funkcji wirtualnej **CView::OnActivateView**.  
  
## <a name="cmdiframewndcmdichildwnd-issues"></a>Cmdiframewnd — / CMDIChildWnd problemów  
 Klasy okien ramowych zarówno MDI pochodzi od **cframewnd —** i w związku z tym są obie włączone dla tego samego rodzaju routing poleceń i aktualizowanie interfejsu użytkownika dostępnych w **cframewnd —**. W typowej aplikacji MDI główną ramkę okna (to znaczy **cmdiframewnd —** obiektu) zawiera paska menu i paska stanu i dlatego jest główne źródło routingu wykonania polecenia.  
  
 Ogólne system routingu jest, że aktywnego okna podrzędnego MDI pobiera pierwszy dostępu do poleceń. Wartość domyślna **PreTranslateMessage** funkcje obsługi tabel akceleratora dla obu okien podrzędnych MDI (najpierw) i ramki MDI (drugi) oraz standardowe akceleratorów polecenia systemu MDI zazwyczaj obsługiwane przez  **TranslateMDISysAccel** (ostatniego).  
  
## <a name="scroll-bar-issues"></a>Problemy z paska przewijania  
 Podczas obsługi wiadomości przewijania (**WM_HSCROLL**/**OnHScroll** i/lub **WM_VSCROLL**/**OnVScroll**), należy napisać kod obsługi, więc nie bazuje na skąd pochodzą komunikatów paska przewijania. To nie jest tylko ogólne Windows problemem, ponieważ komunikaty przewijania mogą pochodzić z true przewijania paska formantów lub z **ws_hscroll —**/**ws_vscroll —** przewiń paski, które nie są formanty paska przewijania.  
  
 Rozszerza MFC, że w celu umożliwienia formanty paska przewijania podrzędnych lub elementów równorzędnych okna jest przewijane (w rzeczywistości relacji nadrzędny/podrzędny między pasek przewijania i okno jest przewijane może być wszystko). Jest to szczególnie ważne dla pasków przewijania udostępnionych z okna podziału. Zapoznaj się z [29 Uwaga techniczna](../mfc/tn029-splitter-windows.md) szczegółowe informacje na temat stosowania **CSplitterWnd** tym więcej informacji na udostępnionych problemów paska przewijania.  
  
 Na Notatka boczna występują dwa **CWnd** klas pochodnych, gdzie czas utworzenia Style paska przewijania, które są określone w są kolor i nie są przekazywane do systemu Windows. Przekazany do procedury tworzenia **ws_hscroll —** i **ws_vscroll —** można niezależnie ustawić, ale po tworzenia nie można zmienić. Oczywiście należy bezpośrednio testów lub ustaw WS_SCROLL bitów stylów okna utworzonego.  
  
 Aby uzyskać **cmdiframewnd —** Style paska przewijania przekazywane w celu **Utwórz** lub **LoadFrame** są używane do tworzenia MDICLIENT. Jeśli chcesz mieć przewijany obszar MDICLIENT (takie jak Windows Menedżera programów) należy ustawić zarówno paska przewijania style (**ws_hscroll —** &#124; **ws_vscroll —**) używany do tworzenia stylu**Cmdiframewnd —**.  
  
 Aby uzyskać **CSplitterWnd** Style paska przewijania dotyczą pasków przewijania udostępnionego specjalne dla regionów podziału. Dla statyczne okna podziału zwykle nie ustawisz albo style paska przewijania. Dla dynamiczne okna podziału, zazwyczaj należy pasek zestaw stylów dla kierunku będzie podziału, czyli przewijania **ws_hscroll —** czy jest możliwe podzielenie wierszy, **ws_vscroll —** czy jest możliwe podzielenie kolumn.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

