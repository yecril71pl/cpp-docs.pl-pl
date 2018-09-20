---
title: 'Polecenie TN021: Routing i komunikatów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
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
ms.openlocfilehash: 4d10fc56363a9ef460e0aaafadf300a2f649d5b2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412343"
---
# <a name="tn021-command-and-message-routing"></a>TN021: routing poleceń i komunikatów

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisuje architekturę routingu i wysyłania poleceń, a także zaawansowanie zagadnienia dotyczące routingu komunikatów Ogólne okna.

Zapoznaj się Visual C++ dla ogólnych informacji na temat architektury widocznym tu opisem, szczególnie rozróżnienie między Windows komunikaty powiadomień dotyczących formantu karty i poleceń. Ta uwaga przyjęto założenie, są bardzo podobnie do funkcji z problemami z opisem zamieszczonym w dokumentacji drukowane i powodowało jedynie bardzo zaawansowanych tematów.

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Routing poleceń i wysyłaj MFC 1.0 funkcji ewoluuje do MFC w wersji 2.0 architektury

Windows ma komunikatów WM_COMMAND, która jest przeciążona, aby zapewnić powiadomień polecenia menu, klawisze skrótów i powiadomień dotyczących formantów okna dialogowego.

1.0 z MFC oparta na tym nieco, umożliwiając procedurę obsługi poleceń (na przykład "OnFileNew") `CWnd` pochodne klasy, aby zostać wywołana w odpowiedzi na określone WM_COMMAND. To jest przyklejone wraz z strukturę danych o nazwie mapy komunikatów i powoduje mechanizm bardzo kompaktowa polecenia.

1.0 z MFC udostępniane są również dodatkowe funkcje do oddzielania powiadomień dotyczących formantu karty z komunikaty poleceń. Polecenia są reprezentowane przez identyfikator 16-bitowych, czasami znana jako identyfikatora polecenia. Poleceń rozpoczyna się zwykle z `CFrameWnd` (oznacza to, wybierz menu lub przetłumaczone akceleratora) i Pobierz kierowane do różnych innych oknach.

1.0 z MFC używany routing poleceń w sensie ograniczone dla implementacji interfejsu dokumencie wielu (MDI). (Okna ramki MDI delegować polecenia, aby jego aktywnego okna elementu podrzędnego MDI).

Ta funkcja została uogólniona i rozszerzony w MFC 2.0 w celu zezwalania na polecenia, które mają być obsługiwane przez szerszego zakresu obiektów (nie tylko obiektów okien). Zapewnia więcej formalnych i rozszerzalnej architektury dla routingu wiadomości, a także ponownie używa routingu docelowym poleceń nie tylko obsługi poleceń, ale także do aktualizowanie obiektów interfejsu użytkownika (np. elementy menu i przycisków paska narzędzi) w celu odzwierciedlenia bieżącej dostępności polecenia .

## <a name="command-ids"></a>Identyfikatory poleceń

Wyjaśnienie polecenia routingu i powiązanie procesu na ten temat można znaleźć w Visual C++. [Uwagi techniczne 20](../mfc/tn020-id-naming-and-numbering-conventions.md) zawiera informacje na temat nazewnictwa identyfikator.

Używamy ogólnego prefiksu "ID_" dla identyfikatorów poleceń. Identyfikatory poleceń jest > = 0x8000. Wiadomości wiersza lub paska stanu wyświetli ciąg opisu polecenia, jeśli istnieje zasób STRINGTABLE o takich samych identyfikatorów jako identyfikator polecenia.

Zasoby aplikacji polecenia, który można identyfikator pojawia się w kilku miejscach:

- W jednej STRINGTABLE zasób, który ma ten sam identyfikator jako wiersz wiadomości.

- W prawdopodobnie wielu MENU zasobów, które są dołączone do elementów menu, które wywołują to samo polecenie.

- (Zaawansowane) w oknie dialogowym przycisk polecenia GOSUB.

W kodzie źródłowym aplikacji polecenia, który można identyfikator pojawia się w kilku miejscach:

