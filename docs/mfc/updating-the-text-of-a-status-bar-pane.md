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
ms.openlocfilehash: 20cd519f15fa9b218bca3dd1348659cfd0d5e473
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907636"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Aktualizowanie tekstu w okienku paska stanu

W tym artykule wyjaśniono, jak zmienić tekst wyświetlany w okienku paska stanu MFC. Pasek stanu — obiekt window klasy [CStatusBar](../mfc/reference/cstatusbar-class.md) — zawiera kilka "okienek". Każde okienko jest prostokątnym obszarem paska stanu, którego można użyć do wyświetlania informacji. Na przykład wiele aplikacji wyświetla stan Caps Lock, NUM LOCK i innych kluczy w okienku po prawej stronie. Aplikacje często wyświetlają tekst informacyjny w okienku po lewej stronie (okienko 0), czasami nazywane "okienkiem wiadomości". Na przykład domyślny pasek stanu MFC używa okienka wiadomości, aby wyświetlić ciąg objaśniający aktualnie wybrany element menu lub przycisk paska narzędzi. Rysunek w [paskach stanu](../mfc/status-bar-implementation-in-mfc.md) pokazuje pasek stanu z aplikacji MFC utworzonej przez Kreatora aplikacji.

Domyślnie MFC nie włącza `CStatusBar` okienka podczas tworzenia okienka. Aby uaktywnić okienko, należy użyć makra ON_UPDATE_COMMAND_UI dla każdego okienka na pasku stanu i zaktualizować okienka. Ponieważ okienka nie wysyłają wiadomości WM_COMMAND (nie są one podobne do przycisków paska narzędzi), należy wpisać kod ręcznie.

Załóżmy na przykład, że jedno okienko ma `ID_INDICATOR_PAGE` jako identyfikator polecenia i zawiera bieżący numer strony w dokumencie. Poniższa procedura opisuje sposób tworzenia nowego okienka na pasku stanu.

### <a name="to-make-a-new-pane"></a>Aby utworzyć nowe okienko

1. Zdefiniuj identyfikator polecenia okienka.

   W menu **Widok** kliknij **Widok zasobów**. Kliknij prawym przyciskiem myszy zasób projektu i kliknij pozycję **symbole zasobów**. W oknie dialogowym symbole zasobów kliknij pozycję `New`. Wpisz nazwę identyfikatora polecenia: na przykład `ID_INDICATOR_PAGE`. Określ wartość dla identyfikatora lub Zaakceptuj wartość sugerowaną przez okno dialogowe symbole zasobów. Na przykład dla `ID_INDICATOR_PAGE`, Zaakceptuj wartość domyślną. Zamknij okno dialogowe symbole zasobów.

1. Zdefiniuj domyślny ciąg, który ma być wyświetlany w okienku.

   Przy otwartym Widok zasobów kliknij dwukrotnie pozycję **tabela ciągów** w oknie, która zawiera listę typów zasobów aplikacji. Po otwarciu edytora **tabeli ciągów** wybierz **Nowy ciąg** z menu **Wstaw** . Wybierz identyfikator polecenia okienka (na przykład `ID_INDICATOR_PAGE`), a następnie wpisz wartość domyślną ciągu, na przykład "Strona". Zamknij Edytor ciągów. (Do uniknięcia błędu kompilatora wymagany jest ciąg domyślny).

1. Dodaj okienko do tablicy *wskaźniki* .

   W pliku MAINFRM. CPP Znajdź tablicę *wskaźników* . Ta tablica zawiera identyfikatory poleceń dla wszystkich wskaźników paska stanu, w kolejności od lewej do prawej. W odpowiednim punkcie tablicy wprowadź identyfikator polecenia Twojego okienka, jak pokazano poniżej `ID_INDICATOR_PAGE`:

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

Zalecanym sposobem wyświetlania tekstu w okienku jest wywołanie `SetText` funkcji składowej klasy `CCmdUI` w funkcji procedury obsługi aktualizacji dla tego okienka. Na przykład możesz chcieć skonfigurować zmienną *m_nPage* , która zawiera bieżący numer strony i użyć `SetText` do ustawienia tekstu w okienku na wersję ciągu tego numeru.

> [!NOTE]
>  Zalecane `SetText` jest podejście. To zadanie można wykonać na nieco niższym poziomie, wywołując `CStatusBar` funkcję `SetPaneText`członkowską. Nawet dlatego potrzebna jest procedura obsługi aktualizacji. Bez takiego programu obsługi dla okienka MFC automatycznie wyłącza okienko, wymazywanie jego zawartości.

Poniższa procedura pokazuje, jak używać funkcji obsługi aktualizacji do wyświetlania tekstu w okienku.

#### <a name="to-make-a-pane-display-text"></a>Aby wyświetlić tekst w okienku

1. Dodaj procedurę obsługi aktualizacji polecenia dla polecenia.

   Dodaj ręcznie prototyp do programu obsługi, jak pokazano tutaj `ID_INDICATOR_PAGE` (w MainFrm. H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. W odpowiednich przypadkach. CPP plik, Dodaj definicję programu obsługi, jak pokazano tutaj `ID_INDICATOR_PAGE` (w MainFrm. CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   Ostatnie trzy wiersze tej procedury obsługi to kod, który wyświetla tekst.

1. W odpowiedniej mapie komunikatów Dodaj makro ON_UPDATE_COMMAND_UI, jak pokazano poniżej `ID_INDICATOR_PAGE` (w MainFrm. CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

Po zdefiniowaniu wartości zmiennej składowej *m_nPage* (klasy `CMainFrame`) Ta technika powoduje, że numer strony pojawi się w okienku podczas przetwarzania bezczynności w taki sam sposób, w jaki aplikacja aktualizuje inne wskaźniki. W przypadku zmiany *m_nPage* wyświetlania zmiany w następnej pętli bezczynności.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Aktualizowanie obiektów interfejsu użytkownika (jak aktualizować przyciski paska narzędzi i elementy menu jako zmiany warunków programu)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>Zobacz także

[Implementacja paska stanu w MFC](../mfc/status-bar-implementation-in-mfc.md)<br/>
[Klasa CStatusBar](../mfc/reference/cstatusbar-class.md)
