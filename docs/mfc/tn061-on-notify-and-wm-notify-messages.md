---
title: 'TN061: komunikaty ON_NOTIFY i WM_NOTIFY'
ms.date: 06/28/2018
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
ms.openlocfilehash: 845558dad6b9f6e820c759cb83fce2c6cbceaa0c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366599"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061: komunikaty ON_NOTIFY i WM_NOTIFY

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

Ta uwaga techniczna zawiera podstawowe informacje na temat nowego komunikatu WM_NOTIFY i opisuje zalecany (i najbardziej typowy) sposób obsługi komunikatów WM_NOTIFY w aplikacji MFC.

**Wiadomości powiadomień w systemie Windows 3.x**

W systemie Windows 3.x formanty powiadamiają rodziców o zdarzeniach, takich jak kliknięcia myszą, zmiany w zawartości i zaznaczeniu oraz kontrolują malowanie w tle, wysyłając wiadomość do rodzica. Proste powiadomienia są wysyłane jako specjalne wiadomości WM_COMMAND, z kodem powiadomień (takim jak BN_CLICKED) i identyfikatorem sterowania zapakowanym w *wParam* i uchwytem formantu w *lParam*. Należy pamiętać, że ponieważ *wParam* i *lParam* są pełne, nie ma możliwości przekazania dodatkowych danych — te wiadomości mogą być tylko prostym powiadomieniem. Na przykład w powiadomieniu BN_CLICKED nie ma możliwości wysyłania informacji o lokalizacji kursora myszy po kliknięciu przycisku.

