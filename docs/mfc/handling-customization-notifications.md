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
ms.openlocfilehash: dc34f3eaa4b085b9d8acbaf47b21cf1825627100
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303660"
---
# <a name="handling-customization-notifications"></a>Obsługa powiadomień dotyczących dostosowania

Formantu typowego paska narzędzi Windows zawiera funkcje wbudowane dostosowywania, w tym okno dialogowe dostosowanie zdefiniowane przez system, który umożliwia użytkownikowi Wstawianie, usuwanie lub rozmieszczanie przycisków paska narzędzi. Aplikacja określa, czy funkcje dostosowywania są dostępne i określa zakres, do którego użytkownik może dostosować na pasku narzędzi.

Można udostępnić te funkcje dostosowywania użytkownikowi, zapewniając na pasku narzędzi **CCS_ADJUSTABLE** stylu. Funkcje dostosowywania umożliwiają użytkownikowi przeciągnij przycisk do nowej pozycji lub przycisk Usuń, przeciągając go wyłączyć na pasku narzędzi. Ponadto, użytkownik może kliknąć dwukrotnie narzędzi, aby wyświetlić **Dostosuj pasek narzędzi** okno dialogowe, które zezwala użytkownikowi na dodawanie, usuwanie i ponowne rozmieszczanie przycisków paska narzędzi. Aplikacja może wyświetlać okno dialogowe przy użyciu [Dostosuj](../mfc/reference/ctoolbarctrl-class.md#customize) funkcja elementu członkowskiego.

Formantu paska narzędzi wysyła powiadomienia do okna nadrzędnego, w każdym kroku procesu dostosowywania. Jeśli użytkownik ma klucz PRZESUNIĘCIA w, rozpoczął przeciąganie przycisku paska narzędzi automatycznie obsługuje operacji przeciągania. Pasek narzędzi wysyła **tbn_querydelete —** komunikatu powiadomienia do nadrzędnego okna w celu ustalenia, czy przycisk może zostać usunięty. Operacja przeciągania kończy się po zwraca okno nadrzędne **FALSE**. W przeciwnym razie pasek narzędzi przechwytuje wejście myszy i czeka na zatwierdzenie użytkownika do zwolnij przycisk myszy.

Gdy użytkownik zwolni przycisk myszy, formantu paska narzędzi Określa położenie kursora myszy. Jeśli kursor znajduje się poza pasek narzędzi, przycisk zostanie usunięty. Jeśli kursor znajduje się na inny przycisk paska narzędzi, pasek narzędzi wysyła **tbn_queryinsert —** komunikatu powiadomienia do nadrzędnego okna, aby określić, jeśli przycisk może zostać wstawiona po lewej stronie przycisku danego. Przycisk zostanie wstawiony, jeśli zwróci okno nadrzędne **TRUE**; w przeciwnym razie nie jest. Pasek narzędzi wysyła **tbn_toolbarchange —** wiadomości z powiadomieniem o zakończeniu operacji przeciągania.

Jeśli użytkownik rozpoczyna się operacja przeciągania bez przytrzymywania klawisza SHIFT, wysyła formantu paska narzędzi **tbn_begindrag —** komunikatu powiadomienia do okna właściciela. Aplikacji, która implementuje swój własny kod przeciąganie przycisk umożliwia tego komunikatu jako sygnał rozpocząć operację przeciągania. Pasek narzędzi wysyła **tbn_enddrag —** wiadomości z powiadomieniem o zakończeniu operacji przeciągania.

Formancie paska narzędzi wysyła komunikaty powiadomień, gdy użytkownik dostosowuje pasek narzędzi za pomocą **Dostosuj pasek narzędzi** okno dialogowe. Pasek narzędzi wysyła **tbn_beginadjust —** komunikat z powiadomieniem po użytkownik kliknie dwukrotnie pasek narzędzi, ale przed okna dialogowego pole zostanie utworzony. Następnie pasek narzędzi zaczyna się wysyłanie serii **tbn_queryinsert —** komunikaty powiadomień, aby ustalić, czy pasek narzędzi umożliwia przycisków do wstawienia. Gdy okno nadrzędne zwraca **TRUE**, pasek narzędzi zaprzestaje inicjowania **tbn_queryinsert —** wiadomości z powiadomieniami. Jeśli okno nadrzędne nie zwróci **TRUE** dla dowolnego przycisku paska narzędzi niszczy okno dialogowe.

Następnie formantu paska narzędzi decyduje, jeśli wszystkie przyciski mogą zostać usunięte z paska narzędzi, wysyłając jedną **tbn_querydelete —** komunikatu powiadomienia dla każdego przycisku na pasku narzędzi. Zwraca okno nadrzędne **TRUE** wskazujący, że przycisk może być usunięty; w przeciwnym razie, zwraca **FALSE**. Pasek narzędzi dodaje wszystkie przyciski paska narzędzi do okna dialogowego, ale grays te, które nie mogą zostać usunięte.

Zawsze, gdy formant paska narzędzi potrzebuje informacji na temat przycisku w oknie dialogowym Dostosuj pasek narzędzi, wysyła **tbn_getbuttoninfo —** komunikat powiadomienia, określanie indeks przycisku, którego potrzebuje informacji i adres **tbnotify —** struktury. Okno nadrzędne należy podać struktury istotne informacje.

**Dostosuj pasek narzędzi** okno dialogowe zawiera przyciski pomocy i resetowania. Gdy użytkownik wybierze przycisk Pomoc, wysyła formantu paska narzędzi **tbn_custhelp —** wiadomość z powiadomieniem. Okno nadrzędne, powinien odpowiedzieć, wyświetlając informacje pomocy. Okno dialogowe wysyła **tbn_reset —** komunikat powiadomienia, gdy użytkownik wybierze przycisk Resetuj. Ten komunikat sygnalizuje, że pasek narzędzi zostanie ponownie zainicjować okno dialogowe.

Te komunikaty są wszystkie **WM_NOTIFY** wiadomości, dlatego mogą być obsługiwane w okno właściciela, dodając wpisy mapy komunikatów o następującej postaci do okna właściciela mapy wiadomości:

```cpp
ON_NOTIFY( wNotifyCode, idControl, memberFxn )
```

- **wNotifyCode**

   Takie jak kod identyfikatora komunikatu powiadomienia **tbn_beginadjust —**.

- **idControl**

   Identyfikator formantu wysyłania powiadomienia.

- **memberFxn**

   Funkcja elementu członkowskiego, który ma być wywoływana po odebraniu tego powiadomienia.

Czy można zadeklarować funkcji składowej z poniższy prototyp:

```cpp
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );
```

Jeśli program obsługi komunikatów powiadomień zwróci wartość, jej należy umieścić go w **LRESULT** wskazywany przez *wynik*.

Dla każdego komunikatu `pNotifyStruct` wskazuje albo **NMHDR** struktury lub **tbnotify —** struktury. Te struktury są opisane poniżej:

**NMHDR** struktura zawiera następujące składniki:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;  // handle of control sending message
    UINT idFrom;// identifier of control sending message
    UINT code;  // notification code; see below
} NMHDR;
```

- **hwndFrom**

   Uchwyt okna kontrolki, która wysyła powiadomienia. Aby przekonwertować tego dojścia do `CWnd` wskaźnika, użyj [CWnd::FromHandle](../mfc/reference/cwnd-class.md#fromhandle).

- **idFrom**

   Identyfikator kontrolki wysyłania powiadomienia.

- **Kod**

   Kod powiadomienia. Ten element członkowski może być wartością specyficzny dla typu kontrolki, takie jak **tbn_beginadjust —** lub **TTN_NEEDTEXT**, lub może być jedną z typowych wartości powiadomień wymienionych poniżej:

   - **NM_CLICK** użytkownik kliknął lewym przyciskiem myszy wewnątrz formantu.

   - **Nm_dblclk —** użytkownik podwójnie kliknął lewym przyciskiem myszy wewnątrz formantu.

   - **Nm_killfocus —** kontrolka utraciła fokus wprowadzania.

   - **Nm_outofmemory —** formantu nie można ukończyć operacji, ponieważ nie jest dostępna wystarczająca ilość pamięci.

   - **Nm_rclick —** po kliknięciu prawym przyciskiem myszy wewnątrz formantu.

   - **Nm_rdblclk —** użytkownik podwójnie kliknął prawym przyciskiem myszy wewnątrz formantu.

   - **Nm_return —** kontrolka ma fokus wprowadzania a użytkownik nacisnął klawisz ENTER.

   - **Nm_setfocus —** kontrolka otrzymała fokusa wejścia.

**Tbnotify —** struktura zawiera następujące składniki:

```cpp
typedef struct {
    NMHDR hdr; // information common to all WM_NOTIFY messages
    int iItem; // index of button associated with notification
    TBBUTTON tbButton; // info about button associated withnotification
    int cchText;   // count of characters in button text
    LPSTR lpszText;// address of button text
} TBNOTIFY, FAR* LPTBNOTIFY;
```

- **hdr**

   Informacje wspólne dla wszystkich **WM_NOTIFY** wiadomości.

- **iItem**

   Indeks przycisku skojarzony z powiadomieniem.

- **tbButton**

   **TBBUTTON** strukturę, która zawiera informacje o przycisku paska narzędzi skojarzony powiadomienia.

- **cchText**

   Liczba znaków w tekst przycisku.

- **lpszText**

   Wskaźnik do tekstu przycisku.

Powiadomienia, które wysyła na pasku narzędzi są następujące:

- **TBN_BEGINADJUST**

   Wysyłany, gdy użytkownik rozpoczyna Dostosowywanie formantu paska narzędzi. Wskaźnik wskazuje **NMHDR** strukturę, która zawiera informacje dotyczące powiadomienia. Program obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_BEGINDRAG**

   Wysyłany, gdy użytkownik rozpoczął przeciąganie przycisku w formancie paska narzędzi. Wskaźnik wskazuje **tbnotify —** struktury. **Towaru** elementu członkowskiego zawiera liczony od zera indeks przycisk przeciągania. Program obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_CUSTHELP**

   Wysyłany, gdy użytkownik naciśnie przycisk Pomoc w oknie dialogowym Dostosuj pasek narzędzi. Nie zwraca wartości. Wskaźnik wskazuje **NMHDR** strukturę, która zawiera informacje na temat komunikatu powiadomienia. Program obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_ENDADJUST**

   Wysyłany, gdy użytkownik zatrzymuje Dostosowywanie formantu paska narzędzi. Wskaźnik wskazuje **NMHDR** strukturę, która zawiera informacje na temat komunikatu powiadomienia. Program obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_ENDDRAG**

   Wysyłany, gdy użytkownik zatrzymuje przeciąganie przycisku w formancie paska narzędzi. Wskaźnik wskazuje **tbnotify —** struktury. **Towaru** elementu członkowskiego zawiera liczony od zera indeks przycisk przeciągania. Program obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_GETBUTTONINFO**

   Wysyłany, gdy dostosowywania formancie paska narzędzi przez użytkownika. Pasek narzędzi używa tego komunikatu powiadomienia można pobrać informacji wymaganych przez okna dialogowego Dostosuj pasek narzędzi. Wskaźnik wskazuje **tbnotify —** struktury. **Towaru** elementu członkowskiego określa liczony od zera indeks przycisku. **PszText** i **cchText** członków Podaj adres i długość w znakach dany tekst przycisku. Aplikację należy wypełnić strukturę z informacjami o przycisku. Zwróć **TRUE** Jeśli przycisk informacje zostały skopiowane do struktury, lub **FALSE** inaczej.

- **TBN_QUERYDELETE**

   Wysyłane podczas dostosowywania paska narzędzi w celu ustalenia, czy przycisk może zostać usunięty z formantem paska narzędzi przez użytkownika. Wskaźnik wskazuje **tbnotify —** struktury. **Towaru** elementu członkowskiego zawiera liczony od zera indeks przycisku do usunięcia. Zwróć **TRUE** umożliwia przycisk aby usunąć lub **FALSE** aby zapobiec usunięciu przycisku.

- **TBN_QUERYINSERT**

   Wysyłane podczas dostosowywania kontrolce paska narzędzi, aby ustalić, czy przycisk może zostać wstawiona po lewej stronie przycisku danego użytkownika. Wskaźnik wskazuje **tbnotify —** struktury. **Towaru** elementu członkowskiego zawiera liczony od zera indeks przycisku, który ma zostać wstawiony. Zwróć **TRUE** zezwalająca na przycisku, który ma zostać wstawiony przed danym przycisk lub **FALSE** aby zapobiec wstawiane przycisku.

- **TBN_RESET**

   Wysyłany, gdy użytkownik resetuje zawartość okna dialogowego Dostosuj pasek narzędzi. Wskaźnik wskazuje **NMHDR** strukturę, która zawiera informacje na temat komunikatu powiadomienia. Program obsługi nie musi zwracać żadnej określonej wartości.

- **TBN_TOOLBARCHANGE —**

   Wysyłane po użytkownik dostosował formancie paska narzędzi. Wskaźnik wskazuje **NMHDR** strukturę, która zawiera informacje na temat komunikatu powiadomienia. Program obsługi nie musi zwracać żadnej określonej wartości.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
