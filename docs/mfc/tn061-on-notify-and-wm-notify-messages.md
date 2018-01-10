---
title: 'TN061: Komunikaty ON_NOTIFY i WM_NOTIFY | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
dev_langs: C++
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9cd99f2ff37effb1e153a759eb36c9adba5f3671
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tn061-onnotify-and-wmnotify-messages"></a>TN061: komunikaty ON_NOTIFY i WM_NOTIFY
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga techniczna podano informacje dotyczące nowego **WM_NOTIFY** wiadomości i opisuje zalecane (i najbardziej typowych) sposób obsługi **WM_NOTIFY** wiadomości w aplikacji MFC.  
  
 **Komunikaty powiadomień w systemie Windows 3.x**  
  
 W systemie Windows 3.x, formanty powiadomić ich nadrzędnych zdarzenia, takie jak kliknięcie myszą zmiany w zawartości i wyboru i rysowania tła formantu, wysyłając wiadomość do elementu nadrzędnego. Proste powiadomienia są wysyłane jako specjalne **WM_COMMAND** wiadomości z kodem powiadomienia (takich jak **BN_CLICKED**) i identyfikator spakowane do formantu `wParam` i uchwyt formantu w `lParam`. Należy pamiętać, że od momentu `wParam` i `lParam` są pełne, nie istnieje sposób do przekazania dodatkowych danych — komunikaty te mogą być tylko proste powiadomienia. Na przykład w **BN_CLICKED** powiadomienia, nie istnieje sposób wysyłanie informacji o lokalizacji kursora myszy, gdy kliknięto przycisk.  
  
 Podczas kontroli Windows 3.x należy wysłać komunikatu powiadomienia, który zawiera dodatkowe dane, używają różnych specjalnych wiadomości, łącznie z `WM_CTLCOLOR`, `WM_VSCROLL`, `WM_HSCROLL`, `WM_DRAWITEM`, `WM_MEASUREITEM`, `WM_COMPAREITEM`, `WM_DELETEITEM`, `WM_CHARTOITEM`, `WM_VKEYTOITEM`i tak dalej. Te komunikaty można uwzględnione do formantu, który je wysłać. Aby uzyskać więcej informacji, zobacz [TN062: odbicie komunikatu dla formantów systemu Windows](../mfc/tn062-message-reflection-for-windows-controls.md).  
  
 **Komunikaty powiadomień w systemie Win32**  
  
 Dla formantów, które były dostępne w systemie Windows 3.1, interfejs API Win32 używa większość komunikatów powiadomień, które były używane w systemie Windows 3.x. Jednak Win32 również dodaje szeregu kontroli, zaawansowane, złożone do obsługiwanych w systemie Windows 3.x. Często tych kontrolek musi wysłać dodatkowe dane z ich komunikaty powiadomień. Zamiast dodawać nowe **WM_\***  komunikat dla każdego nowe powiadomienie, które wymaga dodatkowych danych, projektantów Win32 API wybrał opcję Dodaj tylko jeden komunikat **WM_NOTIFY**, które można przekazać żadnego ilości dodatkowych danych w sposób standardowy.  
  
 **WM_NOTIFY** wiadomości zawierają identyfikator formantu, wysyłanie komunikatu `wParam` i wskaźnika do struktury w `lParam`. Ta struktura jest **NMHDR** struktury lub niektóre większej struktury, która ma **NMHDR** struktury jako swojego pierwszego elementu członkowskiego. Należy pamiętać, że od momentu **NMHDR** element członkowski jest pierwszy, wskaźnik do struktury może być używany jako wskaźnik do **NMHDR** lub jako wskaźnik do większej struktury w zależności od tego, jak rzutowania.  
  
 W większości przypadków wskaźnik będzie wskazywać większej struktury i należy rzutować go, gdy jest używany. Tylko kilka powiadomień, takie jak wspólnej powiadomienia (o nazwach zaczynających **NM_**) i formantem etykietki narzędzia **TTN_SHOW** i **TTN_POP** powiadomienia, to **NMHDR** struktury rzeczywiście używane.  
  
 **NMHDR** struktury lub elementu członkowskiego początkowej zawiera dojście i identyfikator formantu wysyłania wiadomości i kod powiadomienia (takich jak **TTN_SHOW**). Format **NMHDR** struktury przedstawiono poniżej:  
  
