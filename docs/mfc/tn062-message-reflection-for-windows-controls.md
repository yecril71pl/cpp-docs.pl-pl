---
title: 'TN062: Komunikat odbicie dla formantów Windows | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
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
ms.openlocfilehash: 994095042dc473fda315b6d842d9ec9355ff3671
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055401"
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062: odbicie komunikatu dla formantów systemu Windows

> [!NOTE]
> Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga techniczna opisano odbicie komunikatu, nowa funkcja w wersji 4.0 MFC. Zawiera ona także wskazówki dotyczące tworzenia prostego formantu wielokrotnego użytku, który korzysta odbicie komunikatu.

Ta uwaga techniczna nie omówiono w nim odbicie komunikatu ma zastosowanie do kontrolki ActiveX (dawniej nazywanych formantów OLE). Można znaleźć w artykule [kontrolek ActiveX: Tworzenie podklasy kontrolki Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).

**Co to jest odbicie komunikatu**

Formanty Windows często wysyłać powiadomienia do ich nadrzędnej systemu windows. Na przykład wiele kontrolek wysłać komunikatu powiadomienia kolor kontrolki (wm_ctlcolor — lub jednego z jej wariantów), do ich nadrzędnej umożliwiające nadrzędnego do dostarczania pędzel dla tła formantu do malowania.

W Windows i MFC przed wersją 4.0 okno nadrzędne, często okno dialogowe, jest odpowiedzialny za obsługę tych komunikatów. Oznacza to, że kod do obsługi komunikatu musi być w klasie okno nadrzędne i że ma zostać zduplikowane w każdej klasy, która wymaga, by obsłużyć ten komunikat. W przypadku powyższych co okno dialogowe, które chcieli kontrolek z niestandardowe tła musi obsłużyć komunikat powiadomienia kolor kontrolki. Byłoby znacznie ułatwia ponowne użycie kodu, jeśli klasa sterowania mogłyby być zapisywane, która będzie obsługiwać własne kolor tła.

W wersji 4.0 MFC, wciąż działa mechanizm stare — windows nadrzędny może obsługiwać komunikaty powiadomień. Ponadto, jednak MFC 4.0 ułatwia ponowne użycie, zapewniając funkcję o nazwie "komunikat odbicie" umożliwiająca te powiadomienia mają być obsługiwane w okno kontrolki podrzędne lub okno nadrzędne lub obu. W przykładzie kolor tła kontrolki, teraz możesz tworzyć klasy kontrolki, która ustawia kolor tła, obsługa komunikatów odbitych wm_ctlcolor — — wszystko to bez konieczności polegania na element nadrzędny. (Należy pamiętać, że ponieważ odbicie komunikatu jest implementowany przez MFC, nie przez Windows, klasy okna nadrzędny musi pochodzić od `CWnd` dla odbicie komunikatu do pracy.)

Starsze wersje biblioteki MFC zostało coś podobnego do odbicie komunikatu, udostępniając funkcje wirtualne kilka wiadomości, takich jak wiadomości dla okna listy rysowane przez właściciela (WM_DRAWITEM i tak dalej). Nowy mechanizm odbicia wiadomości jest uogólniony i spójne.

Odbicie komunikatu jest zgodne z poprzednimi wersjami przy użyciu kodu napisanego dla wersji MFC przed 4.0.

Program obsługi dla określonej wiadomości podano lub szeregu wiadomości w klasie okna nadrzędnego, spowoduje zastąpienie odzwierciedlona programy obsługi komunikatów dla tej samej wiadomości pod warunkiem nie wywołuj klasy bazowej funkcji obsługi własnego programu obsługi. Na przykład w wm_ctlcolor — można obsłużyć w klasie okno dialogowe, obsługi usługi spowoduje zastąpienie wszelkich programy obsługi komunikatów odbitych.

Jeśli w klasie nadrzędnej okna podasz Obsługa określony komunikat WM_NOTIFY lub komunikaty zakresu WM_NOTIFY, programu obsługi zostanie wywołana tylko wtedy, gdy kontrolka podrzędna wysyłania tych wiadomości nie ma program obsługi komunikatów odbitych za pośrednictwem `ON_NOTIFY_REFLECT()`. Jeśli używasz `ON_NOTIFY_REFLECT_EX()` na mapie komunikatów programu obsługi komunikatów może być lub może nie pozwalać na okno nadrzędne, by obsłużyć komunikat. Jeśli program obsługi zwraca **FALSE**, wiadomość będzie obsługiwany przez nadrzędny, jak również podczas wywołania, które zwraca **TRUE** nie zezwala na nadrzędnego do jego obsługi. Należy pamiętać, że komunikatów odbitych odbywa się przed komunikat powiadomienia.