- W swoim ZASOBIE. H (lub innego pliku nagłówkowym symboli głównego) do zdefiniowania identyfikatorów poleceń specyficznych dla aplikacji.

- Być może w tablicy Identyfikatora, używany do tworzenia paska narzędzi.

- W ON_COMMAND — makro.

- Być może w ON_UPDATE_COMMAND_UI — makro.

Obecnie można tylko wdrożenia w MFC, który wymaga identyfikatory poleceń > = 0x8000 jest implementacją GOSUB okien dialogowych/poleceń.

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>Polecenia GOSUB, przy użyciu polecenia architektury w oknach dialogowych

Architektura polecenia routing poleceń i dobrze działa z okien ramowych, elementy menu, przyciski paska narzędzi, przycisków paska dialogowego innych pasków sterowania i inne elementy interfejsu użytkownika, przeznaczony do aktualizacji na żądanie, jak i trasy poleceń lub kontroli identyfikatory dla metody main element docelowy polecenia (zwykle w oknie głównym ramki). Polecenie głównego obiektu docelowego może kierować powiadomienia polecenia lub formantu do innych obiektów docelowych polecenia zgodnie z potrzebami.

Okno dialogowe (modalnym lub niemodalnym) mogą korzystać z niektórych funkcji architektury polecenia, jeśli przypiszesz kontroli identyfikator formantu okna dialogowego do odpowiednich komendy Obsługa w oknach dialogowych jest automatyczne, więc trzeba napisać dodatkowy kod.

Należy pamiętać, że wszystkie te funkcje działają prawidłowo, swoim identyfikatorem polecenia powinien być > = 0x8000. Ponieważ wiele okien dialogowych można uzyskać kierowane do tego samego ramki, udostępnionych poleceń powinny być > = 0x8000, podczas gdy nieudostępnionych IDCs w określonym oknie dialogowym powinny być < = 0x7FFF.

Normalny przycisk można umieścić w normalnym modalne okno dialogowe z firmy IDC przycisku, ustaw odpowiedni komendy Gdy użytkownik wybierze przycisk, właściciela okna dialogowego (zwykle w oknie głównym ramki) pobiera polecenia, podobnie jak inne polecenia. Jest to nazywane polecenia GOSUB, ponieważ zwykle jest używany do innego okna dialogowego (GOSUB pierwsze okno dialogowe).

Można również wywołać funkcję `CWnd::UpdateDialogControls` na okna dialogowego i przekaż go na adres Twojej głównej ramki okna. Ta funkcja będzie włączać lub wyłączać formantów okna dialogowego na podstawie tego, czy mają one programy obsługi poleceń w ramce. Ta funkcja jest wywoływana automatycznie dla Ciebie pasków sterowania w pętli bezczynności aplikacji, ale należy wywołać go bezpośrednio do normalnego okien dialogowych, które chcesz użyć tej funkcji.

## <a name="when-onupdatecommandui-is-called"></a>Gdy jest wywoływana ON_UPDATE_COMMAND_UI

Obsługa przez cały czas stan włączony zaznaczone program wszystkie elementy menu może to stanowić problem dużego nakładu mocy obliczeniowych. Typową techniką jest/kontrola włączenia elementów menu tylko wtedy, gdy użytkownik wybierze opcję menu PODRĘCZNEGO. Implementacja MFC w wersji 2.0 `CFrameWnd` obsługuje wiadomości WM_INITMENUPOPUP i używa architektury routingu poleceń do określenia stany menu za pomocą ON_UPDATE_COMMAND_UI obsługi.

`CFrameWnd` obsługuje także komunikatów wm_enteridle, gdy do opisania bieżącego menu wybrany element na pasku (znany także jako wiersz wiadomości) stanu.

Struktura menu aplikacja, edytowane przez Visual C++, jest używana do reprezentowania potencjalnych poleceń dostępnych w czasie WM_INITMENUPOPUP. ON_UPDATE_COMMAND_UI obsługi można zmodyfikować stanu lub tekst menu, lub na potrzeby zaawansowanego (na przykład listy ostatnio używanych plików lub menu podręcznego czasowniki OLE), faktycznie modyfikować strukturę menu przed narysowaniem menu.

