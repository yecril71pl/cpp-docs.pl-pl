---
title: 'TN062: Komunikatu odbicia dla formantów systemu Windows | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls.messages
dev_langs:
- C++
helpviewer_keywords:
- ON_WM_VKEYTOITEM_REFLECT macro [MFC]
- ON_WM_DRAWITEM_REFLECT macro [MFC]
- ON_WM_VSCROLL_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT message [MFC]
- ON_CONTROL_REFLECT_EX macro [MFC]
- ON_UPDATE_COMMAND_UI_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT_EX message [MFC]
- ON_WM_HSCROLL_REFLECT macro [MFC]
- message reflection [MFC]
- ON_WM_COMPAREITEM_REFLECT macro [MFC]
- ON_WM_MEASUREITEM_REFLECT macro [MFC]
- ON_NOTIFY message [MFC]
- WM_COMMAND [MFC]
- WM_CTLCOLOR message [MFC]
- TN062 [MFC]
- ON_WM_CHARTOITEM_REFLECT macro [MFC]
- ON_WM_CTLCOLOR_REFLECT macro [MFC]
- ON_WM_DELETEITEM_REFLECT macro [MFC]
- notification messages [MFC]
- ON_WM_PARENTNOTIFY_REFLECT macro [MFC]
- WM_NOTIFY message [MFC]
- ON_CONTROL_REFLECT macro
ms.assetid: 53efb0ba-fcda-4fa0-a3c7-14e0b78fb494
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba8e9cac3b7f7997da8c620966234a630b9b9fbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062: odbicie komunikatu dla formantów systemu Windows
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga techniczna opisuje odbicie wiadomości, nowa funkcja w wersji 4.0 MFC. Zawiera również wskazówki dotyczące tworzenia prostego formantu wielokrotnego użytku, który korzysta odbicie wiadomości.  
  
 Ta uwaga techniczna nie omówiono w nim odbicie wiadomości mają zastosowanie do formantów ActiveX (wcześniej nazywanych formantów OLE). Zobacz artykuł [formantów ActiveX: Tworzenie podklasy kontrolki okna](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
 **Odbicie wiadomości co to jest**  
  
 Formanty systemu Windows często wysyłać powiadomienia do ich nadrzędnej systemu windows. Na przykład wiele formantów wysłać komunikatu powiadomienia kolor formantu (`WM_CTLCOLOR` lub jednej z jej wariantów) do ich nadrzędnej, umożliwia nadrzędnego do dostarczania pędzel dla tła formantu malowania.  
  
 W systemie Windows i MFC przed w wersji 4.0 okno nadrzędne, często okno dialogowe, jest odpowiedzialny za obsługę tych wiadomości. Oznacza to, że kodu do obsługi komunikatu musi być w klasie okno nadrzędne i że ma być zduplikowany w każdej klasy, który musi obsługiwać tę wiadomość. W przypadku powyższych co okno dialogowe, którego chce formantów z niestandardowe tła musi obsłużyć komunikat powiadomienia kolor formantu. Jest znacznie ułatwia ponowne użycie kodu, jeśli klasa sterowania może być zapisany, który będzie obsługiwać kolor tła.  
  
 W MFC 4.0, nadal działa starego mechanizmu — windows nadrzędny może obsługiwać powiadomień. Ponadto, jednak MFC 4.0 ułatwia ponownemu zapewniając funkcję o nazwie "odbicie komunikatu" umożliwiająca te komunikaty powiadomień mają być obsługiwane w okno podrzędne kontrolki lub okna nadrzędnego, lub oba. W przykładzie kolor tła formantu można teraz zapisać klasy formantu, który ustawia kolor tła dzięki obsłudze odbite `WM_CTLCOLOR` wiadomości — wszystko to bez polegania na element nadrzędny. (Należy pamiętać, że od czasu odbicie wiadomości jest implementowany przez MFC, nie przez system Windows, klasę okna nadrzędnego musi pochodzić z `CWnd` dla odbicie wiadomości do pracy.)  
  
 Starsze wersje biblioteki MFC wykonała podobne do odbicie wiadomości, podając funkcji wirtualnych kilka komunikaty, takie jak wiadomości dla pola listy rysowane przez właściciela (`WM_DRAWITEM`i tak dalej). Mechanizm odbicie komunikatu jest ogólnych i spójny.  
  
 Odbicie wiadomości jest zgodna z kodu napisanego dla wersji MFC przed 4.0.  
  
 Jeśli podano obsługi dla określonego komunikatu lub zakresu wiadomości w klasie okna nadrzędnego spowoduje zastąpienie odzwierciedlane obsługi komunikatów dla tego samego komunikatu pod warunkiem nie wywołanie funkcji obsługi klasy podstawowej własnego programu obsługi. Na przykład, jeśli można obsługiwać `WM_CTLCOLOR` w klasie — okno dialogowe programu obsługi spowoduje zastąpienie wszelkich programy obsługi komunikatów odbitych.  
  
 Jeśli w klasie okna nadrzędnego, podaj obsługi dla określonego **WM_NOTIFY** wiadomości lub zakres **WM_NOTIFY** wiadomości, programu obsługi będzie można wywołać tylko wtedy, gdy formant podrzędny wysyłania tych wiadomości wykonuje nie ma obsługi komunikatów odbitych za pośrednictwem **ON_NOTIFY_REFLECT()**. Jeśli używasz **ON_NOTIFY_REFLECT_EX()** na mapie komunikatów programu obsługi wiadomości mogą lub nie zezwalają okno nadrzędne, by obsłużyć komunikat. Jeśli program obsługi zwraca **FALSE**, komunikat będzie obsługiwany przez element nadrzędny, jak również podczas wywołania, które zwraca **TRUE** nie zezwala na element nadrzędny do jego obsługi. Należy pamiętać, że komunikatów odbitych odbywa się przed komunikat powiadomienia.  
  
 Gdy **WM_NOTIFY** jest wysyłany komunikat, kontrolka jest oferowany pierwszej szansy do jego obsługi. Jeśli inne komunikatów odbitych, pierwszy możliwość jego obsługa ma okno nadrzędne i formant będzie otrzymywać komunikatów odbitych. Aby to zrobić, należy w funkcji programu obsługi i odpowiedni wpis w mapie komunikatów klasy formantu.  
  
 Makra mapy komunikatów dla komunikatów odbitych są nieco inne niż regularnych powiadomień: ma **_REFLECT** dołączany do zwykłych nazwy. Na przykład do obsługi **WM_NOTIFY** komunikat w obiekcie nadrzędnym, można użyć makra `ON_NOTIFY` w mapie komunikatów elementu nadrzędnego. Do obsługi komunikatów odbitych w formant podrzędny, użyj **on_notify_reflect —** makra mapy wiadomości kontrolki podrzędnej. W niektórych przypadkach parametry są różne, a także. Zauważ, że ClassWizard można zwykle dodać wpisy mapy wiadomości dla Ciebie i zawierać implementacje szkielet funkcji z prawidłowymi parametrami.  
  
 Zobacz [TN061: komunikaty ON_NOTIFY i WM_NOTIFY](../mfc/tn061-on-notify-and-wm-notify-messages.md) informacji na nowym **WM_NOTIFY** wiadomości.  
  
 **Wpisy mapy wiadomości i prototypy funkcji obsługi komunikatów odbitych**  
  
 Do obsługi komunikatu powiadomienia odbite kontroli, użyj makra map wiadomości i prototypy funkcji wymienionych w poniższej tabeli.  
  
 ClassWizard zwykle można dodać te wpisy mapy wiadomości dla Ciebie i udostępniać implementacji funkcji szkielet. Zobacz [Definiowanie obsługi komunikatów dla komunikatu odzwierciedlone](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md) informacji o sposobie Zdefiniuj programy obsługi komunikatów odbitych.  
  
 Aby przekonwertować z nazwy komunikatu nazwa odbite makra, dołączenie wartości **ON_** i Dołącz **_REFLECT**. Na przykład `WM_CTLCOLOR` staje się **on_wm_ctlcolor_reflect —**. (Aby wyświetlić wiadomości, które można uwzględnione, należy wykonać konwersję przeciwną we wpisach makra w poniższej tabeli.)  
  
 Dostępne są następujące trzy wyjątki zasadę powyżej:  
  
-   Makra dla **WM_COMMAND** powiadomień jest **on_control_reflect —**.  
  
-   Makra dla **WM_NOTIFY** jest odbić **on_notify_reflect —**.  
  
-   Makra dla `ON_UPDATE_COMMAND_UI` jest odbić **on_update_command_ui_reflect —**.  
  
 W każdej z powyższych przypadków specjalnych należy określić nazwę funkcji członkowskiej obsługi. W innych przypadkach należy użyć standardową nazwą dla funkcji programu obsługi.  
  
 Znaczenie parametrów i wartości zwracane funkcji opisano w nazwę funkcji lub nazwę funkcji z **na** dołączany początku. Na przykład **CtlColor** opisano w `OnCtlColor`. Programy obsługi komunikatów odbitych kilka wymaga mniej parametrów niż podobne obsługi w okno nadrzędne. Po prostu odpowiadają nazwom w poniższej tabeli z nazwami formalnych parametrów w dokumentacji.  
  
|Wpis w mapie|Prototyp funkcji|  
|---------------|------------------------|  
|**ON_CONTROL_REFLECT — (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **();**|  
|**ON_NOTIFY_REFLECT — (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **(NMHDR \***  `pNotifyStruct` **, elementu LRESULT\***  *wynik* **);**|  
|**ON_UPDATE_COMMAND_UI_REFLECT — (** `memberFxn` **)**|**afx_msg void** `memberFxn` **(CCmdUI\***  `pCmdUI` **);**|  
|**ON_WM_CTLCOLOR_REFLECT —)**|**afx_msg HBRUSH CtlColor (CDC\***  `pDC` **, UINT** `nCtlColor` **);**|  
|**ON_WM_DRAWITEM_REFLECT —)**|**afx_msg void DrawItem (LPDRAWITEMSTRUCT** `lpDrawItemStruct` **);**|  
|**ON_WM_MEASUREITEM_REFLECT —)**|**afx_msg void MeasureItem (LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **);**|  
|**ON_WM_DELETEITEM_REFLECT —)**|**afx_msg void DeleteItem (LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **);**|  
|**ON_WM_COMPAREITEM_REFLECT —)**|**afx_msg int CompareItem (LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **);**|  
|**ON_WM_CHARTOITEM_REFLECT —)**|**afx_msg int CharToItem (UINT** `nKey` **, UINT** `nIndex` **);**|  
|**ON_WM_VKEYTOITEM_REFLECT —)**|**afx_msg int VKeyToItem (UINT** `nKey` **, UINT** `nIndex` **);**|  
|**ON_WM_HSCROLL_REFLECT —)**|**afx_msg void HScroll (UINT** `nSBCode` **, UINT** `nPos` **);**|  
|**ON_WM_VSCROLL_REFLECT —)**|**afx_msg void VScroll (UINT** `nSBCode` **, UINT** `nPos` **);**|  
|**ON_WM_PARENTNOTIFY_REFLECT —)**|**afx_msg void ParentNotify (UINT** `message` **, LPARAM** `lParam` **);**|  
  
 **On_notify_reflect —** i **on_control_reflect —** makra są czcionki Zezwalaj więcej niż jeden obiekt (na przykład formantu i jego element nadrzędny) do obsługi danego komunikatu.  
  
