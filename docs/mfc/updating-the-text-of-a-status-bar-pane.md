---
title: Aktualizowanie tekstu w okienku paska stanu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae8b15431edbdd24a7afd6c7e25be6b9eadb4107
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081394"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Aktualizowanie tekstu w okienku paska stanu

W tym artykule wyjaśniono, jak zmienić tekst, który jest wyświetlany w okienku paska stanu w MFC. Pasek stanu — obiekt window klasy [CStatusBar](../mfc/reference/cstatusbar-class.md) — zawiera kilka "okienka." Każde okienko jest prostokątny obszar na pasku stanu, który służy do wyświetlania informacji. Na przykład wiele aplikacji wyświetlić stan włączony klawisz CAPS LOCK i NUM LOCK, innych kluczy, w okienku po prawej stronie. Aplikacje często wyświetlić tekst informacyjny w skrajnej lewej okienku (0), czasami nazywane "okienko komunikat". Na przykład pasek stanu MFC domyślny używa okienka komunikat do wyświetlenia ciągu wyjaśniające, menu aktualnie wybranego elementu lub przycisk paska narzędzi. Wartość w [paski stanu](../mfc/status-bar-implementation-in-mfc.md) wyświetlany pasek stanu, z aplikacji utworzonej przez Kreatora aplikacji MFC.

Domyślnie nie zostanie włączony MFC `CStatusBar` okienko podczas tworzenia okienka. Aby aktywować okienko, należy użyć ON_UPDATE_COMMAND_UI — makro dla każdego okienka na pasku stanu i aktualizacji okienka. Ponieważ okienka nie wysyłają komunikatów WM_COMMAND (nie są takie jak przyciski paska narzędzi), należy wpisywać kod ręcznie.

Załóżmy, że ma jedno okienko `ID_INDICATOR_PAGE` jako jego identyfikator polecenia i zawiera numer bieżącej strony w dokumencie. Poniższa procedura opisuje sposób tworzenia nowego okienka paska stanu.

### <a name="to-make-a-new-pane"></a>Aby utworzyć nowe okienko

1. Zdefiniuj identyfikator okienka polecenia.

   Na **widoku** menu, kliknij przycisk **widok zasobów**. Kliknij prawym przyciskiem myszy zasób projektu, a następnie kliknij przycisk **symboli zasobów**. W oknie dialogowym symboli zasobów kliknij pozycję `New`. Wpisz nazwę Identyfikatora polecenia: na przykład `ID_INDICATOR_PAGE`. Określ wartość dla Identyfikatora, lub zaakceptuj wartość zaproponowana przez okno dialogowe symboli zasobów. Na przykład w przypadku `ID_INDICATOR_PAGE`, zaakceptuj wartość domyślną. Zamknij okno dialogowe symboli zasobów.

1. Zdefiniuj domyślny ciąg do wyświetlenia w okienku.

   Otwórz widok zasobów, kliknij dwukrotnie **tabeli ciągów** w oknie, które wyświetla listę typów zasobów dla aplikacji. Za pomocą **tabeli ciągów** edytor jest otwarty, wybierz **nowy ciąg** z **Wstaw** menu. W oknie dialogowym właściwości ciągu wybierz identyfikator polecenia tego okienka (na przykład `ID_INDICATOR_PAGE`) i wpisz wartość domyślną ciągu, takich jak "Page". Zamknij edytor ciągów. (Należy domyślny ciąg, aby uniknąć błąd kompilatora).

1. Okienko Aby dodać *wskaźniki* tablicy.

   W pliku MAINFRM. CPP, zlokalizuj *wskaźniki* tablicy. Ta tablica zawiera listę identyfikatorów poleceń dla wszystkich wskaźników pasek stanu, w kolejności od lewej do prawej. We właściwym punkcie w tablicy, wprowadź identyfikator polecenia dla tego okienka, jak pokazano poniżej, aby uzyskać `ID_INDICATOR_PAGE`:

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

Zalecanym sposobem wyświetlania tekstu w okienku jest wywołanie `SetText` funkcji składowej klasy typu `CCmdUI` w funkcji procedury obsługi aktualizacji dla tego okienka. Na przykład możesz chcieć skonfigurować zmienną całkowitoliczbową *m_nPage* zawiera numer bieżącej strony i użyj `SetText` ustawić tekst z okienka parametry wersją tej liczby.

> [!NOTE]
>  `SetText` Podejście jest zalecane. Można to zrobić na nieco niższy poziom, wywołując `CStatusBar` funkcja elementu członkowskiego `SetPaneText`. Nawet w takim przypadku należy do obsługi aktualizacji. Bez tych program obsługi dla tego okienka MFC wyłączy okienku wymazywania jej zawartości.

Poniższa procedura pokazuje, jak używać funkcji obsługi aktualizacji do wyświetlania tekstu w okienku.

#### <a name="to-make-a-pane-display-text"></a>Aby w okienku wyświetlania tekstu

1. Dodaj program obsługi aktualizacji poleceń dla polecenia.

   Ręcznie Dodaj prototyp obsługi, jak pokazano poniżej, aby uzyskać `ID_INDICATOR_PAGE` (w MAINFRM. GODZ.):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. W odpowiedniej. CPP Dodaj program obsługi definicji, jak pokazano poniżej, aby uzyskać `ID_INDICATOR_PAGE` (w MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   Trzy ostatnie wiersze tej procedury obsługi są kod, który wyświetla tekst.

1. Na mapie odpowiedni komunikat i Dodaj ON_UPDATE_COMMAND_UI — makro, jak pokazano poniżej, aby uzyskać `ID_INDICATOR_PAGE` (w MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

Po zdefiniowaniu wartość *m_nPage* zmienną członkowską (klasy `CMainFrame`), ta metoda powoduje, że numer strony, aby w okienku są wyświetlane podczas przetwarzania bezczynności w taki sam sposób, że aplikacja aktualizuje inne wskaźniki. Jeśli *m_nPage* zmian, zmiany wyświetlania podczas następnego wykonywania pętli bezczynności.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Aktualizowanie obiektów interfejsu użytkownika (jak zaktualizować elementy menu i przycisków na pasku narzędzi, zmianami warunków program)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>Zobacz też

[Implementacja paska stanu w MFC](../mfc/status-bar-implementation-in-mfc.md)<br/>
[Klasa CStatusBar](../mfc/reference/cstatusbar-class.md)
