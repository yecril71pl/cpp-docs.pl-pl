---
title: Aktualizowanie tekstu w okienku paska stanu
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- ON_UPDATE_COMMAND_UI macro [MFC]
- user interface objects [MFC], updating
- text, status bar
- CStatusBar class [MFC], updating
- SetText method [MFC]
- panes, status bar
- status bars [MFC], updating
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
ms.openlocfilehash: 723046fc1721cc46608e00f19a4431ef081be13d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366695"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Aktualizowanie tekstu w okienku paska stanu

W tym artykule wyjaśniono, jak zmienić tekst, który pojawia się w okienku stanu MFC. Pasek stanu — obiekt okna klasy [CStatusBar](../mfc/reference/cstatusbar-class.md) — zawiera kilka "okienek". Każde okienko jest prostokątnym obszarem paska stanu, którego można używać do wyświetlania informacji. Na przykład wiele aplikacji wyświetla stan CAPS LOCK, NUM LOCK i innych klawiszy w okienkach po prawej stronie. Aplikacje często wyświetlają również tekst informacyjny w okienku po lewej stronie (okienko 0), czasami nazywany "okienkiem wiadomości". Na przykład domyślny pasek stanu MFC używa okienka komunikatów do wyświetlenia ciągu wyjaśniającego aktualnie zaznaczony element menu lub przycisk paska narzędzi. Rysunek w [paskach stanu](../mfc/status-bar-implementation-in-mfc.md) pokazuje pasek stanu z aplikacji MFC utworzonej przez Kreatora aplikacji.

Domyślnie MFC nie włącza `CStatusBar` okienka podczas tworzenia okienka. Aby uaktywnić okienko, należy użyć makra ON_UPDATE_COMMAND_UI dla każdego okienka na pasku stanu i zaktualizować okienka. Ponieważ okienka nie wysyłają WM_COMMAND wiadomości (nie są one jak przyciski paska narzędzi), należy wpisać kod ręcznie.

Załóżmy na przykład, `ID_INDICATOR_PAGE` że jedno okienko ma jako identyfikator polecenia i że zawiera bieżący numer strony w dokumencie. W poniższej procedurze opisano sposób tworzenia nowego okienka na pasku stanu.

### <a name="to-make-a-new-pane"></a>Aby zrobić nowe okienko

1. Zdefiniuj identyfikator polecenia okienka.

   W menu **Widok** kliknij polecenie **Widok zasobów**. Kliknij prawym przyciskiem myszy zasób projektu i kliknij polecenie **Symbole zasobów**. W oknie dialogowym Symbole `New`zasobów kliknij przycisk . Wpisz nazwę identyfikatora polecenia: `ID_INDICATOR_PAGE`na przykład . Określ wartość identyfikatora lub zaakceptuj wartość sugerowaną w oknie dialogowym Symbole zasobów. Na przykład `ID_INDICATOR_PAGE`dla , zaakceptuj wartość domyślną. Zamknij okno dialogowe Symbole zasobów.

1. Zdefiniuj domyślny ciąg do wyświetlenia w okienku.

   Po otwarciu widoku zasobów kliknij dwukrotnie pozycję **Tabela ciągów** w oknie zawierającym listę typów zasobów dla aplikacji. Po otwarciu **edytora tabeli ciągów** wybierz polecenie **Nowy ciąg** z menu **Wstaw.** Wybierz identyfikator polecenia okienka (na `ID_INDICATOR_PAGE`przykład) i wpisz domyślną wartość ciągu, taką jak "Strona". Zamknij edytor ciągów. (Aby uniknąć błędu kompilatora, potrzebny jest domyślny ciąg znaków.

1. Dodaj okienko do *tablicy wskaźników.*

   W pliku MAINFRM. CPP, zlokalizuj tablicę *wskaźników.* Ta tablica zawiera listę identyfikatorów poleceń dla wszystkich wskaźników paska stanu w kolejności od lewej do prawej. W odpowiednim punkcie tablicy wprowadź identyfikator polecenia okienka, jak pokazano `ID_INDICATOR_PAGE`poniżej dla:

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

Zalecanym sposobem wyświetlania tekstu w okienku `SetText` jest wywołanie funkcji elementu członkowskiego klasy `CCmdUI` w funkcji programu obsługi aktualizacji dla okienka. Na przykład można skonfigurować zmienną całkowitą *m_nPage,* która zawiera bieżący numer `SetText` strony i użyć do ustawienia tekstu okienka na wersję ciągu tej liczby.

> [!NOTE]
> Podejście `SetText` jest zalecane. Możliwe jest wykonanie tego zadania na nieco niższym `SetPaneText`poziomie, wywołując funkcję `CStatusBar` elementu członkowskiego . Mimo to nadal potrzebujesz obsługi aktualizacji. Bez takiego programu obsługi dla okienka MFC automatycznie wyłącza okienko, wymazując jego zawartość.

Poniższa procedura pokazuje, jak używać funkcji programu obsługi aktualizacji do wyświetlania tekstu w okienku.

#### <a name="to-make-a-pane-display-text"></a>Aby wyświetlić tekst w okienku

1. Dodaj program obsługi aktualizacji polecenia dla polecenia.

   Ręcznie dodaj prototyp dla obsługi, jak pokazano `ID_INDICATOR_PAGE` tutaj (w MAINFRM. H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. W odpowiednim . CPP, dodaj definicję programu obsługi, jak `ID_INDICATOR_PAGE` pokazano tutaj (w MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   Ostatnie trzy wiersze tego programu obsługi to kod, który wyświetla tekst.

1. Na odpowiedniej mapie komunikatów dodaj makro ON_UPDATE_COMMAND_UI, jak `ID_INDICATOR_PAGE` pokazano tutaj (w MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

Po zdefiniowaniu wartości *zmiennej m_nPage* elementu członkowskiego `CMainFrame`(klasy), ta technika powoduje, że numer strony pojawia się w okienku podczas bezczynnego przetwarzania w taki sam sposób, w jaki aplikacja aktualizuje inne wskaźniki. Jeśli *m_nPage* się zmieni, wyświetlacz zmieni się podczas następnej pętli bezczynnej.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Aktualizowanie obiektów interfejsu użytkownika (jak zaktualizować przyciski paska narzędzi i elementy menu w miarę zmiany warunków programu)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>Zobacz też

[Implementacja paska stanu w MFC](../mfc/status-bar-implementation-in-mfc.md)<br/>
[Klasa CStatusBar](../mfc/reference/cstatusbar-class.md)
