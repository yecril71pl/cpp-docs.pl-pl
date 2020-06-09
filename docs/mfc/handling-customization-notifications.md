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
ms.openlocfilehash: d88e1efe12fd5b31a9f78b8fe439ba1aefa72d1e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625727"
---
# <a name="handling-customization-notifications"></a>Obsługa powiadomień dotyczących dostosowania

Typowy formant paska narzędzi systemu Windows ma wbudowane funkcje dostosowywania, w tym okno dialogowe dostosowywania zdefiniowane przez system, które umożliwia użytkownikowi Wstawianie, usuwanie lub zmienianie rozmieszczenia przycisków paska narzędzi. Aplikacja określa, czy funkcje dostosowywania są dostępne, oraz określa zakres, do którego użytkownik może dostosować pasek narzędzi.

Te funkcje dostosowywania można udostępnić użytkownikowi, podając pasek narzędzi styl **CCS_ADJUSTABLE** . Funkcje dostosowywania umożliwiają użytkownikowi przeciąganie przycisku w nowe położenie lub usuwanie przycisku, przeciągając go poza pasek narzędzi. Ponadto użytkownik może kliknąć dwukrotnie pasek narzędzi, aby wyświetlić okno dialogowe **Dostosowywanie paska narzędzi** , które pozwala użytkownikowi dodawać, usuwać i zmieniać rozmieszczenie przycisków paska narzędzi. Aplikacja może wyświetlić okno dialogowe przy użyciu funkcji [dostosowywania](reference/ctoolbarctrl-class.md#customize) elementu członkowskiego.

Kontrolka paska narzędzi wysyła komunikaty powiadomień do okna nadrzędnego w każdym kroku w procesie dostosowywania. Jeśli użytkownik utrzymuje klawisz SHIFT i rozpocznie przeciąganie przycisku, pasek narzędzi automatycznie obsługuje operację przeciągania. Pasek narzędzi wysyła komunikat powiadomienia o **TBN_QUERYDELETE** do okna nadrzędnego, aby określić, czy przycisk może zostać usunięty. Operacja przeciągania zostaje zakończona, jeśli okno nadrzędne zwróci **wartość false**. W przeciwnym razie pasek narzędzi przechwytuje dane wejściowe myszy i czeka, aż użytkownik zwolni przycisk myszy.

Gdy użytkownik zwolni przycisk myszy, formant Toolbar określa lokalizację kursora myszy. Jeśli kursor znajduje się poza paskiem narzędzi, przycisk jest usuwany. Jeśli kursor znajduje się na innym przycisku paska narzędzi, pasek narzędzi wysyła komunikat powiadomienia o **TBN_QUERYINSERT** do okna nadrzędnego, aby określić, czy przycisk może zostać wstawiony po lewej stronie danego przycisku. Przycisk zostanie wstawiony, jeśli okno nadrzędne zwróci **wartość PRAWDA**; w przeciwnym razie nie jest. Pasek narzędzi wysyła **TBN_TOOLBARCHANGE** komunikat powiadomienia, aby sygnalizować koniec operacji przeciągania.

Jeśli użytkownik rozpocznie operację przeciągania bez przytrzymywania klawisza SHIFT, formant Toolbar wyśle **TBN_BEGINDRAG** komunikat powiadomienia do okna właściciela. Aplikacja, która implementuje własny kod do przeciągania, może używać tego komunikatu jako sygnału do rozpoczęcia operacji przeciągania. Pasek narzędzi wysyła **TBN_ENDDRAG** komunikat powiadomienia, aby sygnalizować koniec operacji przeciągania.

Kontrolka paska narzędzi wysyła komunikaty powiadomień, gdy użytkownik dostosowuje pasek narzędzi przy użyciu okna dialogowego **Dostosuj pasek narzędzi** . Pasek narzędzi wysyła **TBN_BEGINADJUST** komunikat powiadomienia po dwukrotnym kliknięciu paska narzędzi przez użytkownika, ale przed utworzeniem okna dialogowego. Następnie na pasku narzędzi rozpocznie się wysyłanie serii **TBN_QUERYINSERT** komunikatów powiadomień, aby określić, czy pasek narzędzi umożliwia wstawianie przycisków. Gdy okno nadrzędne zwróci **wartość true**, pasek narzędzi przestaje wysyłać **TBN_QUERYINSERT** komunikaty powiadomień. Jeśli okno nadrzędne nie zwraca **wartości true** dla dowolnego przycisku, pasek narzędzi niszczy okno dialogowe.

Następnie formant Toolbar określa, czy dowolne przyciski mogą zostać usunięte z paska narzędzi, wysyłając jeden **TBN_QUERYDELETE** komunikat powiadomienia dla każdego przycisku na pasku narzędzi. Okno nadrzędne zwraca **wartość true** , aby wskazać, że przycisk może zostać usunięty; w przeciwnym razie zwraca **wartość false**. Pasek narzędzi dodaje wszystkie przyciski paska narzędzi do okna dialogowego, ale szare, które nie mogą zostać usunięte.

Za każdym razem, gdy kontrolka Toolbar wymaga informacji o przycisku w oknie dialogowym Dostosuj pasek narzędzi, wysyła komunikat powiadomienia **TBN_GETBUTTONINFO** , określając indeks przycisku, dla którego są potrzebne informacje, oraz adres struktury **TBNOTIFY** . Okno nadrzędne musi wypełnić strukturę odpowiednimi informacjami.

Okno dialogowe **Dostosowywanie paska narzędzi** zawiera przycisk Pomoc i przycisk Resetuj. Gdy użytkownik wybierze przycisk Pomoc, formant Toolbar wyśle **TBN_CUSTHELP** komunikat powiadomienia. Okno nadrzędne powinno odpowiadać przez wyświetlanie informacji pomocy. Okno dialogowe wysyła **TBN_RESET** komunikat powiadomienia, gdy użytkownik wybierze przycisk Resetuj. Ten komunikat sygnalizuje, że pasek narzędzi zostanie ponownie zainicjowany okno dialogowe.

Te komunikaty to wszystkie **WM_NOTIFY** komunikaty i mogą być obsługiwane w oknie właściciela przez dodanie wpisów mapy komunikatów z następującej postaci do mapy komunikatów Twojego okna właściciela:

```cpp
ON_NOTIFY( wNotifyCode, idControl, memberFxn )
```

- **Włącz wNotifyCode**

   Kod identyfikatora komunikatu powiadomienia, taki jak **TBN_BEGINADJUST**.

- **idControl**

   Identyfikator kontrolki wysyłającej powiadomienie.

- **memberFxn**

   Funkcja członkowska, która ma zostać wywołana w przypadku otrzymania tego powiadomienia.

Funkcja członkowska zostałaby zadeklarowana przy użyciu następującego prototypu:

```cpp
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );
```

Jeśli program obsługi komunikatów powiadomień zwraca wartość, powinna ona zostać umieszczona w **LRESULT** wskazywanym przez *wynik*.

Dla każdego komunikatu `pNotifyStruct` wskazuje strukturę **NMHDR** lub strukturę **TBNOTIFY** . Te struktury są opisane poniżej:

Struktura **NMHDR** zawiera następujące elementy członkowskie:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;  // handle of control sending message
    UINT idFrom;// identifier of control sending message
    UINT code;  // notification code; see below
} NMHDR;
```

- **hwndFrom**

   Uchwyt okna kontrolki wysyłającej powiadomienie. Aby przekonwertować ten uchwyt na `CWnd` wskaźnik, użyj [CWnd:: FromHandle](reference/cwnd-class.md#fromhandle).

- **idFrom**

   Identyfikator kontrolki wysyłającej powiadomienie.

- **kodu**

   Kod powiadomienia. Ten element członkowski może być wartością specyficzną dla typu formantu, takiego jak **TBN_BEGINADJUST** lub **TTN_NEEDTEXT**, lub może być jedną z typowych wartości powiadomień wymienionych poniżej:

  - **NM_CLICK** Użytkownik kliknął lewym przyciskiem myszy w kontrolce.

  - **NM_DBLCLK** Użytkownik podwójnie kliknął lewym przyciskiem myszy w kontrolce.

  - **NM_KILLFOCUS** Kontrolka utraciła fokus wprowadzania.

  - **NM_OUTOFMEMORY** Kontrolka nie mogła ukończyć operacji, ponieważ nie jest dostępna wystarczająca ilość pamięci.

  - **NM_RCLICK** Użytkownik kliknął prawy przycisk myszy w kontrolce.

  - **NM_RDBLCLK** Użytkownik dwukrotnie kliknął prawy przycisk myszy w kontrolce.

  - **NM_RETURN** Kontrolka ma fokus wprowadzania, a użytkownik nacisnął klawisz ENTER.

  - **NM_SETFOCUS** Formant otrzymał fokus wprowadzania.

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

- **nagłówka**

   Informacje wspólne dla wszystkich **WM_NOTIFY** komunikatów.

- **iItem**

   Indeks przycisku skojarzonego z powiadomieniem.

- **tbButton**

   Struktura **TBBUTTON** , która zawiera informacje o przycisku paska narzędzi skojarzonym z powiadomieniem.

- **cchText**

   Liczba znaków w tekście przycisku.

- **lpszText**

   Wskaźnik do tekstu przycisku.

Powiadomienia wysyłane przez ten pasek narzędzi są następujące:

- **TBN_BEGINADJUST**

   Wysyłany, gdy użytkownik rozpocznie dostosowywanie kontrolki paska narzędzi. Wskaźnik wskazuje na strukturę **NMHDR** , która zawiera informacje o powiadomieniu. Procedura obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_BEGINDRAG**

   Wysyłany, gdy użytkownik rozpoczyna przeciąganie przycisku w kontrolce paska narzędzi. Wskaźnik wskazuje na strukturę **TBNOTIFY** . Element członkowski **iItem** zawiera indeks (liczony od zera) przycisku, który jest przeciągany. Procedura obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_CUSTHELP**

   Wysyłany, gdy użytkownik wybierze przycisk Pomoc w oknie dialogowym Dostosuj pasek narzędzi. Brak wartości zwracanej. Wskaźnik wskazuje na strukturę **NMHDR** , która zawiera informacje o komunikacie powiadomienia. Procedura obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_ENDADJUST**

   Wysyłany, gdy użytkownik zatrzyma Dostosowywanie kontrolki paska narzędzi. Wskaźnik wskazuje na strukturę **NMHDR** , która zawiera informacje o komunikacie powiadomienia. Procedura obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_ENDDRAG**

   Wysyłany, gdy użytkownik zatrzyma przeciąganie przycisku w kontrolce paska narzędzi. Wskaźnik wskazuje na strukturę **TBNOTIFY** . Element członkowski **iItem** zawiera indeks (liczony od zera) przycisku, który jest przeciągany. Procedura obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_GETBUTTONINFO**

   Wysyłany, gdy użytkownik dostosowuje formant paska narzędzi. Ten komunikat z powiadomieniem służy do pobierania informacji wymaganych przez okno dialogowe Dostosowywanie paska narzędzi. Wskaźnik wskazuje na strukturę **TBNOTIFY** . Element członkowski **iItem** Określa indeks (liczony od zera) przycisku. Elementy członkowskie **pszText** i **cchText** określają adres i długość bieżącego tekstu przycisku. Aplikacja powinna wypełnić strukturę informacjami o przycisku. Zwraca **wartość true** , jeśli informacje o przycisku zostały skopiowane do struktury lub w przeciwnym razie ma **wartość false** .

- **TBN_QUERYDELETE**

   Wysyłany, gdy użytkownik dostosowuje pasek narzędzi, aby określić, czy przycisk może zostać usunięty z kontrolki paska narzędzi. Wskaźnik wskazuje na strukturę **TBNOTIFY** . Element członkowski **iItem** zawiera indeks (liczony od zera) przycisku, który ma zostać usunięty. Zwróć **wartość true** , aby zezwolić na usunięcie przycisku lub **Fałsz** , aby zapobiec usunięciu przycisku.

- **TBN_QUERYINSERT**

   Wysyłany, gdy użytkownik dostosowuje formant paska narzędzi, aby określić, czy przycisk może zostać wstawiony po lewej stronie danego przycisku. Wskaźnik wskazuje na strukturę **TBNOTIFY** . Element członkowski **iItem** zawiera indeks (liczony od zera) przycisku, który ma zostać wstawiony. Zwróć **wartość true** , aby zezwolić na Wstawianie przycisku przed danym przyciskiem lub **false** , aby uniemożliwić Wstawianie przycisku.

- **TBN_RESET**

   Wysyłany, gdy użytkownik resetuje zawartość okna dialogowego Dostosuj pasek narzędzi. Wskaźnik wskazuje na strukturę **NMHDR** , która zawiera informacje o komunikacie powiadomienia. Procedura obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_TOOLBARCHANGE**

   Wysyłany, gdy użytkownik dostosował formant paska narzędzi. Wskaźnik wskazuje na strukturę **NMHDR** , która zawiera informacje o komunikacie powiadomienia. Procedura obsługi nie musi zwracać żadnej określonej wartości.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Formanty](controls-mfc.md)