|Wpis w mapie|Prototyp funkcji|  
|---------------|------------------------|  
|**ON_NOTIFY_REFLECT_EX — (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **(NMHDR \***  `pNotifyStruct` **, elementu LRESULT\***  *wynik* **);**|  
|**ON_CONTROL_REFLECT_EX — (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **();**|  
  
## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>Obsługa wiadomości Reflected: Przykład formantu wielokrotnego użytku  
 Ten prosty przykład tworzy kontrolkę wielokrotnego użytku, o nazwie `CYellowEdit`. Formant działa tak samo, jako formant edycji regularnych z tą różnicą, że wyświetla czarny tekst na tle żółty. Możesz ją łatwo dodać funkcje Członkowskie, które umożliwiałyby `CYellowEdit` formantu, aby wyświetlić różne kolory.  
  
#### <a name="to-try-the-example-that-creates-a-reusable-control"></a>Aby wypróbować w przykładzie, która tworzy kontrolkę wielokrotnego użytku  
  
1.  Tworzenie nowego okna dialogowego w istniejącej aplikacji. Aby uzyskać więcej informacji, zobacz [Edytor okien dialogowych](../windows/dialog-editor.md) tematu.  
  
     Musi mieć aplikację, w którym można opracowywać wielokrotnego użytku kontroli. Jeśli nie masz istniejącej aplikacji do użycia, tworzenie aplikacji opartych na oknach dialogowych za pomocą kreatorami AppWizard.  
  
2.  Z projektem załadowanych do programu Visual C++, użyj ClassWizard, aby utworzyć nową klasę o nazwie `CYellowEdit` na podstawie `CEdit`.  
  
3.  Dodaj trzy zmienne Członkowskie, aby Twoje `CYellowEdit` klasy. Pierwsze dwie będzie **COLORREF** zmienne do przechowywania kolor tekstu i kolor tła. Trzeci będzie `CBrush` obiektu, którym będą przechowywane pędzel dla tła malowania. `CBrush` Obiektu umożliwia tworzenie pędzla raz, jedynie odwołuje po i zniszcz pędzla automatycznie po `CYellowEdit` formantu zostanie zniszczony.  
  
4.  Inicjowanie zmiennych Członkowskich za zapisywanie konstruktora w następujący sposób:  
  
 ```  
    CYellowEdit::CYellowEdit() 
 {  
    m_clrText = RGB(0,
    0,
    0);

    m_clrBkgnd = RGB(255,
    255,
    0);

    m_brBkgnd.CreateSolidBrush(m_clrBkgnd);

 }  
 ```  
  
5.  Przy użyciu ClassWizard, Dodaj obsługę odbite `WM_CTLCOLOR` wiadomości do Twojej `CYellowEdit` klasy. Należy pamiętać, znak równości przed nazwą wiadomości na liście wiadomości, które może obsłużyć wskazuje, że wiadomość jest widoczny. Jest to opisane w [Definiowanie obsługi komunikatów dla komunikatu odzwierciedlone](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).  
  
     ClassWizard dodaje następująca funkcja makro i szkielet mapy komunikatów:  
  
 ```  
    ON_WM_CTLCOLOR_REFLECT() 
 *// Note: other code will be in between....  
 
    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)   
 { *// TODO: Change any attributes of the DC here  
 *// TODO: Return a non-NULL brush if the *//   parent's handler should not be called  
    return NULL;  
 }  
 ```  
  
6.  Zastąp następujący kod treści funkcji. Kod określa kolor tekstu, kolor tła tekstu i kolor tła rest formantu.  
  
 ```  
    pDC->SetTextColor(m_clrText);
*// text  
    pDC->SetBkColor(m_clrBkgnd);
*// text bkgnd  
    return m_brBkgnd;            // ctl bkgnd  
 ```  
  
7.  Tworzenie formantu edycji w oknie dialogowym, a następnie dołączyć go ze zmienną członkowską, klikając dwukrotnie kontrolki edycji podczas przytrzymując klawisz control. W oknie dialogowym Dodawanie zmiennej członkowskiej Zakończ nazwę zmiennej, a następnie wybierz pozycję "Control" dla kategorii, a następnie "CYellowEdit" dla typu zmiennej. Należy pamiętać ustawić kolejność tabulacji w oknie dialogowym. Ponadto należy uwzględnić plik nagłówka `CYellowEdit` formantu w pliku nagłówka okna dialogowego.  
  
8.  Skompiluj i uruchom aplikację. Kontrolka edycji będzie miała żółty tła.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

