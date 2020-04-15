---
title: 'TN021: routing poleceń i komunikatów'
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: bdd405bda5c0af9e04a50eee4ef5738f3a53259e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370413"
---
# <a name="tn021-command-and-message-routing"></a>TN021: routing poleceń i komunikatów

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

W tej notatce opisano architekturę routingu i wysyłki poleceń, a także zaawansowane tematy w ogólnym routingu komunikatów okien.

Szczegółowe informacje na temat architektur opisanych w tym miejscu można znaleźć w języku Visual C++, a zwłaszcza na temat rozróżnienia między komunikatami systemu Windows, powiadomieniami sterującymi i poleceniami. Ta uwaga zakłada, że jesteś bardzo zaznajomiony z problemami opisanymi w drukowanej dokumentacji i dotyczy tylko bardzo zaawansowanych tematów.

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Funkcja routingu i wysyłki polecenia MFC 1.0 ewoluuje do architektury MFC 2.0

System Windows ma WM_COMMAND komunikat, który jest przeciążony, aby zapewnić powiadomienia o poleceniach menu, klawiszach akceleratora i powiadomieniach o kontroli dialogu dialogowego.

MFC 1.0 zbudowany na tym trochę, umożliwiając program obsługi poleceń (na przykład `CWnd` "OnFileNew") w klasie pochodnej, aby uzyskać wywoływane w odpowiedzi na określone WM_COMMAND. Jest to sklejone ze strukturą danych zwaną mapą komunikatów i powoduje bardzo kosmiczny mechanizm poleceń.

MFC 1.0 również dodatkowe funkcje do oddzielania powiadomień sterujących z komunikatów poleceń. Polecenia są reprezentowane przez 16-bitowy identyfikator, czasami znany jako identyfikator polecenia. Polecenia zwykle zaczynają się `CFrameWnd` od (czyli wyboru menu lub apeckiego tłumaczenia) i są kierowane do różnych innych okien.

MFC 1.0 używane routingu polecenia w ograniczonym znaczeniu dla implementacji wielu interfejsów dokumentów (MDI). (Okno ramki MDI deleguje polecenia do aktywnego okna podrzędnego MDI).

Ta funkcja została uogólniona i rozszerzona w MFC 2.0, aby umożliwić obsługę poleceń przez szerszy zakres obiektów (nie tylko obiektów okna). Zapewnia bardziej formalną i rozszerzalną architekturę do routingu wiadomości i ponownie używa routingu docelowego polecenia nie tylko do obsługi poleceń, ale także do aktualizowania obiektów interfejsu użytkownika (takich jak elementy menu i przyciski paska narzędzi), aby odzwierciedlić bieżącą dostępność polecenia.

## <a name="command-ids"></a>Identyfikatory poleceń

Zobacz Visual C++ wyjaśnienie procesu routingu polecenia i powiązania. [Uwaga techniczna 20](../mfc/tn020-id-naming-and-numbering-conventions.md) zawiera informacje na temat nazewnictwa identyfikatorów.

Używamy ogólnego prefiksu "ID_" dla identyfikatorów poleceń. Identyfikatory poleceń są >= 0x8000. Wiersz komunikatu lub pasek stanu wyświetli ciąg opisu polecenia, jeśli istnieje zasób STRINGTABLE o tych samych identyfikatorach co identyfikator polecenia.

W zasobach aplikacji identyfikator polecenia może być wyświetlany w kilku miejscach:

- W jednym zasobie STRINGTABLE, który ma ten sam identyfikator co monit wiersza wiadomości.

- W prawdopodobnie wiele zasobów MENU, które są dołączone do elementów menu, które wywołują to samo polecenie.

- (ZAAWANSOWANE) w przycisku dialogowym dla polecenia GOSUB.

W kodzie źródłowym aplikacji identyfikator polecenia może być wyświetlany w kilku miejscach:

