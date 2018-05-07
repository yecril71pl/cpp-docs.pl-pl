---
title: Obsługa powiadomień dotyczących dostosowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3636d3db480563295213b76de06133e78e30cd0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="handling-customization-notifications"></a>Obsługa powiadomień dotyczących dostosowania
Typowe kontrolki paska narzędzi systemu Windows ma dostosowania wbudowane funkcje, w tym okno dialogowe dostosowanie zdefiniowane przez system, które umożliwiają użytkownikom wstawianie, usuwanie lub rozmieszczanie przycisków paska narzędzi. Aplikacja określa, czy funkcje dostosowywania są dostępne i określa zakres, do którego użytkownik może dostosować na pasku narzędzi.  
  
 Można udostępnić te funkcje dostosowywania użytkownikowi, zapewniając na pasku narzędzi `CCS_ADJUSTABLE` stylu. Funkcje dostosowywania umożliwiają użytkownikowi przeciągnij przycisk do nowej pozycji lub usunąć przycisk przeciągając go poza pasek narzędzi. Ponadto użytkownik może kliknąć dwukrotnie narzędzi, aby wyświetlić **Dostosuj pasek narzędzi** okno dialogowe, które pozwala użytkownikowi na dodawanie, usuwanie i rozmieszczanie przycisków paska narzędzi. Aplikację można wyświetlić okna dialogowego za pomocą [Dostosuj](../mfc/reference/ctoolbarctrl-class.md#customize) funkcję elementu członkowskiego.  
  
 Formantu toolbar wysyła komunikaty powiadomień do nadrzędnego okna w każdym kroku procesu dostosowywania. Jeśli użytkownik posiada klawisz SHIFT i rozpocznie przeciąganie przycisk, pasek narzędzi automatycznie obsługiwać operacji przeciągania. Pasek narzędzi wysyła **tbn_querydelete —** komunikatu powiadomienia do nadrzędnego okna, aby określić, czy przycisk mogą zostać usunięte. Operacja przeciągania kończy się, jeśli okno nadrzędne zwraca **FALSE**. W przeciwnym razie pasek narzędzi przechwytuje myszą i czeka na użytkownikowi zwolnij przycisk myszy.  
  
 Gdy użytkownik zwolni przycisk myszy, formantu toolbar określa lokalizacji kursora myszy. W przypadku gdy kursor znajduje się poza pasek narzędzi, przycisk zostaną usunięte. Jeśli kursor znajduje się na inny przycisk paska narzędzi, pasek narzędzi wysyła **tbn_queryinsert —** komunikatu powiadomienia do nadrzędnego okna, aby określić, czy przycisk można wstawiać do lewego przycisku danego. Przycisk zostanie wstawiony, jeśli okno nadrzędne zwraca **TRUE**; w przeciwnym razie nie jest. Pasek narzędzi wysyła **tbn_toolbarchange —** komunikat powiadomienia, która sygnalizuje koniec operacji przeciągania.  
  
 Jeśli użytkownik rozpoczyna się operacja przeciągania bez przytrzymując naciśnięty klawisz SHIFT, wysyła formantu toolbar **tbn_begindrag —** wiadomość z powiadomieniem do okna nadrzędnego. Sygnał aplikacji, która implementuje własny kod przeciąganie przycisku służy ten komunikat ma zostać rozpoczęta operacja przeciągania. Pasek narzędzi wysyła **tbn_enddrag —** komunikat powiadomienia, która sygnalizuje koniec operacji przeciągania.  
  
 Formantu paska narzędzi wysyła komunikaty powiadomień, gdy użytkownik dostosowuje pasek narzędzi przy użyciu **Dostosuj pasek narzędzi** okno dialogowe. Pasek narzędzi wysyła **tbn_beginadjust —** wiadomość z powiadomieniem po użytkownik kliknie dwukrotnie pasek narzędzi, ale przed okna dialogowego okno jest tworzone. Następnie paska narzędzi rozpoczyna wysyłanie szereg **tbn_queryinsert —** komunikatów powiadomień, aby określić, czy pasek narzędzi umożliwia przyciski do wstawienia. Gdy okno nadrzędne zwraca **TRUE**, pasek narzędzi zatrzymuje wysyłanie **tbn_queryinsert —** komunikaty powiadomień. Jeśli okno nadrzędne nie zwraca **TRUE** dla dowolnego przycisku paska narzędzi niszczy okno dialogowe.  
  
 Następnie formantu toolbar Określa, jeśli wszystkie przyciski mogą zostać usunięte z paska narzędzi przez wysyłanie co **tbn_querydelete —** komunikatu powiadomienia dla każdego przycisku w pasku narzędzi. Zwraca okno nadrzędne **TRUE** aby wskazać, że przycisk może być usunięty; w przeciwnym razie, zwraca **FALSE**. Pasek narzędzi dodaje wszystkie przycisków paska narzędzi do okna dialogowego, ale grays te, które nie mogą zostać usunięte.  
  
 Zawsze, gdy formantu toolbar wymaga informacji o przycisku w oknie dialogowym Dostosuj pasek narzędzi, wysyła **tbn_getbuttoninfo —** komunikat powiadomienia, określenie indeksu przycisku, dla którego wymaganych informacji i adres **tbnotify —** struktury. Okno nadrzędne, należy podać struktury istotne informacje.  
  
 **Dostosuj pasek narzędzi** okno dialogowe zawiera przyciski pomocy i Reset. Gdy użytkownik wybierze przycisk Pomoc, wysyła formantu toolbar **tbn_custhelp —** wiadomość z powiadomieniem. Okno nadrzędne powinien odpowiadać za pomocą wyświetlania informacji pomocy. Okno dialogowe wysyła **tbn_reset —** powiadomienie, gdy użytkownik wybierze przycisk resetowania. Ten komunikat sygnalizuje, że pasek narzędzi zostanie zainicjowana ponownie w oknie dialogowym.  
  
 Komunikaty te są wszystkie **WM_NOTIFY** wiadomości i ich są obsługiwane w oknie właściciela przez dodanie wpisów map wiadomości następującą postać do mapy komunikatów z oknem właściciela:  
  
 `ON_NOTIFY( wNotifyCode, idControl, memberFxn )`  
  
 `wNotifyCode`  
 Takie jak kod identyfikatora komunikatu powiadomienia **tbn_beginadjust —**.  
  
 `idControl`  
 Identyfikator formantu wysyłania powiadomienia.  
  
 `memberFxn`  
 Funkcja członkowska ma być wywoływana po otrzymaniu tego powiadomienia.  
  
 Czy można zadeklarować funkcji Członkowskich przy użyciu prototypu następujące:  
  
 `afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );`  
  
 Jeśli program obsługi komunikatów powiadomień zwróci wartość, powinno umieścić go **elementu LRESULT** wskazywana przez *wynik*.  
  
 Dla każdego komunikatu `pNotifyStruct` wskazuje albo **NMHDR** struktury lub **tbnotify —** struktury. Poniżej opisano te struktury:  
  
 **NMHDR** struktura zawiera następujące składniki:  
  
 `typedef struct tagNMHDR {`  
  
 `HWND hwndFrom;  // handle of control sending message`  
  
 `UINT idFrom;// identifier of control sending message`  
  
 `UINT code;  // notification code; see below`  
  
 `} NMHDR;`  
  
 **hwndFrom**  
 Uchwyt okna kontrolki, która wysyła powiadomienia. Aby przekonwertować ta dojścia do `CWnd` wskaźnika, użyj [CWnd::FromHandle](../mfc/reference/cwnd-class.md#fromhandle).  
  
 **idFrom**  
 Identyfikator formantu wysyłania powiadomienia.  
  
 **Kod**  
 Kod powiadomienia. Ten element członkowski może być wartością specyficzne dla typu formantu, takich jak **tbn_beginadjust —** lub **TTN_NEEDTEXT**, lub może być jedną z wymienionych poniżej typowe wartości powiadomień:  
  
-   **NM_CLICK** użytkownik kliknął lewym przyciskiem myszy wewnątrz formantu.  
  
-   **Nm_dblclk —** użytkownik podwójnie kliknął lewym przyciskiem myszy wewnątrz formantu.  
  
-   **Nm_killfocus —** kontrolka utraciła fokus wprowadzania.  
  
-   **Nm_outofmemory —** formantu nie można ukończyć operacji, ponieważ nie jest dostępna wystarczająca ilość pamięci.  
  
-   **Nm_rclick —** po kliknięciu prawym przyciskiem myszy wewnątrz formantu.  
  
-   **Nm_rdblclk —** użytkownik podwójnie kliknął prawym przyciskiem myszy wewnątrz formantu.  
  
-   **Nm_return —** formant ma fokus wprowadzania a użytkownik nacisnął klawisz ENTER.  
  
-   **Nm_setfocus —** kontrolka otrzymała fokus wprowadzania.  
  
 **Tbnotify —** struktura zawiera następujące składniki:  
  
 `typedef struct {`  
  
 `NMHDR hdr; // information common to all WM_NOTIFY messages`  
  
 `int iItem; // index of button associated with notification`  
  
 `TBBUTTON tbButton; // info about button associated withnotification`  
  
 `int cchText;   // count of characters in button text`  
  
 `LPSTR lpszText;// address of button text`  
  
 `} TBNOTIFY, FAR* LPTBNOTIFY;`  
  
## <a name="remarks"></a>Uwagi  
 **HDR**  
 Wspólne dla wszystkich informacji **WM_NOTIFY** wiadomości.  
  
 **Towaru**  
 Indeks przycisku skojarzonego z powiadomień.  
  
 **tbButton**  
 `TBBUTTON` Struktura, która zawiera informacje o przycisku paska narzędzi skojarzone z powiadomienia.  
  
 **cchText**  
 Liczba znaków w tekście przycisku.  
  
 **lpszText**  
 Wskaźnik do tekstu przycisku.  
  
 Powiadomienia, które wysyła pasku narzędzi są następujące:  
  
-   **Tbn_beginadjust —** wysyłany, gdy użytkownik rozpocznie Dostosowywanie formantu paska narzędzi. Wskaźnik wskazuje **NMHDR** struktury, który zawiera informacje o powiadomienia. Program obsługi nie musi zwracać żadnej określonej wartości.  
  
-   **Tbn_begindrag —** wysyłany, gdy użytkownik rozpocznie przeciąganie przycisk w formancie paska narzędzi. Wskaźnik wskazuje **tbnotify —** struktury. **Towaru** elementu członkowskiego zawiera liczony od zera indeks przycisk przeciągania. Program obsługi nie musi zwracać żadnej określonej wartości.  
  
-   **Tbn_custhelp —** wysyłany, gdy użytkownik wybierze przycisk Pomoc w oknie dialogowym Dostosuj pasek narzędzi. Brak wartości zwracanej. Wskaźnik wskazuje **NMHDR** struktury, który zawiera informacje o komunikatu powiadomienia. Program obsługi nie musi zwracać żadnej określonej wartości.  
  
-   **Tbn_endadjust —** wysyłany, gdy użytkownik przestanie Dostosowywanie formantu paska narzędzi. Wskaźnik wskazuje **NMHDR** struktury, który zawiera informacje o komunikatu powiadomienia. Program obsługi nie musi zwracać żadnej określonej wartości.  
  
-   **Tbn_enddrag —** wysyłany, gdy użytkownik przestanie przeciągać przycisk w formancie paska narzędzi. Wskaźnik wskazuje **tbnotify —** struktury. **Towaru** elementu członkowskiego zawiera liczony od zera indeks przycisk przeciągania. Program obsługi nie musi zwracać żadnej określonej wartości.  
  
-   **Tbn_getbuttoninfo —** wysyłane podczas dostosowywania formantu paska narzędzi przez użytkownika. Pasek narzędzi używa tego komunikatu powiadomienia można pobrać informacji wymaganych przez okno dialogowe Dostosuj pasek narzędzi. Wskaźnik wskazuje **tbnotify —** struktury. **Towaru** elementu członkowskiego określa liczony od zera indeks przycisku. **PszText** i **cchText** członków Określ adres i długość w znakach dany tekst przycisku. Czy operacja fill struktury informacji o przycisku aplikacji. Zwraca **TRUE** Jeśli przycisku informacje zostały skopiowane do struktury, lub **FALSE** inaczej.  
  
-   **Tbn_querydelete —** wysyłane podczas dostosowywania paska narzędzi w celu ustalenia, czy przycisk mogą zostać usunięte z formantem paska narzędzi przez użytkownika. Wskaźnik wskazuje **tbnotify —** struktury. **Towaru** elementu członkowskiego zawiera liczony od zera indeks przycisku do usunięcia. Zwraca **TRUE** umożliwia przycisku do usunięcia lub **FALSE** aby zapobiec usunięciu przycisku.  
  
-   **Tbn_queryinsert —** wysyłane podczas dostosowywania formantu paska narzędzi, aby określić, czy przycisk można wstawiać do lewego przycisku danego użytkownika. Wskaźnik wskazuje **tbnotify —** struktury. **Towaru** elementu członkowskiego zawiera liczony od zera indeks przycisku do wstawienia. Zwraca **TRUE** umożliwia przycisk ma zostać wstawiony przed danym przycisk lub **FALSE** aby zapobiec wstawiane przycisku.  
  
-   **Tbn_reset —** wysyłany, gdy użytkownik resetuje zawartość okna dialogowego Dostosuj pasek narzędzi. Wskaźnik wskazuje **NMHDR** struktury, który zawiera informacje o komunikatu powiadomienia. Program obsługi nie musi zwracać żadnej określonej wartości.  
  
-   **Tbn_toolbarchange —** wysyłane po użytkownik dostosował formantu paska narzędzi. Wskaźnik wskazuje **NMHDR** struktury, który zawiera informacje o komunikatu powiadomienia. Program obsługi nie musi zwracać żadnej określonej wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

