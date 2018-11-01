---
title: 'TN061: komunikaty ON_NOTIFY i WM_NOTIFY'
ms.date: 06/28/2018
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
ms.openlocfilehash: 74eb39a855da3ff3e6da7f14a76bf0804919826d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658851"
---
# <a name="tn061-onnotify-and-wmnotify-messages"></a>TN061: komunikaty ON_NOTIFY i WM_NOTIFY

> [!NOTE]
> Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga techniczna podano informacje dotyczące nowy komunikat WM_NOTIFY i opisano zalecane (i najbardziej powszechnym) sposób Obsługa komunikatów WM_NOTIFY w Twojej aplikacji MFC.

**Komunikatów powiadomień w Windows 3.x**

W Windows 3.x, formanty Powiadom nadrzędnych zdarzenia, takie jak kliknięcie myszą, zmian w zawartości i wyboru i rysowania tła kontrolki, wysyłając wiadomość do elementu nadrzędnego. Proste powiadomienia są wysyłane jako specjalne wm_command — komunikaty, podając mu kod powiadomienia (na przykład BN_CLICKED) i identyfikator spakowane do formantu *wParam* i uchwyt formantu w *lParam*. Należy pamiętać, że od momentu *wParam* i *lParam* są pełne, nie istnieje sposób do przekazania dodatkowych danych — te komunikaty mogą być tylko proste powiadomienia. Na przykład w powiadomieniu BN_CLICKED nie ma możliwości do wysyłania informacji o lokalizacji kursora myszy, gdy został kliknięty przycisk.