- W zasobie. H (lub inny główny plik nagłówka symbolu) w celu zdefiniowania identyfikatorów poleceń specyficznych dla aplikacji.

- BYĆ MOŻE w tablicy identyfikatora używane do tworzenia paska narzędzi.

- W ON_COMMAND makra.

- BYĆ MOŻE w ON_UPDATE_COMMAND_UI makro.

Obecnie jedyną implementacją w MFC, która wymaga identyfikatorów poleceń >= 0x8000 jest implementacja dialogów/poleceń GOSUB.

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>Polecenia GOSUB, korzystanie z architektury poleceń w oknach dialogowych

Architektura poleceń routingu i włączania poleceń dobrze współadł a także z oknami ramki, elementami menu, przyciskami paska narzędzi, przyciskami paska dialogowego, innymi paskami sterowania i innymi elementami interfejsu użytkownika zaprojektowanymi w celu aktualizacji poleceń na żądanie i trasy lub identyfikatorów sterujących do głównego obiektu docelowego polecenia (zwykle głównego okna ramki). Ten główny cel polecenia może kierować powiadomienia polecenia lub kontroli do innych obiektów docelowych polecenia, stosownie do przypadku.

Okno dialogowe (modalne lub modne) może korzystać z niektórych funkcji architektury poleceń, jeśli zostanie przypisany identyfikator formantu sterującego do odpowiedniego identyfikatora polecenia. Obsługa okien dialogowych nie jest automatyczna, więc może być konieczne napisanie dodatkowego kodu.

Należy zauważyć, że aby wszystkie te funkcje działały poprawnie, identyfikatory poleceń powinny być >= 0x8000. Ponieważ wiele okien dialogowych może zostać przekierowanych do tej samej klatki, polecenia udostępnione powinny być >= 0x8000, podczas gdy nieudostępnione kontrolery IDC w określonym oknie dialogowym powinny być <= 0x7FFF.

Przycisk normalny można umieścić w normalnym oknie dialogowym modalnym, przy czym identyfikator przycisku jest ustawiony na odpowiedni identyfikator polecenia. Gdy użytkownik wybierze przycisk, właściciel okna dialogowego (zwykle okno ramki głównej) pobiera polecenie, podobnie jak każde inne polecenie. Jest to nazywane poleceniem GOSUB, ponieważ zwykle jest używane do wywoływania innego okna dialogowego (GOSUB pierwszego okna dialogowego).

Można również wywołać `CWnd::UpdateDialogControls` funkcję w oknie dialogowym i przekazać jej adres okna głównej ramki. Ta funkcja włącza lub wyłącza formanty dialogowe w zależności od tego, czy mają programy obsługi poleceń w ramce. Ta funkcja jest wywoływana automatycznie dla pasków sterowania w pętli bezczynności aplikacji, ale należy wywołać ją bezpośrednio dla normalnych okien dialogowych, które mają mieć tę funkcję.

## <a name="when-on_update_command_ui-is-called"></a>Kiedy ON_UPDATE_COMMAND_UI jest wywoływana

Utrzymywanie włączonego/sprawdzonego stanu wszystkich elementów menu programu przez cały czas może być kosztownym obliczeniowo problemem. Powszechną techniką jest włączanie/sprawdzanie elementów menu tylko wtedy, gdy użytkownik wybierze popup. Implementacja MFC 2.0 `CFrameWnd` obsługuje komunikat WM_INITMENUPOPUP i używa architektury routingu poleceń do określenia stanów menu za pośrednictwem ON_UPDATE_COMMAND_UI programów obsługi.

`CFrameWnd`obsługuje również komunikat WM_ENTERIDLE, aby opisać bieżący element menu wybrany na pasku stanu (znany również jako wiersz wiadomości).