Jest taka sama ON_UPDATE_COMMAND_UI przetwarzanie odbywa się paski narzędzi (i inne paski sterowania) po przejściu jego wykonywania pętli bezczynności w aplikacji. Zobacz *odwołanie do biblioteki klas* i [techniczne 31 Uwaga](../mfc/tn031-control-bars.md) więcej informacji na temat pasków sterowania.

## <a name="nested-pop-up-menus"></a>Zagnieżdżone wyskakujących menu

Jeśli używasz struktury zagnieżdżonej menu, można zauważyć, że obsługa ON_UPDATE_COMMAND_UI pierwszy element menu w menu podręcznym jest wywoływana w dwóch różnych przypadkach.

Po pierwsze jest ona wywoływana dla samo menu podręcznego. Jest to konieczne, ponieważ wyskakujących menu nie ma identyfikatorów i używamy identyfikator pierwszego elementu menu podręcznym menu do odwoływania się do całego menu podręcznego. W tym przypadku *m_pSubMenu* zmienną elementu członkowskiego `CCmdUI` obiekt będzie mieć wartości NULL i wskaż menu podręcznego.

Po drugie jest wywoływana przed elementów menu w menu podręcznym mają być tworzone. W tym przypadku identyfikator dotyczy tylko pierwszego elementu menu i *m_pSubMenu* zmienną elementu członkowskiego `CCmdUI` obiektu będzie mieć wartości NULL.

Umożliwia włączenie menu podręcznego różne od jego elementy menu, ale wymaga pisania kodu z rozpoznawaniem niektóre menu. Na przykład w zagnieżdżonych menu o następującej strukturze:

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

Polecenia ID_NEW_SHEET i ID_NEW_CHART można niezależnie włączać lub wyłączać. **New** menu podręcznego powinno być włączone, jeśli jeden z dwóch jest włączona.

Procedury obsługi poleceń dla ID_NEW_SHEET (pierwsze polecenie w oknie podręcznym) będą wyglądać mniej więcej tak:

```cpp
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)
{
    if (pCmdUI->m_pSubMenu != NULL)
    {
        // enable entire pop-up for "New" sheet and chart
        BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;
        // CCmdUI::Enable is a no-op for this case, so we
        // must do what it would have done.
        pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex,
            MF_BYPOSITION |
            (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

        return;
    }
    // otherwise just the New Sheet command
    pCmdUI->Enable(m_bCanCreateSheet);
}
```

Procedury obsługi poleceń dla ID_NEW_CHART będzie, program obsługi poleceń normalnej aktualizacji i wygląd coś w rodzaju:

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="oncommand-and-onbnclicked"></a>ON_COMMAND i ON_BN_CLICKED

Makra mapy komunikatów dla **ON_COMMAND** i **ON_BN_CLICKED** są takie same. MFC poleceń i kontroli mechanizm routingu powiadomień używa tylko identyfikator polecenia zdecydować, gdzie można kierować do. Kontrolowania powiadomień z kontroli kodu powiadomienia o wartości zero (**BN_CLICKED**) są interpretowane jako polecenia.

> [!NOTE]
> W rzeczywistości wszystkie komunikaty powiadomień dotyczących kontrolki przechodzą przez łańcuch program obsługi poleceń. Na przykład jest technicznie możliwe, pisanie obsługi powiadamiania kontrolki **EN_CHANGE** w swojej klasie dokumentów. To nie jest na ogół ponieważ praktyczne zastosowania tej funkcji są kilka, funkcja ta nie jest obsługiwana przez ClassWizard i korzystanie z funkcji może spowodować delikatna kodu.

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>Wyłączanie automatycznego wyłączania formanty przycisków