```  
typedef struct tagNMHDR {  
    HWND hwndFrom;  
    UINT idFrom;  
    UINT code;  
} NMHDR;  
```  
  
 Dla **TTN_SHOW** wiadomości, **kod** będzie miał ustawienie elementu członkowskiego **TTN_SHOW**.  
  
 Większość powiadomienia przekazać wskaźnik do większej struktury, która zawiera **NMHDR** struktury jako swojego pierwszego elementu członkowskiego. Na przykład, należy wziąć pod uwagę struktury używane przez formant widoku listy **LVN_KEYDOWN** komunikat powiadomienia, który jest wysyłany, gdy zostanie naciśnięty klawisz w kontrolce widoku listy. Wskaźnik wskazuje **LV_KEYDOWN** struktury, która jest zdefiniowana w sposób przedstawiony poniżej:  
  
```  
typedef struct tagLV_KEYDOWN {  
    NMHDR hdr;     
    WORD wVKey;    
    UINT flags;    
} LV_KEYDOWN;  
```  
  
 Należy pamiętać, że od momentu **NMHDR** element członkowski jest pierwszy w tej strukturze, wskaźnika jest przekazano komunikat powiadomienia mogą być rzutowane na wskaźnik do **NMHDR** lub wskaźnika do **LV_KEYDOWN** .  
  
 **Typowe powiadomienia do wszystkich nowych formantów systemu Windows**  
  
 Niektóre powiadomienia są wspólne dla wszystkich nowych formantów systemu Windows. Te powiadomienia wskaźnikiem do **NMHDR** struktury.  
  
|Kod powiadomienia|Wysłać, ponieważ|  
|-----------------------|------------------|  
|**NM_CLICK**|Użytkownik kliknął lewym przyciskiem myszy w formancie|  
|**NM_DBLCLK —**|Użytkownik dwukrotnym kliknięciu lewym przyciskiem myszy w formancie|  
|**NM_RCLICK —**|Użytkownik kliknął prawym przyciskiem myszy w formancie|  
|**NM_RDBLCLK —**|Użytkownik dwukrotnym kliknięciu prawym przyciskiem myszy w formancie|  
|**NM_RETURN —**|Użytkownik naciśnięciu klawisza ENTER, gdy formant ma wejściowych fokus|  
|**NM_SETFOCUS —**|Formant ma fokus wprowadzania|  
|**NM_KILLFOCUS —**|Kontrolka utraciła fokus wprowadzania|  
|**NM_OUTOFMEMORY —**|Formant nie można ukończyć operacji, ponieważ nie był dostępny za mało pamięci|  
  
##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>On_notify —: Obsługa WM_NOTIFY komunikatów w aplikacjach MFC  
 Funkcja `CWnd::OnNotify` obsługi komunikatów powiadomień. Jego domyślna implementacja sprawdza mapy komunikatów dla programów obsługi powiadomień do wywołania. Ogólnie rzecz biorąc, możesz nie zastępują `OnNotify`. Należy podać funkcji obsługi i dodanie wpisu mapy komunikatów dla tego programu obsługi do mapy komunikatów z oknem właściciela klasy.  
  
 ClassWizard, za pomocą ClassWizard arkusza właściwości, można utworzyć `ON_NOTIFY` wpisu mapy wiadomości i udostępnić funkcję obsługi szkielet. Aby uzyskać więcej informacji na temat używania ClassWizard ułatwić, zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).  
  
 `ON_NOTIFY` Makra map wiadomości ma następującą składnię:  
  
```  
 
ON_NOTIFY(
wNotifyCode  ,  
id  ,
    memberFxn)  
 
```  
  
 gdzie są zastępowane kursywy parametry:  
  
 `wNotifyCode`  
 Kod komunikatu powiadomienia, które mają być obsługiwane, takich jak **LVN_KEYDOWN**.  
  
 `id`  
 Identyfikator podrzędnych formantu, dla którego jest wysyłane powiadomienie.  
  
 `memberFxn`  
 Funkcja członkowska wywoływana, gdy to powiadomienie jest wysyłane.  
  
 Funkcja elementu członkowskiego musi być zadeklarowany z następującym prototypie:  
  
```  
 
afx_msg void  
memberFxn  
(NMHDR* 
pNotifyStruct  , LRESULT* result);

 
```  
  
## <a name="remarks"></a>Uwagi  
 gdy kursywy parametry są:  
  
 `pNotifyStruct`  
 Wskaźnik do struktury powiadomień, zgodnie z opisem w poprzedniej sekcji.  
  
 *wynik*  
 Wskaźnik do kod wyniku zostanie ustawiona przed zwróceniem.  
  
## <a name="example"></a>Przykład  
 Aby określić, że funkcja członkowska `OnKeydownList1` do obsługi **LVN_KEYDOWN** komunikaty z `CListCtrl` których identyfikator jest `IDC_LIST1`, należy użyć ClassWizard, aby dodać następujące mapy komunikatów:  
  
