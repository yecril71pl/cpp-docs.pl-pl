---
title: Klasa COleControlContainer
ms.date: 11/04/2016
f1_keywords:
- COleControlContainer
- AFXOCC/COleControlContainer
- AFXOCC/COleControlContainer::COleControlContainer
- AFXOCC/COleControlContainer::AttachControlSite
- AFXOCC/COleControlContainer::BroadcastAmbientPropertyChange
- AFXOCC/COleControlContainer::CheckDlgButton
- AFXOCC/COleControlContainer::CheckRadioButton
- AFXOCC/COleControlContainer::CreateControl
- AFXOCC/COleControlContainer::CreateOleFont
- AFXOCC/COleControlContainer::FindItem
- AFXOCC/COleControlContainer::FreezeAllEvents
- AFXOCC/COleControlContainer::GetAmbientProp
- AFXOCC/COleControlContainer::GetDlgItem
- AFXOCC/COleControlContainer::GetDlgItemInt
- AFXOCC/COleControlContainer::GetDlgItemText
- AFXOCC/COleControlContainer::HandleSetFocus
- AFXOCC/COleControlContainer::HandleWindowlessMessage
- AFXOCC/COleControlContainer::IsDlgButtonChecked
- AFXOCC/COleControlContainer::OnPaint
- AFXOCC/COleControlContainer::OnUIActivate
- AFXOCC/COleControlContainer::OnUIDeactivate
- AFXOCC/COleControlContainer::ScrollChildren
- AFXOCC/COleControlContainer::SendDlgItemMessage
- AFXOCC/COleControlContainer::SetDlgItemInt
- AFXOCC/COleControlContainer::SetDlgItemText
- AFXOCC/COleControlContainer::m_crBack
- AFXOCC/COleControlContainer::m_crFore
- AFXOCC/COleControlContainer::m_listSitesOrWnds
- AFXOCC/COleControlContainer::m_nWindowlessControls
- AFXOCC/COleControlContainer::m_pOleFont
- AFXOCC/COleControlContainer::m_pSiteCapture
- AFXOCC/COleControlContainer::m_pSiteFocus
- AFXOCC/COleControlContainer::m_pSiteUIActive
- AFXOCC/COleControlContainer::m_pWnd
- AFXOCC/COleControlContainer::m_siteMap
helpviewer_keywords:
- COleControlContainer [MFC], COleControlContainer
- COleControlContainer [MFC], AttachControlSite
- COleControlContainer [MFC], BroadcastAmbientPropertyChange
- COleControlContainer [MFC], CheckDlgButton
- COleControlContainer [MFC], CheckRadioButton
- COleControlContainer [MFC], CreateControl
- COleControlContainer [MFC], CreateOleFont
- COleControlContainer [MFC], FindItem
- COleControlContainer [MFC], FreezeAllEvents
- COleControlContainer [MFC], GetAmbientProp
- COleControlContainer [MFC], GetDlgItem
- COleControlContainer [MFC], GetDlgItemInt
- COleControlContainer [MFC], GetDlgItemText
- COleControlContainer [MFC], HandleSetFocus
- COleControlContainer [MFC], HandleWindowlessMessage
- COleControlContainer [MFC], IsDlgButtonChecked
- COleControlContainer [MFC], OnPaint
- COleControlContainer [MFC], OnUIActivate
- COleControlContainer [MFC], OnUIDeactivate
- COleControlContainer [MFC], ScrollChildren
- COleControlContainer [MFC], SendDlgItemMessage
- COleControlContainer [MFC], SetDlgItemInt
- COleControlContainer [MFC], SetDlgItemText
- COleControlContainer [MFC], m_crBack
- COleControlContainer [MFC], m_crFore
- COleControlContainer [MFC], m_listSitesOrWnds
- COleControlContainer [MFC], m_nWindowlessControls
- COleControlContainer [MFC], m_pOleFont
- COleControlContainer [MFC], m_pSiteCapture
- COleControlContainer [MFC], m_pSiteFocus
- COleControlContainer [MFC], m_pSiteUIActive
- COleControlContainer [MFC], m_pWnd
- COleControlContainer [MFC], m_siteMap
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
ms.openlocfilehash: 3aa2515b1731eafcb5e3bcfa22a56ebbc1cdfdfb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504325"
---
# <a name="colecontrolcontainer-class"></a>Klasa COleControlContainer

Działa jako kontener formantów dla kontrolek ActiveX.