Jeśli formant przycisku na pasku okna dialogowego lub w oknie dialogowym przy użyciu gdzie wywołujesz **CWnd::UpdateDialogControls** na własną rękę, zauważysz, że przyciski, które nie mają **ON_COMMAND** lub **ON_UPDATE_COMMAND_UI** obsługi zostanie automatycznie wyłączone dla Ciebie przez platformę. W niektórych przypadkach nie musisz mieć program obsługi, ale można przycisk aby pozostać włączone. Najprostszym sposobem osiągnięcia tego jest można dodać procedury obsługi polecenia fikcyjnego (łatwy sposób korzystania z ClassWizard) i nic nie rób w nim.

## <a name="window-message-routing"></a>Routing komunikatów okien

Poniżej przedstawiono niektóre bardziej zaawansowane tematy dotyczące klas MFC i routing komunikatów Windows i innych tematów wpływie na ich. W tym miejscu informacje tylko opisano skrótowo. Zapoznaj się *odwołanie do biblioteki klas* szczegółowe informacje na temat publicznych interfejsów API. Zapoznaj się kod źródłowy biblioteki MFC, aby uzyskać więcej informacji na temat szczegółów implementacji.

Zapoznaj się [techniczne 17 Uwaga](../mfc/tn017-destroying-window-objects.md) szczegółowe informacje na temat czyszczenia okna, bardzo ważne tematu dla wszystkich **CWnd**-klas pochodnych.

## <a name="cwnd-issues"></a>Problemy z CWnd

Funkcja elementu członkowskiego implementacji **CWnd::OnChildNotify** zapewnia wydajna i Rozszerzalna architektura podrzędnych do systemu Windows (znany także jako formanty) utworzenie punktu zaczepienia lub w przeciwnym razie informowany o wiadomości, poleceń i kontroli powiadomienia, które przejść do ich nadrzędnej (lub "właściciel"). Jeśli okna podrzędnego (/ kontrolować) jest C++ **CWnd** obiektu, funkcja wirtualna **OnChildNotify** jest wywoływana najpierw z parametrami z oryginalnego komunikatu (oznacza to, **MSG**struktury). Okno podrzędne można samodzielnie Pozostaw wiadomość, jeść go lub zmodyfikuj wiadomość nadrzędnego (rzadkiego).

Wartość domyślna **CWnd** implementacja obsługuje następujące komunikaty i używa **OnChildNotify** punktu zaczepienia umożliwiające podrzędne systemu windows (formanty) do pierwszego dostępu wglądu do wiadomości:

- **WM_MEASUREITEM** i **WM_DRAWITEM** (własnym narysuj)

- **WM_COMPAREITEM** i **WM_DELETEITEM** (własnym narysuj)

- **WM_HSCROLL** i **WM_VSCROLL**

- **WM_CTLCOLOR —**

- **WM_PARENTNOTIFY**

Można zauważyć **OnChildNotify** punktów zaczepienia jest używana do Zmienianie rysowania przez właściciela, wiadomości na własnym narysuj wiadomości.

Oprócz **OnChildNotify** hook wiadomości przewijania mają dalsze routingu zachowanie. Poniżej podano szczegółowe informacje na temat pasków przewijania i źródeł **WM_HSCROLL** i **WM_VSCROLL** wiadomości.

## <a name="cframewnd-issues"></a>Problemy z obiektu CFrameWnd

**CFrameWnd** klasy zawiera większość routing poleceń i interfejs użytkownika aktualizacji wdrożenia. Służy on głównie do ramką głównego okna aplikacji (**CWinApp::m_pMainWnd**), ale ma zastosowanie do wszystkich okien ramowych.

Ramką głównego okna okna przy użyciu paska menu i jest elementem nadrzędnym na pasku stanu lub komunikatu wiersza. Można znaleźć w dyskusji powyżej routing poleceń i **WM_INITMENUPOPUP.**

**CFrameWnd** klasy umożliwia zarządzanie bieżącym widokiem. Następujące komunikaty są przesyłane za pośrednictwem widoku aktywnego:

- Wszystkie komunikaty poleceń (widok aktywny pobiera pierwszego uzyskiwania do nich dostępu).