Po wysłaniu komunikatu WM_NOTIFY formant jest dostępna w pierwszej szansy do jego obsługi. Jeśli inne komunikatów odbitych zostanie wysłany, okno nadrzędne jest pierwszym szansę, aby go obsłużyć, a kontrolki będą otrzymywać komunikatów odbitych. Aby to zrobić, należy w funkcji obsługi i odpowiedni wpis w mapie komunikatów klasy formantu.

Makra mapy komunikatów dla komunikatów odbitych jest nieco inne niż w przypadku regularnego powiadomienia: ma *_REFLECT* dołączany do nazwy zwykle. Na przykład aby obsłużyć komunikat WM_NOTIFY w obiekcie nadrzędnym, należy użyć ON_NOTIFY — makro w mapie komunikatów elementu nadrzędnego. Do obsługi komunikatów odbitych w kontrolki podrzędnej, należy użyć makra on_notify_reflect — w mapie komunikatów kontrolki podrzędnej. W niektórych przypadkach parametry różnią się, jak również. Pamiętaj, że ClassWizard można zwykle dodać wpisy mapy komunikatów dla Ciebie dostarczać implementacje szkielet funkcji z prawidłowymi parametrami.

Zobacz [TN061: komunikaty ON_NOTIFY i Wm_notify](../mfc/tn061-on-notify-and-wm-notify-messages.md) uzyskać informacji na temat nowy komunikat WM_NOTIFY.

**Wpisy mapy komunikatów i prototypy funkcji obsługi dla komunikatów odbitych**

Aby obsłużyć komunikat z powiadomieniem odbitych kontroli, użyj makra map wiadomości i prototypy funkcji wymienionych w poniższej tabeli.

ClassWizard zazwyczaj można dodać te wpisy mapy komunikatów dla Ciebie i dostarczać implementacje funkcji szkielet. Zobacz [Definiowanie obsługi komunikatów dla komunikatów odzwierciedlone](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md) informacji o tym, jak zdefiniować programy obsługi dla komunikatów odbitych.

Aby przekonwertować z nazwa komunikatu nazwy odbitych makra, należy poprzedzić *ON_* obiektów blob i uzupełnialnych *_REFLECT*. Na przykład wm_ctlcolor — staje się ON_WM_CTLCOLOR_REFLECT. (Aby zobaczyć, wiadomości, które można uwzględnione, należy przeprowadzić konwersję przeciwny we wpisach makra w poniższej tabeli.)

Dostępne są następujące trzy wyjątki od reguły powyżej:

- Makro WM_COMMAND powiadomień jest ON_CONTROL_REFLECT.

- Makra dla odbić WM_NOTIFY jest on_notify_reflect —.

- Makra dla odbić ON_UPDATE_COMMAND_UI jest ON_UPDATE_COMMAND_UI_REFLECT.

We wszystkich powyższych przypadkach specjalne należy określić nazwę funkcji elementu członkowskiego programu obsługi. W innych przypadkach należy użyć standardowej nazwy funkcji procedury obsługi.

Znaczenie parametry i zwracane wartości funkcji opisano w nazwy funkcji lub nazwy funkcji za pomocą *na* dołączony. Na przykład `CtlColor` jest udokumentowany w `OnCtlColor`. Programy obsługi komunikatów odbitych kilka muszą mniej parametrów niż podobne programy obsługi, w oknie nadrzędnym. Po prostu być zgodne z nazwami w poniższej tabeli za pomocą nazwy parametrów formalnych w dokumentacji.

|Wpis mapy|Prototyp funkcji|
|---------------|------------------------|
|**ON_CONTROL_REFLECT (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **();**|
|**ON_NOTIFY_REFLECT — (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *wynik* **);**|
|**ON_UPDATE_COMMAND_UI_REFLECT (** `memberFxn` **)**|**afx_msg void** `memberFxn` **(CCmdUI** <strong>\*</strong> `pCmdUI` **);**|
|**ON_WM_CTLCOLOR_REFLECT)**|**afx_msg HBRUSH CtlColor (CDC** <strong>\*</strong> `pDC` **, UINT** `nCtlColor` **);**|
|**ON_WM_DRAWITEM_REFLECT)**|**afx_msg void drawitem — (LPDRAWITEMSTRUCT** `lpDrawItemStruct` **);**|
|**ON_WM_MEASUREITEM_REFLECT)**|**afx_msg void measureitem — (LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **);**|
|**ON_WM_DELETEITEM_REFLECT)**|**afx_msg void DeleteItem (LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **);**|
|**ON_WM_COMPAREITEM_REFLECT)**|**afx_msg int CompareItem (LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **);**|
|**ON_WM_CHARTOITEM_REFLECT)**|**afx_msg int CharToItem (UINT** `nKey` **, UINT** `nIndex` **);**|
|**ON_WM_VKEYTOITEM_REFLECT)**|**afx_msg int VKeyToItem (UINT** `nKey` **, UINT** `nIndex` **);**|
|**ON_WM_HSCROLL_REFLECT)**|**afx_msg void HScroll (UINT** `nSBCode` **, UINT** `nPos` **);**|
|**ON_WM_VSCROLL_REFLECT)**|**afx_msg void VScroll (UINT** `nSBCode` **, UINT** `nPos` **);**|
|**ON_WM_PARENTNOTIFY_REFLECT)**|**afx_msg void ParentNotify (UINT** `message` **, LPARAM** `lParam` **);**|

