---
title: Obsługa powiadomień dotyczących dostosowania
ms.date: 11/04/2016
f1_keywords:
- TBN_CUSTHELP
- TBN_QUERYINSERT
- TBNOTIFY
- NMHDR
- TBN_TOOLBARCHANGE
- TBN_ENDDRAG
- NM_SETFOCUS
- TBN_RESET
- NM_RETURN
- NM_ENDWAIT
- NM_STARTWAIT
- TBN_BEGINDRAG
- NM_OUTOFMEMORY
- TBN_QUERYDELETE
- NM_DBLCLK
- TBN_ENDADJUST
- NM_KILLFOCUS
- NM_RCLICK
- TBN_BEGINADJUST
- NM_CLICK
helpviewer_keywords:
- TBN_ENDADJUST notification [MFC]
- TBNOTIFY notification [MFC]
- TBN_BEGINDRAG notification [MFC]
- TBN_TOOLBARCHANGE notification [MFC]
- NM_CLICK notification [MFC]
- NM_RETURN notification [MFC]
- NM_RCLICK notification [MFC]
- TBN_ENDDRAG notification [MFC]
- TBN_BEGINADJUST notification [MFC]
- NM_ENDWAIT notification [MFC]
- NM_KILLFOCUS notification [MFC]
- NM_SETFOCUS notification [MFC]
- NM_OUTOFMEMORY notification [MFC]
- TBN_QUERYINSERT notification [MFC]
- NMHDR [MFC]
- NM_STARTWAIT notification [MFC]
- CToolBarCtrl class [MFC], handling notifications
- TBN_CUSTHELP notification [MFC]
- TBN_RESET notification [MFC]
- NM_DBLCLK notification [MFC]
- TBN_QUERYDELETE notification [MFC]
- NM_RDBLCLK notification [MFC]
- TBN_GETBUTTONINFO notification [MFC]
ms.assetid: 219ea08e-7515-4b98-85cb-47120f08c0a2
ms.openlocfilehash: 67f40d0dc50a853a39cb9b60a938d8eafe8293c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370486"
---
# <a name="handling-customization-notifications"></a>Obsługa powiadomień dotyczących dostosowania

Wspólny kontrolka paska narzędzi systemu Windows zawiera wbudowane funkcje dostosowywania, w tym okno dialogowe dostosowywania zdefiniowane przez system, które umożliwia użytkownikowi wstawianie, usuwanie lub zmienianie rozmieszczenia przycisków paska narzędzi. Aplikacja określa, czy funkcje dostosowywania są dostępne i kontroluje stopień, w jakim użytkownik może dostosować pasek narzędzi.

