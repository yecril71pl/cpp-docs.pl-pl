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
ms.openlocfilehash: aa1efb628ee45be3dfaee320cf64c4b2cbb91f04
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302240"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061: komunikaty ON_NOTIFY i WM_NOTIFY

> [!NOTE]
> Następująca Uwaga techniczna nie została zaktualizowana, ponieważ została najpierw uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zalecamy wyszukiwanie tematu zainteresowania w indeksie dokumentacji online.

Ta Uwaga techniczna zawiera informacje ogólne o nowym WM_NOTIFY komunikacie i opisuje zalecane (i najbardziej typowe) sposób obsługi komunikatów WM_NOTIFY w aplikacji MFC.

**Komunikaty powiadomień w systemie Windows 3. x**

W systemie Windows 3. x kontrolki powiadamiają obiekty nadrzędne o zdarzeniach, takich jak kliknięcia myszą, zmiany zawartości i wyboru oraz kontrolowanie rysowania tła przez wysłanie komunikatu do elementu nadrzędnego. Proste powiadomienia są wysyłane jako specjalne wiadomości WM_COMMAND, z kodem powiadomienia (na przykład BN_CLICKED) i IDENTYFIKATORem formantu spakowanym do *wParam* i uchwytem kontrolki w *lParam*. Należy zauważyć, że ponieważ *wParam* i *lParam* są zapełnione, nie istnieje sposób przekazywania jakichkolwiek dodatkowych danych — te komunikaty mogą być tylko prostymi powiadomieniami. Na przykład w powiadomieniu o BN_CLICKED nie ma możliwości wysyłania informacji o lokalizacji kursora myszy po kliknięciu przycisku.