Struktura menu aplikacji, edytowana przez visual C++, jest używana do reprezentowania potencjalnych poleceń dostępnych w WM_INITMENUPOPUP czasie. ON_UPDATE_COMMAND_UI programy obsługi mogą modyfikować stan lub tekst menu lub do zastosowań zaawansowanych (takich jak lista File MRU lub menu podręczne Ole Verbs), faktycznie zmodyfikować strukturę menu przed narysowaniem menu.

Ten sam rodzaj przetwarzania ON_UPDATE_COMMAND_UI odbywa się dla pasków narzędzi (i innych pasków kontrolnych), gdy aplikacja wejdzie w pętlę bezczynności. Więcej informacji na temat pasków sterujących można znaleźć w *dokumentacji biblioteki klas* i w [notatce technicznej 31.](../mfc/tn031-control-bars.md)

## <a name="nested-pop-up-menus"></a>Zagnieżdżone menu podręczne

Jeśli używasz struktury menu zagnieżdżonego, można zauważyć, że ON_UPDATE_COMMAND_UI obsługi dla pierwszego elementu menu w menu podręcznym jest wywoływana w dwóch różnych przypadkach.

Po pierwsze, jest to wymagane dla menu podręcznego. Jest to konieczne, ponieważ menu podręczne nie mają identyfikatorów i używamy identyfikatora pierwszego elementu menu w menu podręcznym, aby odnieść się do całego menu podręcznego. W takim przypadku *zmienna m_pSubMenu* elementu `CCmdUI` członkowskiego obiektu będzie nienależy do wartości NULL i wskaże menu podręczne.

Po drugie, jest wywoływana tuż przed elementy menu w menu podręcznym mają być rysowane. W takim przypadku identyfikator odnosi się tylko do pierwszego *m_pSubMenu* elementu menu i `CCmdUI` m_pSubMenu zmienną elementu członkowskiego obiektu będzie NULL.

Dzięki temu można włączyć menu podręczne różniące się od jego elementów menu, ale wymaga, aby napisać kod obsługujących menu. Na przykład w zagnieżdżonym menu o następującej strukturze:

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

Polecenia ID_NEW_SHEET i ID_NEW_CHART można niezależnie włączyć lub wyłączyć. Menu wyskakujące **Nowe** powinno być włączone, jeśli którykolwiek z nich jest włączony.

Program obsługi poleceń dla ID_NEW_SHEET (pierwsze polecenie w wyskakującym okienku) będzie wyglądał mniej więcej tak:

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

Program obsługi poleceń dla ID_NEW_CHART będzie normalnym programem obsługi poleceń aktualizacji i będzie wyglądać mniej więcej tak:

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="on_command-and-on_bn_clicked"></a>ON_COMMAND i ON_BN_CLICKED

Makra mapy wiadomości dla **ON_COMMAND** i **ON_BN_CLICKED** są takie same. Mechanizm routingu powiadomień mfc i kontroli używa tylko identyfikator polecenia, aby zdecydować, gdzie trasa do. Powiadomienia kontrolne z kodem powiadomienia sterującego o wartości zero **(BN_CLICKED)** są interpretowane jako polecenia.

> [!NOTE]
> W rzeczywistości wszystkie komunikaty powiadomień kontroli przechodzą przez łańcuch obsługi poleceń. Na przykład jest technicznie możliwe, aby napisać program obsługi powiadomień kontroli dla **EN_CHANGE** w klasie dokumentu. Nie jest to ogólnie wskazane, ponieważ praktyczne zastosowania tej funkcji są nieliczne, funkcja nie jest obsługiwana przez ClassWizard, a użycie tej funkcji może spowodować delikatny kod.

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>Wyłączanie automatycznego wyłączania elementów sterujących przyciskami