Te funkcje dostosowywania można udostępnić użytkownikowi, nadając pasowi narzędzi **styl CCS_ADJUSTABLE.** Funkcje dostosowywania umożliwiają użytkownikowi przeciąganie przycisku w nowe miejsce lub usunięcie przycisku przez przeciągnięcie go poza pasek narzędzi. Ponadto użytkownik może kliknąć dwukrotnie pasek narzędzi, aby wyświetlić okno dialogowe **Dostosowywanie paska narzędzi,** które umożliwia użytkownikowi dodawanie, usuwanie i zmienianie rozmieszczenia przycisków paska narzędzi. Aplikacja może wyświetlać okno dialogowe za pomocą funkcji Dostosuj element [członkowski.](../mfc/reference/ctoolbarctrl-class.md#customize)

Formant paska narzędzi wysyła komunikaty powiadomień do okna nadrzędnego na każdym kroku w procesie dostosowywania. Jeśli użytkownik przytrzymuje klawisz SHIFT w dół i zaczyna przeciągać przycisk, pasek narzędzi automatycznie obsługuje operację przeciągania. Pasek narzędzi wysyła komunikat powiadomienia **TBN_QUERYDELETE** do okna nadrzędnego, aby ustalić, czy przycisk może zostać usunięty. Operacja przeciągania kończy się, jeśli okno nadrzędne zwraca **wartość FAŁSZ**. W przeciwnym razie pasek narzędzi przechwytuje dane wejściowe myszy i czeka na zwolnienie przycisku myszy przez użytkownika.

Gdy użytkownik zwalnia przycisk myszy, formant paska narzędzi określa położenie kursora myszy. Jeśli kursor znajduje się poza paskiem narzędzi, przycisk zostanie usunięty. Jeśli kursor znajduje się na innym przycisku paska narzędzi, pasek narzędzi wysyła komunikat powiadomienia **TBN_QUERYINSERT** do okna nadrzędnego, aby ustalić, czy przycisk może zostać wstawiony po lewej stronie danego przycisku. Przycisk zostanie wstawiony, jeśli okno nadrzędne zwraca **wartość PRAWDA**; w przeciwnym razie tak nie jest. Pasek narzędzi wysyła komunikat powiadomienia **TBN_TOOLBARCHANGE,** aby zasygnalizować koniec operacji przeciągania.

Jeśli użytkownik rozpocznie operację przeciągania bez przytrzymywalania klawisza SHIFT, kontrolka paska narzędzi wysyła komunikat powiadomienia **TBN_BEGINDRAG** do okna właściciela. Aplikacja, która implementuje swój własny kod przeciągania przycisków można użyć tego komunikatu jako sygnał, aby rozpocząć operację przeciągania. Pasek narzędzi wysyła komunikat powiadomienia **TBN_ENDDRAG,** aby zasygnalizować koniec operacji przeciągania.

Formant paska narzędzi wysyła komunikaty powiadomień, gdy użytkownik dostosowuje pasek narzędzi za pomocą okna dialogowego **Dostosowywanie paska narzędzi.** Pasek narzędzi wysyła komunikat powiadomienia **TBN_BEGINADJUST** po dwukrotnym kliknięciu paska narzędzi, ale przed utworzeniem okna dialogowego. Następnie pasek narzędzi rozpoczyna wysyłanie serii komunikatów powiadomień **TBN_QUERYINSERT,** aby ustalić, czy pasek narzędzi umożliwia wstawienie przycisków. Gdy okno nadrzędne zwraca **wartość PRAWDA,** pasek narzędzi przestaje wysyłać **TBN_QUERYINSERT** komunikaty powiadomień. Jeśli okno nadrzędne nie zwraca **funkcji PRAWDA** dla dowolnego przycisku, pasek narzędzi spowoduje zniszczenie okna dialogowego.

Następnie formant paska narzędzi określa, czy przyciski mogą zostać usunięte z paska narzędzi, wysyłając jeden komunikat powiadomienia **TBN_QUERYDELETE** dla każdego przycisku na pasku narzędzi. Okno nadrzędne zwraca **wartość PRAWDA,** aby wskazać, że przycisk może zostać usunięty; w przeciwnym razie zwraca **wartość FAŁSZ**. Pasek narzędzi dodaje wszystkie przyciski paska narzędzi do okna dialogowego, ale zaszywa te, które nie mogą zostać usunięte.

Za każdym razem, gdy formant paska narzędzi potrzebuje informacji o przycisku w oknie dialogowym Dostosuj pasek narzędzi, wysyła komunikat powiadomienia **TBN_GETBUTTONINFO,** określając indeks przycisku, dla którego potrzebuje informacji i adres struktury **TBNOTIFY.** Okno nadrzędne musi wypełnić strukturę odpowiednimi informacjami.

Okno dialogowe **Dostosowywanie paska narzędzi** zawiera przycisk Pomocy i przycisk Resetuj. Gdy użytkownik wybierze przycisk Pomoc, kontrolka paska narzędzi wysyła komunikat powiadomienia **TBN_CUSTHELP.** Okno nadrzędne powinno odpowiadać, wyświetlając informacje pomocy. Okno dialogowe wysyła komunikat powiadomienia **TBN_RESET,** gdy użytkownik wybierze przycisk Resetuj. Ten komunikat sygnalizuje, że pasek narzędzi ma zamiar ponownie zainicjować okno dialogowe.

Te wiadomości są **WM_NOTIFY** wiadomości i mogą być obsługiwane w oknie właściciela, dodając wpisy mapy wiadomości w następującym formularzu do mapy wiadomości okna właściciela:

```cpp
ON_NOTIFY( wNotifyCode, idControl, memberFxn )
```

- **wNotifyCode**

   Kod identyfikatora wiadomości powiadomień, taki jak **TBN_BEGINADJUST**.

- **kontrola id**

   Identyfikator formantu wysyłającego powiadomienie.

- **członekFxn**

   Funkcja elementu członkowskiego, która ma zostać wywołana po otrzymaniu tego powiadomienia.

Funkcja członka zostanie zadeklarowana za pomocą następującego prototypu:

```cpp
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );
```

Jeśli program obsługi komunikatów powiadomień zwraca wartość, należy umieścić ją w **LRESULT** wskazywał przez *wynik*.

Dla każdej `pNotifyStruct` wiadomości wskazuje strukturę **NMHDR** lub **TBNOTIFY.** Struktury te są opisane poniżej:

Struktura **NMHDR** zawiera następujące elementy członkowskie:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;  // handle of control sending message
    UINT idFrom;// identifier of control sending message
    UINT code;  // notification code; see below
} NMHDR;
```

- **hwndOd**

   Dojście okna formantu, który wysyła powiadomienie. Aby przekonwertować `CWnd` ten uchwyt na wskaźnik, użyj [CWnd::FromHandle](../mfc/reference/cwnd-class.md#fromhandle).

- **idFrom**

   Identyfikator formantu wysyłającego powiadomienie.

- **Kod**

   Kod powiadomienia. Ten element członkowski może być wartością specyficzną dla typu formantu, taką jak **TBN_BEGINADJUST** lub **TTN_NEEDTEXT,** lub może być jedną ze wspólnych wartości powiadomień wymienionych poniżej:

  - **NM_CLICK** Użytkownik kliknął lewy przycisk myszy w formancie.

  - **NM_DBLCLK** Użytkownik dwukrotnie kliknął lewy przycisk myszy w formancie.

  - **NM_KILLFOCUS** Formant utracił fokus wejściowy.

  - **NM_OUTOFMEMORY** Formant nie może ukończyć operację, ponieważ nie ma wystarczającej ilości pamięci.

  - **NM_RCLICK** Użytkownik kliknął prawy przycisk myszy w formancie.

  - **NM_RDBLCLK** Użytkownik dwukrotnie kliknął prawy przycisk myszy w formancie.

  - **NM_RETURN** Formant ma fokus wejściowy, a użytkownik nacisnął klawisz ENTER.

  - **NM_SETFOCUS** Formant otrzymał fokus wejściowy.

Struktura **TBNOTIFY** zawiera następujące elementy członkowskie:

```cpp
typedef struct {
    NMHDR hdr; // information common to all WM_NOTIFY messages
    int iItem; // index of button associated with notification
    TBBUTTON tbButton; // info about button associated withnotification
    int cchText;   // count of characters in button text
    LPSTR lpszText;// address of button text
} TBNOTIFY, FAR* LPTBNOTIFY;
```

- **Hdr**

   Informacje wspólne dla wszystkich **wiadomości WM_NOTIFY.**

- **Iitem**

   Indeks przycisku skojarzony z powiadomieniem.

- **tbButton (przycisk)**

   **Struktura TBBUTTON,** która zawiera informacje o przycisku paska narzędzi skojarzonego z powiadomieniem.

- **cchTekst**

   Liczba znaków w tekście przycisku.

- **lpszText (tekst)**

   Wskaźnik do tekstu przycisku.

Powiadomienia wysyłane przez pasek narzędzi są następujące:

- **TBN_BEGINADJUST**

   Wysyłane, gdy użytkownik rozpoczyna dostosowywanie kontrolki paska narzędzi. Wskaźnik wskazuje strukturę **NMHDR,** która zawiera informacje o powiadomieniu. Program obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_BEGINDRAG**

   Wysyłane, gdy użytkownik zaczyna przeciągać przycisk w formancie paska narzędzi. Wskaźnik wskazuje na **tbnotify** struktury. Element członkowski **iItem** zawiera indeks oparty na wartości zerowej przeciąganego przycisku. Program obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_CUSTHELP**

   Wysyłane, gdy użytkownik wybierze przycisk Pomoc w oknie dialogowym Dostosowywanie paska narzędzi. Brak wartości zwracanej. Wskaźnik wskazuje strukturę **NMHDR,** która zawiera informacje o komunikacie o powiadomieniu. Program obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_ENDADJUST**

   Wysyłane, gdy użytkownik przestaje dostosowywać kontrolkę paska narzędzi. Wskaźnik wskazuje strukturę **NMHDR,** która zawiera informacje o komunikacie o powiadomieniu. Program obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_ENDDRAG**

   Wysyłane, gdy użytkownik przestaje przeciągać przycisk w formancie paska narzędzi. Wskaźnik wskazuje na **tbnotify** struktury. Element członkowski **iItem** zawiera indeks oparty na wartości zerowej przeciąganego przycisku. Program obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_GETBUTTONINFO**

   Wysyłane, gdy użytkownik dostosowuje kontrolkę paska narzędzi. Pasek narzędzi używa tego komunikatu powiadomienia do pobierania informacji potrzebnych w oknie dialogowym Dostosowywanie paska narzędzi. Wskaźnik wskazuje na **tbnotify** struktury. Element **członkowski iItem** określa indeks oparty na wartości zerowej przycisku. Członkowie **pszText** i **cchText** określają adres i długość, w znakach, bieżącego tekstu przycisku. Aplikacja powinna wypełnić strukturę informacjami o przycisku. Zwraca **wartość TRUE,** jeśli informacje o przyciskach zostały skopiowane do struktury lub **FAŁSZ w** inny sposób.

- **TBN_QUERYDELETE**

   Wysyłane, gdy użytkownik dostosowuje pasek narzędzi, aby ustalić, czy przycisk może zostać usunięty z kontrolki paska narzędzi. Wskaźnik wskazuje na **tbnotify** struktury. Element **członkowski iItem** zawiera indeks oparty na wartości zero przycisku do usunięcia. Wróć **TRUE,** aby zezwolić na usunięcie przycisku lub **fałsz,** aby zapobiec usunięciu przycisku.

- **TBN_QUERYINSERT**

   Wysyłane, gdy użytkownik dostosowuje formant paska narzędzi, aby ustalić, czy przycisk może być włożony po lewej stronie danego przycisku. Wskaźnik wskazuje na **tbnotify** struktury. Element członkowski **iItem** zawiera indeks oparty na wartości zerowej przycisku, który ma zostać wstawiony. Powrót **TRUE,** aby umożliwić wstawienie przycisku przed danym przyciskiem lub **FALSE,** aby zapobiec włożeniu przycisku.

- **TBN_RESET**

   Wysyłane, gdy użytkownik resetuje zawartość okna dialogowego Dostosowywanie paska narzędzi. Wskaźnik wskazuje strukturę **NMHDR,** która zawiera informacje o komunikacie o powiadomieniu. Program obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_TOOLBARCHANGE**

   Wysyłane po dostosowaniu kontrolki paska narzędzi przez użytkownika. Wskaźnik wskazuje strukturę **NMHDR,** która zawiera informacje o komunikacie o powiadomieniu. Program obsługi nie musi zwracać żadnej określonej wartości.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