Gdy formanty w systemie Windows 3.x muszą wysyłać komunikat z powiadomieniem zawierający dodatkowe dane, używają różnych wiadomości specjalnego przeznaczenia, w tym WM_CTLCOLOR, WM_VSCROLL, WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM, WM_DELETEITEM, WM_CHARTOITEM, WM_VKEYTOITEM i tak dalej. Te wiadomości mogą być odzwierciedlone z powrotem do formantu, który je wysłał. Aby uzyskać więcej informacji, zobacz [TN062: Odbicie wiadomości dla formantów systemu Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

**Wiadomości powiadomień w win32**

W przypadku formantów, które istniały w systemie Windows 3.1, interfejs API systemu Win32 używa większości komunikatów powiadomień używanych w systemie Windows 3.x. Jednak Win32 dodaje również szereg zaawansowanych, złożonych formantów do tych obsługiwanych w systemie Windows 3.x. Często te formanty muszą wysyłać dodatkowe dane z ich komunikatów powiadomień. Zamiast dodawać **WM_** <strong>\*</strong> nowy komunikat WM_ dla każdego nowego powiadomienia, który wymaga dodatkowych danych, projektanci interfejsu API Win32 wybrał dodać tylko jedną wiadomość, WM_NOTIFY, który może przekazać dowolną ilość dodatkowych danych w sposób standaryzowany.

WM_NOTIFY wiadomości zawierają identyfikator formantu wysyłającego wiadomość w *wParam* i wskaźnik do struktury w *lParam*. Ta struktura jest strukturą **NMHDR** lub większą strukturą, która ma strukturę **NMHDR** jako pierwszy element członkowski. Należy zauważyć, że ponieważ **nmhdr** element członkowski jest pierwszy, wskaźnik do tej struktury może służyć jako wskaźnik do **NMHDR** lub jako wskaźnik do większej struktury w zależności od sposobu rzutu.

W większości przypadków wskaźnik wskazuje większą strukturę i musisz ją oddać podczas korzystania z niej. Tylko w kilku powiadomieniach, takich jak typowe powiadomienia (których nazwy zaczynają się od **NM_)** i TTN_SHOW i powiadomienia TTN_POP formantu narzędzia, jest strukturą **NMHDR** faktycznie używaną.

**NmHDR** struktury lub początkowy element członkowski zawiera dojście i identyfikator formantu wysyłania wiadomości i kod powiadomienia (takich jak TTN_SHOW). Poniżej przedstawiono format struktury **NMHDR:**

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

W przypadku komunikatu TTN_SHOW element członkowski **kodu** zostanie ustawiony na TTN_SHOW.

Większość powiadomień przekazuje wskaźnik do większej struktury, która zawiera strukturę **NMHDR** jako pierwszy element członkowski. Na przykład należy wziąć pod uwagę strukturę używaną przez LVN_KEYDOWN komunikat powiadomienia formantu widoku listy, który jest wysyłany po naciśnięciu klawisza w formancie widoku listy. Wskaźnik wskazuje na **strukturę LV_KEYDOWN,** która jest zdefiniowana w sposób pokazany poniżej:

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Należy zauważyć, że ponieważ element członkowski **NMHDR** jest pierwszy w tej strukturze, wskaźnik, który zostanie przekazany w wiadomości powiadomienia, można rzutować na wskaźnik do **NMHDR** lub wskaźnik do **LV_KEYDOWN**.

**Powiadomienia typowe dla wszystkich nowych formantów systemu Windows**

Niektóre powiadomienia są wspólne dla wszystkich nowych formantów systemu Windows. Te powiadomienia przekazać wskaźnik do struktury **NMHDR.**

|Kod powiadomienia|Wysłane, ponieważ|
|-----------------------|------------------|
|NM_CLICK|Użytkownik kliknął lewym przyciskiem myszy w formancie|
|NM_DBLCLK|Dwukrotne kliknięcie lewym przyciskiem myszy przez użytkownika w formancie|
|NM_RCLICK|Użytkownik kliknął prawym przyciskiem myszy w formancie|
|NM_RDBLCLK|Dwukrotne kliknięcie prawym przyciskiem myszy przez użytkownika w formancie|
|NM_RETURN|Użytkownik nacisnął klawisz ENTER, gdy formant ma fokus wejściowy|
|NM_SETFOCUS|Sterowanie zostało podane fokus wejściowy|
|NM_KILLFOCUS|Kontrola utraciła fokus wejściowy|
|NM_OUTOFMEMORY|Formant nie może ukończyć operacji, ponieważ nie było wystarczającej ilości pamięci|

## <a name="on_notify-handling-wm_notify-messages-in-mfc-applications"></a><a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>ON_NOTIFY: Obsługa komunikatów WM_NOTIFY w aplikacjach MFC

Funkcja `CWnd::OnNotify` obsługuje komunikaty powiadomień. Jego domyślna implementacja sprawdza mapę komunikatów dla programów obsługi powiadomień do wywołania. Ogólnie rzecz biorąc, nie `OnNotify`należy zastępować . Zamiast tego należy podać funkcję obsługi i dodać wpis mapy wiadomości dla tego programu obsługi do mapy wiadomości klasy okna właściciela.

ClassWizard, za pośrednictwem arkusza właściwości ClassWizard, można utworzyć ON_NOTIFY wpis mapy wiadomości i zapewnić funkcję obsługi szkieletu. Aby uzyskać więcej informacji na temat korzystania z Programu ClassWizard w celu ułatwienia tego, zobacz [Mapowanie wiadomości do funkcji](../mfc/reference/mapping-messages-to-functions.md).

Makro ON_NOTIFY-mapa wiadomości ma następującą składnię:

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

gdzie parametrami są:

*wNotifyCode*<br/>
Kod wiadomości powiadomienia do obsługi, takich jak LVN_KEYDOWN.

*Identyfikator*<br/>
Identyfikator podrzędny formantu, dla którego jest wysyłane powiadomienie.

*członekFxn*<br/>
Funkcja elementu członkowskiego, która ma zostać wywołana podczas wysyłania tego powiadomienia.

Funkcję członka należy zadeklarować za pomocą następującego prototypu:

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

gdzie parametrami są:

*pNotifyStruct*<br/>
Wskaźnik do struktury powiadomień, jak opisano w powyższej sekcji.

*Wynik*<br/>
Wskaźnik do kodu wynikowego, który zostanie ustawiony przed powrotem.

## <a name="example"></a>Przykład

Aby określić, że `OnKeydownList1` funkcja elementu członkowskiego ma obsługiwać LVN_KEYDOWN `IDC_LIST1`wiadomości z `CListCtrl` identyfikatora, należy użyć ClassWizard, aby dodać następujące elementy do mapy wiadomości:

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

W powyższym przykładzie funkcja świadczona przez ClassWizard jest:

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

Należy zauważyć, że ClassWizard udostępnia wskaźnik odpowiedniego typu automatycznie. Dostęp do struktury powiadomień można uzyskać za pośrednictwem *pNMHDR* lub *pLVKeyDow*.

## <a name="on_notify_range"></a><a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE

Jeśli musisz przetworzyć ten sam komunikat WM_NOTIFY dla zestawu formantów, możesz użyć ON_NOTIFY_RANGE, a nie ON_NOTIFY. Na przykład może mieć zestaw przycisków, dla których chcesz wykonać tę samą akcję dla określonej wiadomości powiadomienia.

Korzystając z ON_NOTIFY_RANGE, należy określić ciągły zakres identyfikatorów podrzędnych, dla których do obsługi wiadomości powiadomienia, określając początkowe i końcowe identyfikatory podrzędne zakresu.

ClassWizard nie obsługuje ON_NOTIFY_RANGE; aby z niego korzystać, musisz samodzielnie edytować mapę wiadomości.

Wpis mapy wiadomości i prototyp funkcji dla ON_NOTIFY_RANGE są następujące:

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

gdzie parametrami są:

*wNotifyCode*<br/>
Kod wiadomości powiadomienia do obsługi, takich jak LVN_KEYDOWN.

*Identyfikator*<br/>
Pierwszy identyfikator w ciągłym zakresie identyfikatorów.

*idLast*<br/>
Ostatni identyfikator w ciągłym zakresie identyfikatorów.

*członekFxn*<br/>
Funkcja elementu członkowskiego, która ma zostać wywołana podczas wysyłania tego powiadomienia.

Funkcję członka należy zadeklarować za pomocą następującego prototypu:

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

gdzie parametrami są:

*Identyfikator*<br/>
Identyfikator podrzędny formantu, który wysłał powiadomienie.

*pNotifyStruct*<br/>
Wskaźnik do struktury powiadomień, jak opisano powyżej.

*Wynik*<br/>
Wskaźnik do kodu wynikowego, który zostanie ustawiony przed powrotem.

## <a name="on_notify_ex-on_notify_ex_range"></a><a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX, ON_NOTIFY_EX_RANGE

Jeśli chcesz, aby więcej niż jeden obiekt w routingu powiadomień obsługiwał wiadomość, możesz użyć ON_NOTIFY_EX (lub ON_NOTIFY_EX_RANGE), a nie ON_NOTIFY (lub ON_NOTIFY_RANGE). Jedyną różnicą między wersją **EX** a wersją zwykłą jest to, że funkcja elementu członkowskiego wywoływana dla wersji **EX** zwraca **BOOL,** który wskazuje, czy przetwarzanie wiadomości powinno być kontynuowane. Zwracanie **FAŁSZu** z tej funkcji umożliwia przetwarzanie tej samej wiadomości w więcej niż jednym obiekcie.

ClassWizard nie obsługuje ON_NOTIFY_EX lub ON_NOTIFY_EX_RANGE; jeśli chcesz użyć jednego z nich, musisz samodzielnie edytować mapę wiadomości.

Wpis mapy wiadomości i prototyp funkcji dla ON_NOTIFY_EX i ON_NOTIFY_EX_RANGE są następujące. Znaczenie parametrów są takie same jak w przypadku wersji innych niż**EX.**

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

Prototyp dla obu powyższych jest taki sam:

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

W obu przypadkach *identyfikator* przechowuje identyfikator podrzędny formantu, który wysłał powiadomienie.

Funkcja musi zwracać **wartość PRAWDA,** jeśli komunikat powiadomienia został całkowicie obsłużony lub **FALSE,** jeśli inne obiekty w routingu polecenia powinny mieć szansę na obsługę wiadomości.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