Jeśli umieścisz formant przycisku na pasku dialogowym lub w oknie dialogowym przy użyciu, w którym wywołujesz **CWnd::UpdateDialogControls** na własną rękę, można zauważyć, że przyciski, które nie mają **ON_COMMAND** lub **ON_UPDATE_COMMAND_UI** programy obsługi zostaną automatycznie wyłączone przez platformę. W niektórych przypadkach nie trzeba będzie mieć program obsługi, ale trzeba będzie przycisk, aby pozostać włączone. Najprostszym sposobem osiągnięcia tego celu jest dodanie fikcyjnego programu obsługi poleceń (łatwe do zrobienia z ClassWizard) i nic w nim nie robić.

## <a name="window-message-routing"></a>Routing wiadomości w oknie

Poniżej opisano niektóre bardziej zaawansowane tematy dotyczące klas MFC i jak routing wiadomości systemu Windows i inne tematy wpływają na nich. Informacje tutaj są opisane tylko krótko. Szczegółowe informacje na temat publicznych interfejsów API można znaleźć w *bibliotece klas.* Aby uzyskać więcej informacji na temat szczegółów implementacji, zapoznaj się z kodem źródłowym biblioteki MFC.

Szczegółowe informacje na temat oczyszczania okien, bardzo ważne dla wszystkich klas **CWnd,** należy zapoznać się z [uwagą techniczną 17.](../mfc/tn017-destroying-window-objects.md)

## <a name="cwnd-issues"></a>Problemy z CWnd

Funkcja elementu członkowskiego implementacji **CWnd::OnChildNotify** zapewnia zaawansowana i rozszerzalna architektura dla okien podrzędnych (znany również jako formanty) do haka lub w inny sposób być informowany o wiadomościach, polecenia i powiadomienia kontroli, które przechodzą do ich nadrzędnego (lub "właściciel"). Jeśli okno podrzędne (/control) jest samym obiektem **CWnd** języka C+,, funkcja wirtualna **OnChildNotify** jest wywoływana jako pierwsza z parametrami z oryginalnej wiadomości (czyli struktury **MSG).** Okno podrzędne może pozostawić wiadomość w spokoju, zjeść lub zmodyfikować wiadomość dla rodzica (rzadko).

Domyślna implementacja **CWnd** obsługuje następujące komunikaty i używa **onChildNotify** haka, aby umożliwić okna podrzędne (formanty) do pierwszego dostępu w wiadomości:

- **WM_MEASUREITEM** i **WM_DRAWITEM** (do samodzielnego losowania)

- **WM_COMPAREITEM** i **WM_DELETEITEM** (do samodzielnego losowania)

- **WM_HSCROLL** i **WM_VSCROLL**

- **Wm_ctlcolor**

- **WM_PARENTNOTIFY**

Można zauważyć **OnChildNotify** hak jest używany do zmiany wiadomości rysowania właściciela do self-draw wiadomości.

Oprócz **OnChildNotify** haka, przewijania wiadomości mają dalsze zachowanie routingu. Zobacz poniżej, aby uzyskać więcej informacji na temat pasków przewijania i źródeł **WM_HSCROLL** i **WM_VSCROLL** wiadomości.

## <a name="cframewnd-issues"></a>Problemy z CFrameWnd

**Klasa CFrameWnd** zapewnia większość implementacji routingu poleceń i aktualizacji interfejsu użytkownika. Jest to używane głównie dla okna ramki głównej aplikacji (**CWinApp::m_pMainWnd**), ale dotyczy wszystkich okien ramki.

Okno ramki głównej jest oknem z paskiem menu i jest elementem nadrzędnym paska stanu lub wiersza wiadomości. Zapoznaj się z powyższą dyskusją na temat routingu poleceń i **WM_INITMENUPOPUP.**

**Klasa CFrameWnd** zapewnia zarządzanie widokiem aktywnym. Następujące komunikaty są kierowane przez aktywny widok:

- Wszystkie komunikaty poleceń (aktywny widok uzyskuje do nich pierwszy dostęp).

- **WM_HSCROLL** i **WM_VSCROLL** wiadomości z pasków przewijania równorzędne (patrz poniżej).