Gdy kontrolki w systemie Windows 3. x muszą wysyłać komunikat z powiadomieniem zawierającym dodatkowe dane, używają różnych komunikatów specjalnych, takich jak WM_CTLCOLOR, WM_VSCROLL, WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM, WM_DELETEITEM WM_ CHARTOITEM, WM_VKEYTOITEM itd. Te komunikaty można odwrócić do kontrolki, która je wysłała. Aby uzyskać więcej informacji, zobacz [TN062: odbicie komunikatu dla formantów systemu Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

**Komunikaty powiadomień w Win32**

W przypadku kontrolek, które istniały w systemie Windows 3,1, Win32 API używa większości komunikatów powiadomień, które zostały użyte w systemie Windows 3. x. Jednak Win32 dodaje do nich wiele zaawansowanych, złożonych formantów, które są obsługiwane w systemie Windows 3. x. Często te kontrolki muszą wysyłać dodatkowe dane przy użyciu ich komunikatów powiadomień. Zamiast dodawać nowy WM_ komunikat <strong>\*</strong> dla każdego nowego powiadomienia, które wymaga dodatkowych danych, projektanci Win32 API wybierali tylko jeden komunikat, WM_NOTIFY, który może przekazywać dowolną ilość dodatkowych danych w ustandaryzowany sposób.

Komunikaty WM_NOTIFY zawierają identyfikator kontrolki wysyłającej wiadomość w *wParam* i wskaźnik do struktury w *lParam*. Ta struktura jest strukturą **NMHDR** lub większą strukturą, która ma strukturę **NMHDR** jako pierwszy element członkowski. Należy zauważyć, że ponieważ element członkowski **NMHDR** jest pierwszy, wskaźnik do tej struktury może być używany jako wskaźnik do **NMHDR** lub jako wskaźnik do większej struktury, w zależności od sposobu rzutowania.

W większości przypadków wskaźnik wskaże większą strukturę i będzie trzeba go rzutować podczas korzystania z niego. W przypadku tylko kilku powiadomień, takich jak typowe powiadomienia (których nazwy zaczynają się od **NM_** ), a TTN_SHOW i TTN_POP powiadomienia kontrolki etykietki narzędzi, jest to struktura **NMHDR** faktycznie używana.

Struktura **NMHDR** lub początkowy element członkowski zawiera uchwyt i identyfikator kontrolki wysyłającej komunikat oraz kod powiadomienia (na przykład TTN_SHOW). Poniżej przedstawiono format struktury **NMHDR** :

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

Dla komunikatu TTN_SHOW, element członkowski **kodu** zostanie ustawiony na TTN_SHOW.

Większość powiadomień przekazuje wskaźnik do większej struktury, która zawiera strukturę **NMHDR** jako jej pierwszy element członkowski. Na przykład rozważmy strukturę używaną przez LVN_KEYDOWN komunikat powiadomienia o kontrolce widoku listy, który jest wysyłany po naciśnięciu klawisza w kontrolce widoku listy. Wskaźnik wskazuje na strukturę **LV_KEYDOWN** , która jest zdefiniowana w następujący sposób:

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Należy pamiętać, że ponieważ element członkowski **NMHDR** jest pierwszy w tej strukturze, wskaźnik, który jest przesyłany w komunikacie powiadomienia, może być rzutowany na wskaźnik do **NMHDR** lub wskaźnika do **LV_KEYDOWN**.

**Powiadomienia wspólne dla wszystkich nowych kontrolek systemu Windows**

Niektóre powiadomienia są wspólne dla wszystkich nowych kontrolek systemu Windows. Te powiadomienia przechodzą wskaźnik do struktury **NMHDR** .

|Kod powiadomienia|Wysłano, ponieważ|
|-----------------------|------------------|
|NM_CLICK|Użytkownik kliknął lewym przyciskiem myszy na kontrolce|
|NM_DBLCLK|Użytkownik dwukrotnie kliknął lewym przyciskiem myszy na kontrolce|
|NM_RCLICK|Użytkownik kliknął prawym przyciskiem myszy na kontrolce|
|NM_RDBLCLK|Użytkownik dwukrotnie kliknął prawym przyciskiem myszy w kontrolce|
|NM_RETURN|Użytkownik nacisnął klawisz ENTER, gdy kontrolka ma fokus wprowadzania|
|NM_SETFOCUS|Formant otrzymał fokus wprowadzania|
|NM_KILLFOCUS|Kontrolka utraciła fokus wprowadzania|
|NM_OUTOFMEMORY|Kontrolka nie mogła ukończyć operacji, ponieważ nie jest dostępna wystarczająca ilość pamięci|

##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>ON_NOTIFY: obsługiwanie WM_NOTIFY komunikatów w aplikacjach MFC

Funkcja `CWnd::OnNotify` obsługuje komunikaty powiadomień. Jej domyślna implementacja sprawdza mapę komunikatów dla programów obsługi powiadomień w celu wywołania. Ogólnie rzecz biorąc nie zastępuje się `OnNotify`. Zamiast tego należy podać funkcję programu obsługi i dodać wpis mapy komunikatów dla tej procedury obsługi do mapy komunikatów klasy Twojego właściciela.

ClassWizard, za pośrednictwem arkusza właściwości ClassWizard, można utworzyć wpis mapy komunikatów ON_NOTIFY i udostępnić funkcję obsługi szkieletowej. Aby uzyskać więcej informacji na temat korzystania z ClassWizard w celu ułatwienia, zobacz [Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).

ON_NOTIFY makro mapy komunikatów ma następującą składnię:

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

gdzie parametrami są:

*wNotifyCode*<br/>
Kod dla komunikatu powiadomienia, który ma zostać obsłużony, na przykład LVN_KEYDOWN.

*id*<br/>
Identyfikator podrzędny kontrolki, dla której wysyłane jest powiadomienie.

*memberFxn*<br/>
Funkcja członkowska, która ma zostać wywołana w przypadku wysłania tego powiadomienia.

Funkcja członkowska musi być zadeklarowana przy użyciu następującego prototypu:

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

gdzie parametrami są:

*pNotifyStruct*<br/>
Wskaźnik do struktury powiadomień, zgodnie z opisem w powyższej sekcji.

*wynika*<br/>
Wskaźnik do kodu wyniku, który zostanie ustawiony przed zwróceniem.

## <a name="example"></a>Przykład

Aby określić, że funkcja członkowska `OnKeydownList1` obsługiwać LVN_KEYDOWN komunikatów z `CListCtrl` o IDENTYFIKATORze `IDC_LIST1`, użyj ClassWizard, aby dodać następujący element do mapy komunikatów:

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

W powyższym przykładzie funkcja udostępniona przez ClassWizard jest:

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

Należy zauważyć, że ClassWizard zapewnia automatycznie wskaźnik odpowiedniego typu. Dostęp do struktury powiadomień można uzyskać za pomocą *pNMHDR* lub *pLVKeyDow*.

##  <a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE

Jeśli musisz przetworzyć ten sam komunikat WM_NOTIFY dla zestawu kontrolek, możesz użyć ON_NOTIFY_RANGE zamiast ON_NOTIFY. Na przykład możesz mieć zestaw przycisków, dla których chcesz wykonać tę samą akcję dla konkretnego komunikatu z powiadomieniem.

W przypadku korzystania z ON_NOTIFY_RANGE należy określić ciągły zakres identyfikatorów podrzędnych, dla którego ma być obsługiwany komunikat z powiadomieniem, określając początkową i końcową identyfikatory podrzędne zakresu.

ClassWizard nie obsługuje ON_NOTIFY_RANGE; Aby z niego korzystać, musisz samodzielnie edytować mapę wiadomości.

Wpis mapy komunikatów i prototyp funkcji dla ON_NOTIFY_RANGE są następujące:

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

gdzie parametrami są:

*wNotifyCode*<br/>
Kod dla komunikatu powiadomienia, który ma zostać obsłużony, na przykład LVN_KEYDOWN.

*id*<br/>
Pierwszy identyfikator z ciągłego zakresu identyfikatorów.

*idLast*<br/>
Ostatni identyfikator z ciągłego zakresu identyfikatorów.

*memberFxn*<br/>
Funkcja członkowska, która ma zostać wywołana w przypadku wysłania tego powiadomienia.

Funkcja członkowska musi być zadeklarowana przy użyciu następującego prototypu:

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

gdzie parametrami są:

*id*<br/>
Identyfikator podrzędny kontrolki, która wysłała powiadomienie.

*pNotifyStruct*<br/>
Wskaźnik do struktury powiadomień, zgodnie z powyższym opisem.

*wynika*<br/>
Wskaźnik do kodu wyniku, który zostanie ustawiony przed zwróceniem.

##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX, ON_NOTIFY_EX_RANGE

Jeśli chcesz, aby więcej niż jeden obiekt w routingu powiadomień obsługiwał komunikat, możesz użyć ON_NOTIFY_EX (lub ON_NOTIFY_EX_RANGE), a nie ON_NOTIFY (lub ON_NOTIFY_RANGE). Jedyną różnicą między wersją **ex** i regularną jest to, że funkcja członkowska wywołana dla wersji **ex** zwraca wartość **logiczną** , która wskazuje, czy przetwarzanie komunikatów powinno być kontynuowane. Zwrócenie **wartości false** z tej funkcji umożliwia przetworzenie tego samego komunikatu w więcej niż jednym obiekcie.

ClassWizard nie obsługuje ON_NOTIFY_EX ani ON_NOTIFY_EX_RANGE; Jeśli chcesz użyć dowolnego z nich, musisz samodzielnie edytować mapę wiadomości.

Wpis mapy komunikatów i prototyp funkcji dla ON_NOTIFY_EX i ON_NOTIFY_EX_RANGE są następujące. Znaczenie parametrów jest takie samo jak w przypadku wersji**nieex** .

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

Prototyp obu powyższych elementów jest taki sam:

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

W obu przypadkach *Identyfikator* zawiera podrzędny identyfikator kontrolki, która wysłała powiadomienie.

Funkcja musi zwrócić **wartość true** , jeśli komunikat powiadomienia został całkowicie obsłużony lub **Fałsz** , jeśli inne obiekty w marszrucie poleceń powinny mieć szansę obsługi komunikatu.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