```  
ON_NOTIFY(LVN_KEYDOWN,
    IDC_LIST1,
    OnKeydownList1)  
```  
  
 W powyższym przykładzie funkcja podał ClassWizard jest:  
  
```  
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)  
{  
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR; *// TODO: Add your control notification handler *//       code here  
 
 *pResult = 0;  
}  
```  
  
 Uwaga ClassWizard automatycznie zapewnia wskaźnika prawidłowego typu. Dostęp do struktury powiadomień przy użyciu jednej `pNMHDR` lub `pLVKeyDow`.  
  
##  <a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE —  
 Aby przetwarzać takie same **WM_NOTIFY** komunikat zestaw kontrolek, można użyć **on_notify_range —** zamiast `ON_NOTIFY`. Na przykład może być zestaw przycisków, dla której chcesz wykonać tę samą akcję dla komunikatu powiadomienia.  
  
 Jeśli używasz **on_notify_range —**, określ ciągły zakres identyfikatorów podrzędnych dla którego, by obsłużyć komunikat powiadomienia przez określenie początku i zakończenia podrzędne identyfikatory zakresu.  
  
 Nie obsługuje ClassWizard **on_notify_range —**; używane, należy edytować mapy komunikatów samodzielnie.  
  
 Prototyp wpisu i funkcja mapy komunikatów dla **on_notify_range —** są następujące:  
  
```  
 
ON_NOTIFY_RANGE(
wNotifyCode  ,   
id  ,   
idLast  ,
    memberFxn)  
 
```  
  
 gdzie są zastępowane kursywy parametry:  
  
 `wNotifyCode`  
 Kod komunikatu powiadomienia, które mają być obsługiwane, takich jak **LVN_KEYDOWN**.  
  
 `id`  
 Pierwszy identyfikator w ciągły zakres identyfikatorów.  
  
 `idLast`  
 Identyfikator ostatniego w ciągły zakres identyfikatorów.  
  
 `memberFxn`  
 Funkcja członkowska wywoływana, gdy to powiadomienie jest wysyłane.  
  
 Funkcja elementu członkowskiego musi być zadeklarowany z następującym prototypie:  
  
```  
 
afx_msg void  
memberFxn  
(UINT   
id  ,
    NMHDR* 
pNotifyStruct  ,
    LRESULT* result);

 
```  
  
## <a name="remarks"></a>Uwagi  
 gdy kursywy parametry są:  
  
 `id`  
 Identyfikator podrzędnych formantu, który wysyłane powiadomienia.  
  
 `pNotifyStruct`  
 Wskaźnik do struktury powiadomień, jak opisano powyżej.  
  
 *wynik*  
 Wskaźnik do kod wyniku zostanie ustawiona przed zwróceniem.  
  
##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX —, ON_NOTIFY_EX_RANGE —  
 Jeśli chcesz, aby więcej niż jeden obiekt w powiadomieniu routingu do obsługi wiadomości, można użyć **on_notify_ex —** (lub **on_notify_ex_range —**) zamiast `ON_NOTIFY` (lub **on_notify_range —** ). Jedyną różnicą między **EX** i regularnego wersja jest, że funkcja członkowska wywołana dla **EX** zwraca wersji **BOOL** wskazujące, czy Przetwarzanie komunikatów powinno być kontynuowane. Zwracanie **FALSE** z tej funkcji umożliwia przetworzenie tego samego komunikatu w więcej niż jeden obiekt.  
  
 Nie obsługuje ClassWizard **on_notify_ex —** lub **on_notify_ex_range —**; Jeśli chcesz użyć dowolnej z tych funkcji, należy edytować mapy komunikatów samodzielnie.  
  
 Prototyp wpisu i funkcja mapy komunikatów dla **on_notify_ex —** i **on_notify_ex_range —** są następujące. Parametry są takie same jak dla innych niż -**EX** wersji.  
  
```  
 
ON_NOTIFY_EX(
nCode  ,  
id  ,
    memberFxn) ON_NOTIFY_EX_RANGE(
wNotifyCode  ,   
id  ,   
idLast  ,
    memberFxn)  
 
```  
  
 Prototyp dla obu powyższych jest taka sama:  
  
```  
 
afx_msg BOOL  
memberFxn  
(UINT   
id  ,
    NMHDR* 
pNotifyStruct  ,
    LRESULT* result);

 
```  
  
## <a name="remarks"></a>Uwagi  
 W obu przypadkach `id` zawiera identyfikator podrzędnych formantu, który wysyłane powiadomienia.  
  
 Funkcja musi zwracać **TRUE** jeśli całkowicie obsługiwane komunikatu powiadomienia lub **FALSE** Jeśli inne obiekty w routing poleceń powinien mieć możliwość obsługi wiadomości.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