- **WM_ACTIVATE** (i **WM_MDIACTIVATE** dla MDI) stają się wywołaniami funkcji wirtualnej **CView::OnActivateView**.

## <a name="cmdiframewndcmdichildwnd-issues"></a>Problemy z CMDIFrameWnd/CMDIChildWnd

Obie klasy okien ramek MDI pochodzą z **CFrameWnd** i dlatego są włączone dla tego samego rodzaju routingu poleceń i aktualizacji interfejsu użytkownika w **CFrameWnd**. W typowej aplikacji MDI tylko okno ramki głównej (czyli obiekt **CMDIFrameWnd)** posiada pasek menu i pasek stanu i dlatego jest głównym źródłem implementacji routingu polecenia.

Ogólny schemat routingu jest, że aktywne okno podrzędne MDI uzyskuje pierwszy dostęp do poleceń. Domyślne funkcje **PratranslateMessage** obsługują tabele akceleratora zarówno dla okien podrzędnych MDI (pierwszy) i ramki MDI (drugi), jak również standardowe akceleratory poleceń systemowych MDI zwykle obsługiwane przez **TranslateMDISysAccel** (ostatni).

## <a name="scroll-bar-issues"></a>Problemy z paskiem przewijania

Podczas obsługi wiadomości przewijania **(WM_HSCROLL**/**OnHScroll** i/lub **WM_VSCROLL**/**OnVScroll),** należy spróbować napisać kod obsługi, więc nie polegać na tym, skąd pochodzi komunikat paska przewijania. Jest to nie tylko ogólny problem systemu Windows, ponieważ komunikaty przewijania mogą pochodzić z prawdziwych formantów paska przewijania lub z **WS_HSCROLL**/**WS_VSCROLL** pasków przewijania, które nie są formantami paska przewijania.

MFC rozszerza, aby umożliwić formanty paska przewijania być podrzędne lub rodzeństwo okna przewijania (w rzeczywistości relacji nadrzędny/podrzędny między paskiem przewijania i okno przewijane może być wszystko). Jest to szczególnie ważne w przypadku udostępnionych pasków przewijania z oknami rozdzielacza. Szczegółowe informacje na temat implementacji **CSplitterWnd** znajdują się w [notatce technicznej 29,](../mfc/tn029-splitter-windows.md) w tym więcej informacji na temat problemów z udostępnionym paskiem przewijania.

Na marginesie istnieją dwie klasy pochodne **CWnd,** w których style paska przewijania określone w czasie tworzenia są zalewkowane i nie są przekazywane do systemu Windows. Po przejściu do procedury **tworzenia, WS_HSCROLL** i **WS_VSCROLL** można ustawić niezależnie, ale po utworzeniu nie można zmienić. Oczywiście nie należy bezpośrednio testować ani ustawiać bitów stylu WS_SCROLL okna, które utworzyli.

W przypadku **CMDIFrameWnd** style paska przewijania, które przekazujesz do **create** lub **LoadFrame,** są używane do tworzenia MDICLIENT. Jeśli chcesz mieć przewijany obszar MDICLIENT (np. Menedżer programów systemu Windows) należy ustawić oba style paska przewijania **(WS_HSCROLL** &#124; **WS_VSCROLL)** dla stylu używanego do tworzenia **CMDIFrameWnd**.

W przypadku **CSplitterWnd** style paska przewijania mają zastosowanie do specjalnych udostępnionych pasków przewijania dla regionów rozdzielacza. W przypadku okien podziału statycznego zwykle nie można ustawić żadnego stylu paska przewijania. W przypadku dynamicznych okien rozdzielacza zazwyczaj masz ustawiony styl paska przewijania dla kierunku, który podzielisz, to **znaczy, WS_HSCROLL,** czy można podzielić wiersze, **WS_VSCROLL,** czy można podzielić kolumny.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
