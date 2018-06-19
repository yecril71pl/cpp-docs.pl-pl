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
ms.openlocfilehash: dbb2f14f274be3c7282a897c271049fe46434f3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384481"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Aktualizowanie tekstu w okienku paska stanu
W tym artykule wyjaśniono, jak zmienić tekst wyświetlany w okienku paska stanu MFC. Pasek stanu — obiekt window klasy [cstatusbar —](../mfc/reference/cstatusbar-class.md) — zawiera kilka "okienka." Każdy okienko jest prostokątny obszar paska stanu, który służy do wyświetlania informacji. Na przykład wiele aplikacji wyświetlany stan włączony klawisz CAPS LOCK, NUM LOCK i innych kluczy w okienku po prawej stronie. Aplikacje również często jest wyświetlany tekst informacyjny w okienku po lewej stronie (okienko 0), nazywane czasem "okienko komunikat". Na przykład domyślny pasek stanu MFC używa okienku komunikat do wyświetlenia ciąg wyjaśniający menu obecnie wybranego elementu lub przycisku paska narzędzi. Wartość w [pasków stanu](../mfc/status-bar-implementation-in-mfc.md) Wyświetla pasek stanu z aplikacji utworzone przez Kreatora aplikacji MFC.  
  
 Domyślnie nie są włączone MFC `CStatusBar` okienko podczas tworzenia okienka. Aby aktywować okienko, należy użyć `ON_UPDATE_COMMAND_UI` makro dla każdego stanu pasek i zaktualizuj okienka. Ponieważ okienka nie wysyłaj **WM_COMMAND** wiadomości (nie są takie jak przyciski paska narzędzi), należy wpisać kod ręcznie.  
  
 Na przykład, załóżmy, że ma jedno okienko `ID_INDICATOR_PAGE` jako identyfikatora polecenia i zawiera numer bieżącej strony w dokumencie. Poniższa procedura opisuje sposób tworzenia nowego okienka na pasku stanu.  
  
### <a name="to-make-a-new-pane"></a>Aby utworzyć nowe okienko  
  
1.  Zdefiniuj identyfikator okienku polecenia.  
  
     Na **widoku** menu, kliknij przycisk **widok zasobów**. Kliknij prawym przyciskiem myszy zasób projektu, a następnie kliknij przycisk **symbole zasobu**. W oknie dialogowym symbole zasobów, kliknij przycisk `New`. Wpisz nazwę Identyfikatora polecenia: na przykład `ID_INDICATOR_PAGE`. Określ wartość dla Identyfikatora, lub zaakceptuj wartość zasugerowany przez okno dialogowe symboli zasobów. Na przykład w przypadku `ID_INDICATOR_PAGE`, zaakceptuj wartość domyślną. Zamknij okno dialogowe symboli zasobów.  
  
2.  Zdefiniuj domyślny ciąg do wyświetlania w okienku.  
  
     Otwórz widok zasobów, kliknij dwukrotnie **tabeli ciągów** w oknie, który wyświetla listę typów zasobów dla aplikacji. Z **tabeli ciągów** edytor jest otwarty, wybierz **nowe parametry** z **Wstaw** menu. W oknie właściwości ciągu wybierz identyfikator polecenia tego okienka (na przykład `ID_INDICATOR_PAGE`) i wpisać domyślne wartości ciągu, takich jak "Page". Zamknij edytor ciągów. (Należy domyślny ciąg, aby uniknąć błędów kompilatora).  
  
3.  Okienko, aby dodać **wskaźniki** tablicy.  
  
     W pliku MAINFRM. CPP, zlokalizuj **wskaźniki** tablicy. Ta tablica zawiera identyfikatory poleceń dla wszystkich wskaźników na pasku stanu, w kolejności od lewej do prawej. We właściwym momencie w tablicy, wprowadź identyfikator polecenia dla tego okienka, jak pokazano poniżej, aby uzyskać `ID_INDICATOR_PAGE`:  
  
     [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]  
  
 Jest to zalecany sposób wyświetlania tekstu w okienku do wywołania **SetText** funkcji członkowskiej klasy `CCmdUI` w funkcji obsługi aktualizacji dla tego okienka. Na przykład można skonfigurować zmienna całkowitoliczbowa `m_nPage` zawierający numer bieżącej strony i użyj **SetText** można ustawić okienko tekstu do tego numeru wersji ciągu.  
  
> [!NOTE]
>  **SetText** podejście jest zalecane. Istnieje możliwość wykonania tego zadania w nieco niższy poziom wywołując `CStatusBar` funkcji członkowskiej `SetPaneText`. Mimo tego nadal potrzebujesz programu obsługi aktualizacji. Bez takiej obsługi dla tego okienka MFC automatycznie wyłącza okienku wymazywania jej zawartości.  
  
 Poniższa procedura przedstawia sposób użycia funkcji obsługi aktualizacji do wyświetlania tekstu w okienku.  
  
#### <a name="to-make-a-pane-display-text"></a>Aby okienko wyświetlania tekstu  
  
1.  Dodaj program obsługi aktualizacji poleceń dla polecenia.  
  
     Ręcznie Dodaj prototyp obsługi, jak pokazano poniżej, aby uzyskać `ID_INDICATOR_PAGE` (w MAINFRM. H):  
  
     [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]  
  
2.  W odpowiednich. CPP plików, Dodaj program obsługi definicji, jak pokazano poniżej, aby uzyskać `ID_INDICATOR_PAGE` (w MAINFRM. CPP):  
  
     [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]  
  
     Trzy ostatnie wiersze tego programu obsługi są kod, który wyświetla tekst.  
  
3.  W planie odpowiedni komunikat dodać `ON_UPDATE_COMMAND_UI` makra, jak pokazano poniżej, aby uzyskać `ID_INDICATOR_PAGE` (w MAINFRM. CPP):  
  
     [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]  
  
 Po zdefiniowaniu wartość `m_nPage` zmiennej członkowskiej (klasy `CMainFrame`), ta metoda powoduje, że numer strony, aby są wyświetlane w okienku podczas przetwarzania bezczynności w taki sam sposób, że aplikacja aktualizuje innych wskaźników. Jeśli `m_nPage` zmian, zmiany wyświetlania podczas następnego pętli bezczynności.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Aktualizowanie obiektów interfejsu użytkownika (jak zaktualizować przycisków paska narzędzi i elementów menu jako program warunków zmian)](../mfc/how-to-update-user-interface-objects.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Implementacja paska stanu w MFC](../mfc/status-bar-implementation-in-mfc.md)   
 [Klasa CStatusBar](../mfc/reference/cstatusbar-class.md)