Gdy kontrolek Windows 3.x, o których trzeba wysłać komunikatu powiadomienia, który zawiera dodatkowe dane, używają różnych komunikaty specjalnego przeznaczenia, w tym wm_ctlcolor — WM_VSCROLL, WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM, WM_DELETEITEM, WM_ CHARTOITEM WM_VKEYTOITEM i tak dalej. Te komunikaty można odzwierciedlenie do kontrolki, która wysłała je. Aby uzyskać więcej informacji, zobacz [TN062: odbicie komunikatu dla formantów Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

**Komunikaty powiadomień w systemie Win32**

W przypadku kontrolek, które istniały w Windows 3.1 Win32 API wykorzystuje większość komunikaty powiadomień, które były używane w Windows 3.x. Jednak Win32 również zwiększa liczbę kontrolki zaawansowane, złożone obsługiwanymi w Windows 3.x. Często trzeba wysłać dodatkowe dane za pomocą ich komunikatów powiadomień tych kontrolek. Zamiast dodawać nowe **WM_** <strong>\*</strong> komunikatu dla każdego nowe powiadomienie, że będzie potrzebowała dodatkowych danych, projektantów interfejsu API Win32 wybrał opcję Dodaj tylko jeden komunikat WM_NOTIFY, które można przekazać dowolny ilość dodatkowych danych w sposób standardowy.

WM_NOTIFY wiadomości zawierają identyfikator formantu wiadomość jest wysyłana w *wParam* i wskaźnik do struktury w *lParam*. Ta struktura jest albo **NMHDR** struktury lub niektóre większej struktury, która ma **NMHDR** struktury jako swojego pierwszego elementu członkowskiego. Należy pamiętać, że od momentu **NMHDR** następuje składowej, wskaźnik do struktury ten może służyć jako wskaźnik do **NMHDR** lub jako wskaźnik do większej struktury, w zależności od tego, jak rzutowanie.

W większości przypadków kursor wskaże większej struktury, i należy go rzutować, gdy jest używany. Tylko kilka powiadomień, takie jak wspólne powiadomienia (o nazwach zaczynających **NM_**) i narzędzie Porada kontrolki TTN_SHOW i TTN_POP powiadomienia, jest **NMHDR** struktury rzeczywiście używane.

**NMHDR** struktury lub pierwotnym członku zawiera dojście i identyfikator kontrolki, wysyłając wiadomość i kod powiadomienia (na przykład TTN_SHOW). Format **NMHDR** struktury jest pokazany poniżej:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

W przypadku komunikatu TTN_SHOW **kodu** TTN_SHOW będzie miał ustawienie elementu członkowskiego.

Większość powiadomienia przekazać wskaźnik do większych strukturę, która zawiera **NMHDR** struktury jako swojego pierwszego elementu członkowskiego. Na przykład należy wziąć pod uwagę struktury używane przez komunikat powiadomienia LVN_KEYDOWN kontrolka widoku listy, który jest wysyłany po naciśnięciu klawisza w kontrolka widoku listy. Wskaźnik wskazuje **LV_KEYDOWN** struktury, która jest zdefiniowana, jak pokazano poniżej:

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Należy pamiętać, że od momentu **NMHDR** element członkowski jest pierwszy w tej struktury, wskaźnik przekazałeś komunikatu powiadomienia mogą być rzutowane na wskaźnik do **NMHDR** lub wskaźnika do **LV_KEYDOWN** .

**Typowe powiadomienia do wszystkich nowych kontrolek Windows**

Niektóre powiadomienia są wspólne dla wszystkich nowych formantów Windows. Te powiadomienia przekazać wskaźnik do **NMHDR** struktury.

|Kod powiadomienia|Wysłana, ponieważ|
|-----------------------|------------------|
|NM_CLICK|Użytkownik kliknął lewym przyciskiem myszy formant|
|NM_DBLCLK —|Użytkownik dwukrotnym kliknięciu lewym przyciskiem myszy formant|
|NM_RCLICK —|Użytkownik kliknął prawym przyciskiem myszy w kontrolce|
|NM_RDBLCLK —|Użytkownik dwukrotnym kliknięciu prawym przyciskiem myszy w kontrolce|
|NM_RETURN —|Użytkownik nacisnął klawisz ENTER, gdy kontrolka ma fokus wejścia|
|NM_SETFOCUS —|Kontrolka ma fokus wprowadzania|
|NM_KILLFOCUS —|Kontrolka utraciła fokus wprowadzania|
|NM_OUTOFMEMORY —|Kontrolka nie mogła ukończyć operacji, ponieważ nie była dostępna wystarczająca ilość pamięci|

##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a> ON_NOTIFY: Obsługa WM_NOTIFY komunikatów w aplikacjach MFC

Funkcja `CWnd::OnNotify` obsługuje komunikaty powiadomień. Jego domyślna implementacja sprawdza, czy mapę komunikatów w poszukiwaniu programy obsługi powiadomień do wywołania. Ogólnie rzecz biorąc, nie zastąpisz `OnNotify`. Zamiast tego zapewnia funkcję obsługi i Dodaj wpis mapy komunikatów dla tej obsługi na mapie komunikatów klasy okna właściciela.

ClassWizard za pośrednictwem ClassWizard arkusza właściwości, można utworzyć wpisu mapy komunikatów ON_NOTIFY i udostępniać funkcję obsługi szkielet. Aby uzyskać więcej informacji na temat używania ClassWizard, aby to ułatwić, zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).

Makra mapy komunikatów ON_NOTIFY ma następującą składnię:

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

gdzie parametrami są:

*wNotifyCode*<br/>
Kod komunikatu powiadomienia mają być obsługiwane, takich jak LVN_KEYDOWN.

*id*<br/>
Identyfikator podrzędnego kontrolki wysyłania powiadomień.

*memberFxn*<br/>
Funkcja elementu członkowskiego, wywoływana, gdy to powiadomienie jest wysyłane.

Funkcja elementu członkowskiego musi być zadeklarowany z poniższy prototyp:

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

gdzie parametrami są:

*pNotifyStruct*<br/>
Wskaźnik do struktury powiadomień, zgodnie z opisem w poprzedniej sekcji.

*wynik*<br/>
Wskaźnik do kodu wyniku zostanie ustawiona przed zwróceniem.

## <a name="example"></a>Przykład