- **WM_HSCROLL** i **WM_VSCROLL** komunikaty z tego samego poziomu przewiń paski (patrz poniżej).

- **WM_ACTIVATE** (i **WM_MDIACTIVATE** dla MDI) Pobierz zamieniło wywołania funkcji wirtualnej **CView::OnActivateView**.

## <a name="cmdiframewndcmdichildwnd-issues"></a>Problemy z CMDIFrameWnd/CMDIChildWnd

Zarówno klasy okna ramki MDI pochodzić od **CFrameWnd** i dlatego są włączone dla tego samego rodzaju routing poleceń i aktualizowanie interfejsu użytkownika podane w **CFrameWnd**. W Typowa aplikacja MDI ramki głównego okna (czyli **CMDIFrameWnd** obiektu) zawiera pasek menu i paska stanu i dlatego jest głównym źródłem implementacja routingu poleceń.

Ogólne schemat routingu jest, że okno podrzędne MDI active pobiera pierwszą dostęp do poleceń. Wartość domyślna **pretranslatemessage —** funkcje obsługi tabel akceleratora dla obu oknami podrzędnymi MDI (na początku) i ramki MDI (sekundy), a także standardowych akceleratorów poleceń systemowych MDI, zazwyczaj obsługiwane przez  **TranslateMDISysAccel** (ostatniego).

## <a name="scroll-bar-issues"></a>Problemy z paska przewijania

Podczas obsługi komunikatu przewijania (**WM_HSCROLL**/**OnHScroll** i/lub **WM_VSCROLL**/**OnVScroll**), należy starać się pisania kodu programu obsługi, więc nie zależy pochodzenia wiadomości paska przewijania. To nie tylko ogólne Windows problemem, ponieważ komunikaty przewijania mogą pochodzić z true przewijania paska kontrolki lub z **WS_HSCROLL**/**WS_VSCROLL** paski, które nie są formanty paska przewijania przewijania.

MFC rozszerza, aby umożliwić formanty paska przewijania podrzędne lub elementów równorzędnych okna jest przewijane (w rzeczywistości relacji nadrzędny/podrzędny między paska przewijania i jest przewijane okno może być cokolwiek). Jest to szczególnie ważne w przypadku pasków przewijania udostępnione za pomocą okna podziału. Zapoznaj się [techniczne 29 Uwaga](../mfc/tn029-splitter-windows.md) szczegółowe informacje na temat implementacji **CSplitterWnd** łącznie więcej informacji na udostępniony problemów paska przewijania.

Na marginesie, istnieją dwa **CWnd** klasy pochodne, gdy czas utworzenia Style paska przewijania, które są określone na są zablokował i nie zostaną przekazane do Windows. Przekazany do procedury tworzenia **WS_HSCROLL** i **WS_VSCROLL** można niezależnie ustawić, ale po utworzeniu nie można jej zmienić. Oczywiście należy bezpośrednio testów lub ustawić bity WS_SCROLL stylu okna, które zostały utworzone.

Dla **CMDIFrameWnd** Style paska przewijania przekazanej do **Utwórz** lub **loadframe —** są używane do tworzenia MDICLIENT. Jeśli chcesz mieć przewijanym obszarze MDICLIENT (np. Windows Menedżera programów) należy ustawić zarówno paska przewijania style (**WS_HSCROLL** &#124; **WS_VSCROLL**) dla stylu użyty do utworzenia **CMDIFrameWnd**.

Aby uzyskać **CSplitterWnd** Style paska przewijania dotyczą pasków specjalne przewijania udostępnionego dla regionów rozdzielacza. W przypadku systemu windows statyczny rozdzielacz ustawi zwykle nie albo styl paska przewijania. Dynamiczne okna podziału, zazwyczaj należy przypadku pasek zestaw stylów dla kierunku podzielisz, czyli przewijania **WS_HSCROLL** czy jest możliwe podzielenie wierszy, **WS_VSCROLL** czy jest możliwe podzielenie kolumn.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