## <a name="syntax"></a>Składnia

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|Konstruuje `COleControlContainer` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Tworzy lokację kontrolną hostowaną przez kontener.|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informuje wszystkie formanty hostowane, że Właściwość otoczenia została zmieniona.|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Modyfikuje określoną kontrolkę Button.|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Wybiera określony przycisk radiowy grupy.|
|[COleControlContainer:: IsControl](#createcontrol)|Tworzy hostowaną kontrolkę ActiveX.|
|[COleControlContainer::CreateOleFont](#createolefont)|Tworzy czcionkę OLE.|
|[COleControlContainer::FindItem](#finditem)|Zwraca niestandardową lokację określonej kontrolki.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Określa, czy lokacja kontrolki akceptuje zdarzenia.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|Pobiera określoną właściwość otoczenia.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|Pobiera określoną kontrolkę okna dialogowego.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Pobiera wartość określonej kontrolki okna dialogowego.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Pobiera podpis określonej kontrolki okna dialogowego.|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Określa, czy kontener obsługuje komunikaty WM_SETFOCUS.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Obsługuje komunikaty wysyłane do kontrolki bez okna.|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Określa stan określonego przycisku.|
|[COleControlContainer:: OnPaint](#onpaint)|Wywoływana w celu odświeżenia części kontenera.|
|[COleControlContainer::OnUIActivate](#onuiactivate)|Wywoływana, gdy formant ma być aktywowany w miejscu.|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Wywoływana, gdy formant zostanie zdezaktywowany.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|Wywoływane przez platformę, gdy komunikaty przewijania są odbierane z okna podrzędnego.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Wysyła komunikat do określonej kontrolki.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Ustawia wartość określonej kontrolki.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Ustawia tekst określonego formantu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|Kolor tła kontenera.|
|[COleControlContainer::m_crFore](#m_crfore)|Kolor pierwszego planu kontenera.|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Lista obsługiwanych lokacji sterowania.|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|Liczba obsługiwanych kontrolek bez okien.|
|[COleControlContainer::m_pOleFont](#m_polefont)|Wskaźnik do czcionki OLE niestandardowej strony kontrolki.|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Wskaźnik do witryny sterowania przechwytywaniem.|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Wskaźnik do kontrolki, która aktualnie ma fokus wprowadzania.|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Wskaźnik do formantu, który jest aktualnie aktywowany w miejscu.|
|[COleControlContainer::m_pWnd](#m_pwnd)|Wskaźnik do okna implementującego kontener sterowania.|
|[COleControlContainer::m_siteMap](#m_sitemap)|Mapa witryny.|

## <a name="remarks"></a>Uwagi

W tym celu należy zapewnić obsługę co najmniej jednej witryny kontrolki ActiveX (zaimplementowane przez `COleControlSite`). `COleControlContainer`w pełni implementuje interfejsy [IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe) i [IOleContainer](/windows/win32/api/oleidl/nn-oleidl-iolecontainer) , dzięki czemu zawarte kontrolki ActiveX mogą spełnić swoje kwalifikacje jako elementy w miejscu.

Często ta klasa jest używana w połączeniu z `COccManager` i `COleControlSite` do implementowania niestandardowego kontenera kontrolek ActiveX z lokacjami niestandardowymi dla co najmniej jednej kontrolki ActiveX.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxocc. h

##  <a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite

Wywoływane przez platformę, aby utworzyć i dołączyć lokację kontroli.

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do `CWnd` obiektu.

*nIDC*<br/>
Identyfikator kontrolki, która ma zostać dołączona.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, jeśli chcesz dostosować ten proces.

> [!NOTE]
>  Użyj pierwszej formy tej funkcji, jeśli łączysz się statycznie z biblioteką MFC. Jeśli łączysz się dynamicznie z biblioteką MFC, użyj drugiej formy.

##  <a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange

Informuje wszystkie formanty hostowane, że Właściwość otoczenia została zmieniona.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*DISPID*<br/>
Identyfikator wysyłania właściwości otoczenia.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przez platformę, gdy właściwość otoczenia zmieniła wartość. Zastąp tę funkcję, aby dostosować to zachowanie.

##  <a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton

Modyfikuje bieżący stan przycisku.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>Parametry

*nIDButton*<br/>
Identyfikator przycisku, który ma zostać zmodyfikowany.

*nSprawdź*<br/>
Określa stan przycisku. Może to być jeden z następujących elementów:

- BST_CHECKED ustawia stan przycisku na wartość zaznaczone.

- BST_INDETERMINATE ustawia stan przycisku na szary, wskazując nieokreślony stan. Użyj tej wartości tylko wtedy, gdy przycisk ma styl BS_3STATE lub BS_AUTO3STATE.

- BST_UNCHECKED ustawia stan przycisku na wyczyszczony.

##  <a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton

Wybiera określony przycisk radiowy w grupie i czyści pozostałe przyciski w grupie.

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>Parametry

*nIDFirstButton*<br/>
Określa identyfikator pierwszego przycisku radiowego w grupie.

*nIDLastButton*<br/>
Określa identyfikator ostatniego przycisku radiowego w grupie.

*nIDCheckButton*<br/>
Określa identyfikator przycisku radiowego, który ma zostać sprawdzony.

##  <a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer

Konstruuje `COleControlContainer` obiekt.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do okna nadrzędnego kontenera kontrolek.

### <a name="remarks"></a>Uwagi

Po pomyślnym utworzeniu obiektu Dodaj niestandardową lokację kontrolną z wywołaniem `AttachControlSite`do.

##  <a name="createcontrol"></a>COleControlContainer:: IsControl

Tworzy kontrolkę ActiveX hostowaną przez określony `COleControlSite` obiekt.

```
BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);

BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);
```

### <a name="parameters"></a>Parametry

*pWndCtrl*<br/>
Wskaźnik do obiektu okna reprezentującego formant.

*Identyfikator*<br/>
Unikatowy identyfikator klasy formantu.

*lpszWindowName*<br/>
Wskaźnik do tekstu, który ma być wyświetlany w kontrolce. Ustawia wartość napisu lub właściwości text kontrolki (jeśli istnieje). Jeśli wartość jest równa NULL, podpis lub właściwość tekstu kontrolki nie zostanie zmieniona.

*dwStyle*<br/>
Style systemu Windows. Dostępne style są wymienione w sekcji **uwagi** .

*cinania*<br/>
Określa rozmiar i położenie kontrolki. Może to być `CRect` obiekt `RECT` lub struktura.

*nID*<br/>
Określa identyfikator okna podrzędnego kontrolki.

*pPersist*<br/>
Wskaźnik do elementu `CFile` zawierającego trwały stan dla kontrolki. Wartość domyślna to NULL, co oznacza, że kontrolka inicjuje się sama bez przywracania stanu z dowolnego trwałego magazynu. Jeśli wartość nie jest równa null, powinna to być `CFile`wskaźnik do obiektu pochodnego, który zawiera trwałe dane kontrolki w postaci strumienia lub magazynu. Te dane mogły zostać zapisane w poprzedniej aktywacji klienta. Może zawierać inne dane, ale musi mieć ustawiony wskaźnik odczytu i zapisu na pierwszy bajt trwałych danych w czasie wywołania do `CreateControl`. `CFile`

*bStorage*<br/>
Wskazuje, czy dane w *pPersist* powinny być interpretowane `IStorage` jako `IStream` czy dane. Jeśli dane w *pPersist* są magazynem, *bStorage* powinna mieć wartość true. Jeśli dane w *pPersist* jest strumieniem, *bStorage* powinna mieć wartość false. Wartość domyślna to FALSE.

*bstrLicKey*<br/>
Opcjonalne dane klucza licencji. Te dane są potrzebne tylko do tworzenia formantów, które wymagają klucza licencji w czasie wykonywania. Jeśli formant obsługuje Licencjonowanie, należy podać klucz licencji, aby można było utworzyć formant. Wartość domyślna to NULL.

*ppNewSite*<br/>
Wskaźnik do istniejącej lokacji kontrolki, która będzie hostować utworzoną kontrolkę. Wartość domyślna to NULL, co oznacza, że nowa witryna kontrolna zostanie automatycznie utworzona i dołączona do nowej kontrolki.

*formacie*<br/>
Wskaźnik do `POINT` struktury zawierającej lewy górny róg kontrolki. Rozmiar kontrolki jest określany na podstawie wartości *psize*. Wartości *PPT* i *psize* są opcjonalną metodą określania rozmiaru i położenia kontrolki.

*psize*<br/>
Wskaźnik do `SIZE` struktury zawierającej rozmiar kontrolki. Lewy górny róg jest określany przez wartość *PPT*. Wartości *PPT* i *psize* są opcjonalną metodą określania rozmiaru i położenia kontrolki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Tylko podzbiór flag *DwStyle* systemu Windows jest obsługiwany przez `CreateControl`:

- WS_VISIBLE tworzy okno, które jest początkowo widoczne. Wymagane, jeśli formant ma być widoczny natychmiast, na przykład w zwykłych oknach.

- WS_DISABLED tworzy okno, które jest początkowo wyłączone. Wyłączone okno nie może odebrać danych wejściowych od użytkownika. Można ustawić, Jeśli kontrolka ma właściwość Enabled.

- WS_BORDER tworzy okno z obramowaniem cienkim. Można ustawić, Jeśli kontrolka ma właściwość BorderStyle.

- WS_GROUP Określa pierwszą kontrolkę grupy kontrolek. Użytkownik może zmienić fokus klawiatury z jednej kontrolki w grupie na następny przy użyciu klawiszy kierunkowych. Wszystkie kontrolki zdefiniowane przy użyciu stylu WS_GROUP po pierwszej kontrolce należy do tej samej grupy. Następna kontrolka ze stylem WS_GROUP zatrzymuje grupę i rozpoczyna następną grupę.

- WS_TABSTOP określa kontrolkę, która może odbierać fokus klawiatury, gdy użytkownik naciśnie klawisz TAB. Naciśnięcie klawisza TAB powoduje zmianę fokusu klawiatury na następną kontrolkę stylu WS_TABSTOP.

Użyj drugiego przeciążenia, aby utworzyć kontrolki o rozmiarze domyślnym.

##  <a name="createolefont"></a>COleControlContainer::CreateOleFont

Tworzy czcionkę OLE.

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Wskaźnik do czcionki, która ma być używana przez kontener sterowania.

##  <a name="finditem"></a>COleControlContainer::FindItem

Znajduje lokację niestandardową, która hostuje określony element.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator elementu, który ma zostać znaleziony.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do niestandardowej witryny określonego elementu.

##  <a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents

Określa, czy kontener będzie ignorować zdarzenia z dołączonych lokacji sterowania, czy je zaakceptować.

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parametry

*bFreeze*<br/>
Niezerowe, jeśli zdarzenia zostaną przetworzone; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Kontrolka nie jest wymagana, aby zatrzymać Wyzwalanie zdarzeń, jeśli są żądane przez kontener sterowania. Może kontynuować proces uruchamiania, ale wszystkie kolejne zdarzenia zostaną zignorowane przez kontener sterowania.

##  <a name="getambientprop"></a>COleControlContainer::GetAmbientProp

Pobiera wartość określonej właściwości otoczenia.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>Parametry

*pSite*<br/>
Wskaźnik do lokacji kontrolki, z której zostanie pobrana Właściwość otoczenia.

*DISPID*<br/>
Identyfikator wysyłki odpowiedniej właściwości otoczenia.

*pVarResult*<br/>
Wskaźnik do wartości właściwości otoczenia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

##  <a name="getdlgitem"></a>COleControlContainer::GetDlgItem

Pobiera wskaźnik do określonego formantu lub okna podrzędnego w oknie dialogowym lub w innym oknie.

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator elementu okna dialogowego do pobrania.

*phWnd*<br/>
Wskaźnik do uchwytu obiektu okna określonego okna dialogowego.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna elementu okna dialogowego.

##  <a name="getdlgitemint"></a>COleControlContainer::GetDlgItemInt

Pobiera wartość przetłumaczonego tekstu danej kontrolki.

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator kontrolki.

*lpTrans*<br/>
Wskaźnik do zmiennej logicznej, która otrzymuje wartość sukcesu lub niepowodzenia funkcji (wartość TRUE oznacza powodzenie, FAŁSZ wskazuje błąd).

*bSigned*<br/>
Określa, czy funkcja powinna przebadać tekst dla znaku minus na początku i zwracać wartość ze znakiem liczby całkowitej, jeśli znajdzie ją. Jeśli parametr *bSigned* ma wartość true, określenie, że wartość, która ma zostać pobrana, jest liczbą całkowitą ze znakiem, Rzutowanie wartości zwracanej na typ **int** . Aby uzyskać rozszerzone informacje o błędzie, wywołaj [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zmienna wskazywana przez *lpTrans* jest ustawiona na wartość true, a wartość zwracana to przetłumaczona wartość tekstu kontrolki.

Jeśli funkcja się nie powiedzie, zmienna wskazywana przez *lpTrans* ma wartość false, a zwracana wartość to zero. Zwróć uwagę, że ponieważ zero jest możliwie przetłumaczonej wartości, wartość zwracana przez zero sama nie wskazuje błędu.

Jeśli *lpTrans* ma wartość null, funkcja nie zwraca informacji o powodzeniu lub niepowodzeniu.

### <a name="remarks"></a>Uwagi

Funkcja tłumaczy pobrany tekst, oddzielając wszelkie dodatkowe spacje na początku tekstu, a następnie konwertując cyfry dziesiętne. Funkcja przerywa translację, gdy dociera do końca tekstu lub napotka znak nienumeryczny.

Ta funkcja zwraca zero, jeśli przetłumaczona wartość jest większa niż INT_MAX (dla cyfr ze znakiem) lub UINT_MAX (dla liczb bez znaku).

##  <a name="getdlgitemtext"></a>COleControlContainer::GetDlgItemText

Pobiera tekst danej kontrolki.

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator kontrolki.

*lpStr*<br/>
Wskaźnik na tekst kontrolki.

*nMaxCount*<br/>
Określa maksymalną długość ciągu, który ma zostać skopiowany do buforu wskazywanym przez *lpStr*. Jeśli długość ciągu przekracza limit, ciąg zostanie obcięty.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana określa liczbę znaków skopiowanych do buforu, bez uwzględnienia kończącego znaku null.

Jeśli funkcja się nie powiedzie, zwracana wartość jest równa zero. Aby uzyskać rozszerzone informacje o błędzie, wywołaj [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

##  <a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus

Określa, czy kontener obsługuje komunikaty WM_SETFOCUS.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli kontener obsługuje komunikaty WM_SETFOCUS; w przeciwnym razie zero.

##  <a name="handlewindowlessmessage"></a>COleControlContainer::HandleWindowlessMessage

Przetwarza komunikaty okna dla kontrolek bez okien.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>Parametry

*komunikat*<br/>
Identyfikator komunikatu okna dostarczonego przez system Windows.

*wParam*<br/>
Parametr komunikatu; zapewniane przez system Windows. Określa dodatkowe informacje dotyczące wiadomości. Zawartość tego parametru zależy od wartości parametru *Message* .

*lParam*<br/>
Parametr komunikatu; zapewniane przez system Windows. Określa dodatkowe informacje dotyczące wiadomości. Zawartość tego parametru zależy od wartości parametru *Message* .

*plResult*<br/>
Kod wyniku systemu Windows. Określa wynik przetwarzania komunikatów i zależy od wysyłanej wiadomości.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby dostosować obsługę komunikatów kontroli bez okien.

##  <a name="isdlgbuttonchecked"></a>COleControlContainer::IsDlgButtonChecked

Określa stan określonego przycisku.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Parametry

*nIDButton*<br/>
Identyfikator kontrolki przycisku.

### <a name="return-value"></a>Wartość zwracana

Wartość zwracana z przycisku utworzonego przy użyciu stylu BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON lub BS_3STATE. Może to być jeden z następujących elementów:

- Przycisk BST_CHECKED jest zaznaczony.

- Przycisk BST_INDETERMINATE jest wyszarzony, wskazując nieokreślony stan (ma zastosowanie tylko wtedy, gdy przycisk ma styl BS_3STATE lub BS_AUTO3STATE).

- Przycisk BST_UNCHECKED został wyczyszczony.

### <a name="remarks"></a>Uwagi

Jeśli przycisk jest formantem z trzema stanami, funkcja członkowska określa, czy jest ona wygaszona, zaznaczona, czy nie.

##  <a name="m_crback"></a>COleControlContainer::m_crBack

Kolor tła kontenera.

```
COLORREF m_crBack;
```

##  <a name="m_crfore"></a>COleControlContainer::m_crFore

Kolor pierwszego planu kontenera.

```
COLORREF m_crFore;
```

##  <a name="m_listsitesorwnds"></a>  COleControlContainer::m_listSitesOrWnds

Lista lokacji formantów hostowanych przez kontener.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

##  <a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls

Liczba kontrolek bez okien hostowanych przez kontener formantów.

```
int m_nWindowlessControls;
```

##  <a name="m_polefont"></a>  COleControlContainer::m_pOleFont

Wskaźnik do czcionki OLE niestandardowej strony kontrolki.

```
LPFONTDISP m_pOleFont;
```

##  <a name="m_psitecapture"></a>  COleControlContainer::m_pSiteCapture

Wskaźnik do witryny sterowania przechwytywaniem.

```
COleControlSite* m_pSiteCapture;
```

##  <a name="m_psitefocus"></a>  COleControlContainer::m_pSiteFocus

Wskaźnik do lokacji kontrolki, która aktualnie ma fokus wprowadzania.

```
COleControlSite* m_pSiteFocus;
```

##  <a name="m_psiteuiactive"></a>  COleControlContainer::m_pSiteUIActive

Wskaźnik do lokacji kontrolki, która jest aktywowana w miejscu.

```
COleControlSite* m_pSiteUIActive;
```

##  <a name="m_pwnd"></a>COleControlContainer::m_pWnd

Wskaźnik do obiektu okna skojarzonego z kontenerem.

```
CWnd* m_pWnd;
```

##  <a name="m_sitemap"></a>COleControlContainer::m_siteMap

Mapa witryny.

```
CMapPtrToPtr m_siteMap;
```

##  <a name="onpaint"></a>COleControlContainer:: OnPaint

Wywoływane przez platformę, by obsługiwać żądania WM_PAINT.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do kontekstu urządzenia używanego przez kontener.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli komunikat został obsłużony; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby dostosować proces malowania.

##  <a name="onuiactivate"></a>COleControlContainer::OnUIActivate

Wywoływane przez platformę, gdy lokacja kontrolna wskazywana przez *pSite*ma zostać aktywowana w miejscu.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parametry

*pSite*<br/>
Wskaźnik do witryny sterowania, który ma zostać aktywowany w miejscu.

### <a name="remarks"></a>Uwagi

Aktywacja w miejscu oznacza, że menu główne kontenera jest zastępowane menu złożonym w miejscu.

##  <a name="onuideactivate"></a>COleControlContainer::OnUIDeactivate

Wywoływane przez platformę, gdy lokacja kontroli, wskazywana przez *pSite*, zostanie zdezaktywowana.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parametry

*pSite*<br/>
Wskaźnik do lokacji sterowania, który ma zostać zdezaktywowany.

### <a name="remarks"></a>Uwagi

Po otrzymaniu tego powiadomienia kontener powinien ponownie zainstalować interfejs użytkownika i zastosować fokus.

##  <a name="scrollchildren"></a>COleControlContainer::ScrollChildren

Wywoływane przez platformę, gdy komunikaty przewijania są odbierane z okna podrzędnego.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Parametry

*dx*<br/>
Ilość, w pikselach, przewijania wzdłuż osi x.

*dy*<br/>
Kwota przewijania wzdłuż osi y (w pikselach).

##  <a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage

Wysyła komunikat do określonej kontrolki.

```
virtual LRESULT SendDlgItemMessage(
    int nID,
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Określa identyfikator formantu, który odbiera komunikat.

*komunikat*<br/>
Określa komunikat do wysłania.

*wParam*<br/>
Określa dodatkowe informacje dotyczące wiadomości.

*lParam*<br/>
Określa dodatkowe informacje dotyczące wiadomości.

##  <a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt

Ustawia tekst kontrolki w oknie dialogowym na ciąg reprezentujący określoną liczbę całkowitą.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator kontrolki.

*nWartość*<br/>
Wartość całkowita, która ma zostać wyświetlona.

*bSigned*<br/>
Określa, czy parametr *nWartość* jest podpisany czy niepodpisany. Jeśli ten parametr ma wartość TRUE, *nWartość* jest podpisana. Jeśli ten parametr ma wartość TRUE, a *nWartość* jest mniejsza od zera, znak minus jest umieszczany przed pierwszą cyfrą w ciągu. Jeśli ten parametr ma wartość FALSE, *nWartość* jest niepodpisany.

##  <a name="setdlgitemtext"></a>  COleControlContainer::SetDlgItemText

Ustawia tekst określonego formantu przy użyciu tekstu zawartego w *lpszString*.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator kontrolki.

*lpszString*<br/>
Wskaźnik na tekst kontrolki.

## <a name="see-also"></a>Zobacz także

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleControlSite](../../mfc/reference/colecontrolsite-class.md)<br/>
[Klasa COccManager](../../mfc/reference/coccmanager-class.md)