On_notify_reflect — i ON_CONTROL_REFLECT makra mają odmiany, zezwalających na więcej niż jeden obiekt (na przykład formantem i jego element nadrzędny) do obsługi danego komunikatu.

|Wpis mapy|Prototyp funkcji|
|---------------|------------------------|
|**ON_NOTIFY_REFLECT_EX — (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *wynik* **);**|
|**ON_CONTROL_REFLECT_EX (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **();**|

## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>Obsługa Reflected wiadomości: Przykład kontrolki do ponownego wykorzystania

Ten prosty przykład tworzy formant wielokrotnego użytku, nazywany `CYellowEdit`. Kontrolka działa tak samo, jako kontrolka edycji regularnych, z tą różnicą, że wyświetla czarny tekst w żółte tło. Możesz ją łatwo dodawać funkcje Członkowskie, które pozwalałyby na `CYellowEdit` formantu, aby wyświetlić różne kolory.

### <a name="to-try-the-example-that-creates-a-reusable-control"></a>Aby wypróbować przykładu, który tworzy formant wielokrotnego użytku

1. Tworzenie nowego okna dialogowego w istniejącej aplikacji. Aby uzyskać więcej informacji, zobacz [Edytor okien dialogowych](../windows/dialog-editor.md) tematu.

   Musi korzystać z aplikacji, w której do tworzenia kontrolki do ponownego użycia. Jeśli nie masz istniejącej aplikacji do użycia, należy utworzyć aplikację oparta na oknach dialogowych za pomocą Kreatora AppWizard.

2. Za pomocą projektu załadowane do Visual C++, użyj ClassWizard, aby utworzyć nową klasę o nazwie `CYellowEdit` na podstawie `CEdit`.

3. Dodaj trzy zmienne Członkowskie swojej `CYellowEdit` klasy. Pierwsze dwie będą *COLORREF* zmienne do przechowywania kolor tekstu i kolor tła. Trzeci będzie `CBrush` obiektu, który będzie przechowywać pędzel dla tła do malowania. `CBrush` Obiekt umożliwia tworzenie pędzla, jeden raz, jedynie do niego odwoływać później i zniszcz pędzel automatycznie po `CYellowEdit` zniszczenia kontrolki.

4. Inicjowanie zmiennych składowych, pisząc Konstruktor w następujący sposób:

    ```cpp
    CYellowEdit::CYellowEdit()
    {
        m_clrText = RGB(0, 0, 0);
        m_clrBkgnd = RGB(255, 255, 0);
        m_brBkgnd.CreateSolidBrush(m_clrBkgnd);
    }
    ```

5. Przy użyciu ClassWizard, Dodaj program obsługi dla komunikatów odbitych wm_ctlcolor —, aby Twoje `CYellowEdit` klasy. Należy pamiętać, znak równości przed nazwą wiadomości na liście komunikatów, które można obsługiwać wskazuje, czy komunikat jest widoczny. Jest to opisane w [Definiowanie obsługi komunikatów dla komunikatów odzwierciedlone](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

   ClassWizard dodaje następującą funkcję makro i szkielet mapy komunikatów dla Ciebie:

    ```cpp
    ON_WM_CTLCOLOR_REFLECT()
    // Note: other code will be in between....

    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)
    {
        // TODO: Change any attributes of the DC here
        // TODO: Return a non-NULL brush if the
        //       parent's handler should not be called
        return NULL;
    }
    ```

6. Zastąp treści funkcji następującym kodem. Kod ten określa kolor tekstu, kolor tła tekstu i kolor tła w pozostałej części kontrolki.

    ```cpp
    pDC->SetTextColor(m_clrText);   // text
    pDC->SetBkColor(m_clrBkgnd);    // text bkgnd
    return m_brBkgnd;               // ctl bkgnd
    ```

7. Utwórz formant edycji w oknie dialogowym, a następnie dołączyć go ze zmienną członkowską przez dwukrotne kliknięcie kontrolki edycji, przytrzymując klawisz control w dół. W oknie dialogowym Dodawanie zmiennej członkowskiej Zakończ nazwę zmiennej, a następnie wybierz "w elemencie Control" dla kategorii, a następnie "CYellowEdit" dla typu zmiennej. Należy pamiętać ustawić kolejność tabulacji w oknie dialogowym. Ponadto należy uwzględnić plik nagłówka dla `CYellowEdit` formantu w pliku nagłówkowym okno dialogowe.

8. Skompiluj i uruchom aplikację. Kontrolka edycji będzie miała żółte tło.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