Aby określić, że funkcja elementu członkowskiego `OnKeydownList1` może obsługiwać komunikaty LVN_KEYDOWN z `CListCtrl` których identyfikator jest `IDC_LIST1`, ClassWizard umożliwiają Dodaj następujący element do mapy wiadomości:

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

W powyższym przykładzie funkcja dostarczone przez ClassWizard jest następująca:

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

Należy pamiętać, ClassWizard automatycznie dostarcza wskaźnik właściwego typu. Dostęp do struktury powiadomień przy użyciu jednej *pNMHDR* lub *pLVKeyDow*.

##  <a name="_mfcnotes_on_notify_range"></a> ON_NOTIFY_RANGE —

Jeśli musisz przetworzyć ten sam komunikat WM_NOTIFY zbiór kontrolek, można użyć ON_NOTIFY_RANGE zamiast ON_NOTIFY. Na przykład masz zestaw przycisków, dla której chcesz wykonać tę samą akcję dla komunikatu powiadomienia.

Gdy używasz ON_NOTIFY_RANGE, określasz ciągły zakres identyfikatorów podrzędnych dla którego, by obsłużyć komunikat powiadomienia, określając początkowy i końcowy identyfikatorów podrzędnych zakresu.

ClassWizard nie obsługuje ON_NOTIFY_RANGE; Aby go użyć, należy edytować mapy wiadomości, samodzielnie.

Wpis mapy komunikatów i prototypu funkcji ON_NOTIFY_RANGE są następujące:

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

gdzie parametrami są:

*wNotifyCode*<br/>
Kod komunikatu powiadomienia mają być obsługiwane, takich jak LVN_KEYDOWN.

*id*<br/>
Pierwszy identyfikator ciągły zakres identyfikatorów.

*idLast*<br/>
Ostatni identyfikator w ciągły zakres identyfikatorów.

*memberFxn*<br/>
Funkcja elementu członkowskiego, wywoływana, gdy to powiadomienie jest wysyłane.

Funkcja elementu członkowskiego musi być zadeklarowany z poniższy prototyp:

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

gdzie parametrami są:

*id*<br/>
Identyfikator podrzędny formantu wysyłającego powiadomienia.

*pNotifyStruct*<br/>
Wskaźnik do struktury powiadomień, zgodnie z powyższym opisem.

*wynik*<br/>
Wskaźnik do kodu wyniku zostanie ustawiona przed zwróceniem.

##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a> ON_NOTIFY_EX —, ON_NOTIFY_EX_RANGE —

Jeśli chcesz więcej niż jeden obiekt w powiadomieniu o routingu w celu obsługi wiadomości, można użyć on_notify_ex — (lub on_notify_ex_range —) zamiast ON_NOTIFY (lub ON_NOTIFY_RANGE). Jedyną różnicą między **EX** i regularnego wersja jest, że funkcja elementu członkowskiego, wywoływana dla **EX** wersja zwraca **BOOL** oznacza to, czy Przetwarzanie komunikatu powinno być kontynuowane. Zwracanie **FALSE** z tej funkcji służy do przetwarzania ten sam komunikat w więcej niż jeden obiekt.

ClassWizard nie obsługuje on_notify_ex — lub on_notify_ex_range —; Jeśli chcesz użyć którąś z tych funkcji, należy edytować mapy wiadomości, samodzielnie.

Wpis mapy komunikatów i prototypu funkcji on_notify_ex — i on_notify_ex_range — są w następujący sposób. Znaczenie parametry są takie same jak dla innych niż**EX** wersji.

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

Prototyp dla obu powyższych jest taki sam:

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

W obu przypadkach *identyfikator* przechowuje identyfikator podrzędny formantu wysyłającego powiadomienia.

Funkcja musi zwracać **TRUE** Jeśli komunikatu powiadomienia całkowicie obsłużeniu lub **FALSE** Jeśli inne obiekty w routingu poleceń powinny mieć możliwość obsługi wiadomości.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
