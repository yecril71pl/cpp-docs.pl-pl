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
ms.openlocfilehash: 6e97f7ceafb92098d701cba64b4ec01d26d3991a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274989"
---
# <a name="colecontrolcontainer-class"></a>Klasa COleControlContainer

Działa jako kontener formantu dla formantów ActiveX.

## <a name="syntax"></a>Składnia

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|Konstruuje `COleControlContainer` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Tworzy witrynę kontroli, hostowane przez kontener.|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informuje o wszystkich hostowanych formantów, które zmieniono właściwość została zmieniona.|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Modyfikuje kontroli określonego przycisku.|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Wybór przycisku radiowego określonej grupy.|
|[COleControlContainer::CreateControl](#createcontrol)|Tworzy formant ActiveX hostowanej.|
|[COleControlContainer::CreateOleFont](#createolefont)|Tworzy czcionkę OLE.|
|[COleControlContainer::FindItem](#finditem)|Zwraca niestandardowe witryny określoną kontrolkę.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Określa, jeśli witryna kontroli akceptuje zdarzenia.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|Pobiera określoną właściwość otoczenia.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|Pobiera formant określonego okna dialogowego.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Pobiera wartość określonego okna dialogowego formantu.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Pobiera Podpis formantu określonego okna dialogowego.|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Określa, jeśli kontener obsługuje WM_SETFOCUS wiadomości.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Obsługuje komunikaty wysyłane do formantu bez okien.|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Określa stan określonego przycisku.|
|[COleControlContainer::OnPaint](#onpaint)|Wywoływane w celu odświeżenia częścią kontenera.|
|[COleControlContainer::OnUIActivate](#onuiactivate)|Wywołuje się, gdy formant ma być aktywowany w miejscu.|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Wywołuje się, gdy kontrolka zostanie zdezaktywowane.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|Wywoływane przez platformę, gdy przewijania komunikaty są odbierane z okna podrzędnego.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Wysyła komunikat do określonej kontrolki.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Ustawia wartość określonego formantu.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Ustawia tekst określoną kontrolkę.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|Kolor tła kontenera.|
|[COleControlContainer::m_crFore](#m_crfore)|Kolor pierwszego planu kontenera.|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Lista witryn obsługiwanych kontroli.|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|Liczba hostowanych kontrolek bez okien.|
|[COleControlContainer::m_pOleFont](#m_polefont)|Wskaźnik do czcionki OLE witryny kontrolki niestandardowej.|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Wskaźnik do przechwytywania kontroli lokacji.|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Wskaźnik do formantu, który aktualnie ma fokus wejścia.|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Wskaźnik do kontrolki, która obecnie jest aktywowany w miejscu.|
|[COleControlContainer::m_pWnd](#m_pwnd)|Wskaźnik do okna wykonania kontener formantu.|
|[COleControlContainer::m_siteMap](#m_sitemap)|Mapa witryny.|

## <a name="remarks"></a>Uwagi

Jest to realizowane przez zapewnienie obsługi dla co najmniej jedną lokację kontrolki ActiveX (implementowany przez `COleControlSite`). `COleControlContainer` w pełni zaimplementowano [IOleInPlaceFrame](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceframe) i [IOleContainer](/windows/desktop/api/oleidl/nn-oleidl-iolecontainer) interfejsów, dzięki czemu zawartych w nim formantów ActiveX do zrealizowania ich kwalifikacji jako elementy w miejscu.

Zazwyczaj ta klasa jest używana w połączeniu z `COccManager` i `COleControlSite` do zaimplementowania niestandardowego kontenera kontrolki ActiveX, za pomocą niestandardowych witryn dla co najmniej jedną kontrolkę ActiveX.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxocc.h

##  <a name="attachcontrolsite"></a>  COleControlContainer::AttachControlSite

Metoda wywoływana przez platformę, by utworzyć i dołączyć kontroli lokacji.

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
Identyfikator formantu do podłączenia.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, jeśli chcesz dostosować ten proces.

> [!NOTE]
>  Pierwszy formularz tej funkcji należy używać statycznie łącze do biblioteki MFC. Drugi formularz dynamiczne łącze do biblioteki MFC.

##  <a name="broadcastambientpropertychange"></a>  COleControlContainer::BroadcastAmbientPropertyChange

Informuje o wszystkich hostowanych formantów, które zmieniono właściwość została zmieniona.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*dispid*<br/>
Identyfikator wysyłania są zmiany właściwości otoczenia.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przez platformę, gdy zmieniono właściwość została zmieniona wartość. Należy przesłonić tę funkcję, aby dostosować to zachowanie.

##  <a name="checkdlgbutton"></a>  COleControlContainer::CheckDlgButton

Modyfikuje bieżący stan przycisku.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>Parametry

*nIDButton*<br/>
Identyfikator przycisku, który ma zostać zmodyfikowana.

*nCheck*<br/>
Określa stan przycisku. Może to być jeden z następujących elementów:

- Ustawia BST_CHECKED przycisku stan zaznaczone.

- BST_INDETERMINATE ustawia stan przycisku na wyszarzony, wskazując dla niego stan nieokreślony. Użyj tej wartości, tylko wtedy, gdy przycisk BS_3STATE lub BS_AUTO3STATE stylu.

- Ustawia BST_UNCHECKED przycisku stan wyczyszczone.

##  <a name="checkradiobutton"></a>  COleControlContainer::CheckRadioButton

Wybranie przycisku radiowego określony w grupie i czyści pozostałe przyciski w grupie.

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
Określa identyfikator przycisku radiowego, który ma być sprawdzany.

##  <a name="colecontrolcontainer"></a>  COleControlContainer::COleControlContainer

Konstruuje `COleControlContainer` obiektu.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do okna nadrzędnego kontenera kontrolki.

### <a name="remarks"></a>Uwagi

Po pomyślnym utworzeniu obiektu dodać lokację kontrolkę niestandardową przy użyciu wywołania do `AttachControlSite`.

##  <a name="createcontrol"></a>  COleControlContainer::CreateControl

Tworzy formant ActiveX, hostowane przez określony `COleControlSite` obiektu.

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
Wskaźnik do obiektu okna, reprezentujący formantu.

*Identyfikator klasy*<br/>
Identyfikator unikatowy klasy kontrolki.

*lpszWindowName*<br/>
Wskaźnik na tekst, który ma być wyświetlany w formancie. Ustawia wartość właściwości podpisu lub tekst kontrolki (jeśli istnieje). Jeśli ma wartość NULL, właściwości podpisu lub tekstu formantu nie jest zmieniany.

*dwStyle*<br/>
Style Windows. Dostępne style są wyświetlane w obszarze **uwagi** sekcji.

*Rect*<br/>
Określa rozmiar i położenie formantu. Może być albo `CRect` obiektu lub `RECT` struktury.

*nID*<br/>
Określa identyfikator. okno podrzędne kontrolki

*pPersist*<br/>
Wskaźnik do `CFile` zawierający trwały stan dla formantu. Wartość domyślna to NULL, wskazujący, że kontrolka inicjalizuje bez przywracania stanu z dowolnego magazynu trwałego. Jeśli nie ma wartość NULL, powinna to być wskaźnik do `CFile`-pochodzi obiekt, który zawiera trwałych danych formantu w formie strumienia lub magazynu. Można te dane zostały zapisane w poprzednim aktywacji klienta. `CFile` Może zawierać innych danych, ale musi mieć swojego wskaźnika odczytu i zapisu, ustaw do pierwszego bajtu trwałych danych w czasie wywołania `CreateControl`.

*bStorage*<br/>
Wskazuje, czy dane w *pPersist* powinno być interpretowane jako `IStorage` lub `IStream` danych. Jeśli dane w *pPersist* magazynu *bStorage* powinien mieć wartość PRAWDA. Jeśli dane w *pPersist* jest strumieniem, *bStorage* powinna być równa FALSE. Wartość domyślna to FALSE.

*bstrLicKey*<br/>
Opcjonalne dane klucza licencji. Tych danych jest konieczne tylko w przypadku tworzenia formantów, które wymagają klucz licencji środowiska wykonawczego. Jeśli są obsługiwane przez kontrolkę licencjonowania, musisz podać klucz licencji do tworzenia kontrolki została wykonana pomyślnie. Wartością domyślną jest NULL.

*ppNewSite*<br/>
Wskaźnik do istniejącej lokacji formant, który będzie obsługiwać formant tworzony. Wartość domyślna to NULL, wskazującą, czy nowej lokacji sterowania zostanie automatycznie utworzone i dołączone do nowego formantu.

*ppt*<br/>
Wskaźnik do `POINT` strukturę, która zawiera lewego górnego rogu kontrolki. Rozmiar kontrolki jest określany przez wartość *psize*. *Ppt* i *psize* wartości są opcjonalne metodę określania rozmiaru i położenia kontrolki.

*psize*<br/>
Wskaźnik do `SIZE` strukturę, która zawiera rozmiar formantu. Lewy górny róg jest określana przez wartość *ppt*. *Ppt* i *psize* wartości są opcjonalne metodę określania rozmiaru i położenia kontrolki.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Tylko podzbiór Windows *dwStyle* flagi są obsługiwane przez `CreateControl`:

- WS_VISIBLE tworzy okno, które jest początkowo widoczne. Wymagane, jeśli formant aby były widoczne natychmiast, takich jak zwykłe systemu windows.

- WS_DISABLED tworzy okno, które jest początkowo wyłączone. Wyłączone okno nie może odbierać dane wejściowe od użytkownika. Można ustawić, jeśli kontrolka ma właściwość Enabled.

- WS_BORDER tworzy okno z obramowaniem alokowanych wiersza. Można ustawić, jeśli kontrolka ma właściwości BorderStyle.

- WS_GROUP Określa pierwszy formant grupy formantów. Użytkownik może zmienić fokus klawiatury w jeden formant w grupie do następnego przy użyciu kluczy kierunku. Wszystkie formanty zdefiniowane przy użyciu stylu WS_GROUP po pierwszej kontroli należą do tej samej grupy. Następny formant ze stylem WS_GROUP kończy grupy i rozpoczyna następną grupę.

- WS_TABSTOP Określa formant, który może odebrać fokus klawiatury, gdy użytkownik naciśnie klawisz TAB. Naciskając klawisz TAB, zmienia się na następnej kontrolki stylu WS_TABSTOP fokus klawiatury.

Drugie przeciążenie umożliwia tworzenie formantów o rozmiarze domyślnym.

##  <a name="createolefont"></a>  COleControlContainer::CreateOleFont

Tworzy czcionkę OLE.

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Wskaźnik do czcionki do użycia przez kontener formantu.

##  <a name="finditem"></a>  COleControlContainer::FindItem

Umożliwia znalezienie niestandardowej witryny, który jest hostem określonego elementu.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator elementu, który ma zostać odnaleziona.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do niestandardowej witryny określonego elementu.

##  <a name="freezeallevents"></a>  COleControlContainer::FreezeAllEvents

Określa kontener będzie ignorować zdarzenia z witrynami kontrolek dołączonych czy je zaakceptować.

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parametry

*bFreeze*<br/>
Wartość różną od zera, jeśli będzie można przetworzyć zdarzeń; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Kontrolka nie jest wymagane przestanie wyzwalanie zdarzeń, jeśli jest to wymagane przez kontener formantu. Może kontynuować uruchomieniu którego, ale wszystkie kolejne zdarzenia zostaną zignorowane przez kontener formantu.

##  <a name="getambientprop"></a>  COleControlContainer::GetAmbientProp

Pobiera wartość określonej właściwości otoczenia.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>Parametry

*pSite*<br/>
Wskaźnik do lokacji kontroli, z którego będą pobierane właściwości otoczenia.

*dispid*<br/>
Identyfikator alokacji żądanej właściwości otoczenia.

*pVarResult*<br/>
Wskaźnik do wartości właściwości otoczenia.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

##  <a name="getdlgitem"></a>  COleControlContainer::GetDlgItem

Pobiera wskaźnik do określonej kontrolki podrzędne okna lub w oknie dialogowym lub inne okna.

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
Wskaźnik do uchwytu obiekt okna elementu określonego okna dialogowego.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu okna dialogowego okna.

##  <a name="getdlgitemint"></a>  COleControlContainer::GetDlgItemInt

Pobiera wartość zawierające przetłumaczony tekst danej kontrolki.

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
Wskaźnik do zmiennej typu Boolean, który otrzymuje wartość Powodzenie/niepowodzenie — funkcja (wartość TRUE oznacza sukces, wartość FALSE wskazuje niepowodzenie).

*bSigned*<br/>
Określa, czy funkcja należy zbadać tekst znak minus na początku i zwraca wartość liczby całkowitej ze znakiem, jeśli zostanie znaleziony. Jeśli *bSigned* parametr ma wartość PRAWDA, określając, że wartości do pobrania jest wartością liczby całkowitej ze znakiem, wykonaj rzutowanie zwracanej wartości **int** typu. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja się powiedzie, zmienna wskazywany przez *lpTrans* jest ustawiona na wartość TRUE, i wartość zwracana jest wartość przetłumaczonego tekstu kontrolki.

Jeśli funkcja zawiedzie, zmienna wskazywany przez *lpTrans* jest ustawiona na wartość FALSE, a wartość zwracana wynosi zero. Wskazują, ponieważ zero jest możliwa wartość tłumaczenia, zwracana wartość wynosząca zero nie samodzielnie awarii.

Jeśli *lpTrans* ma wartość NULL, funkcja zwraca żadne informacje o powodzeniu lub niepowodzeniu.

### <a name="remarks"></a>Uwagi

Funkcja tłumaczy tekst pobrane przez obcięcie dodatkowe spacje na początku tekstu, a następnie konwertując cyfr dziesiętnych. Funkcja przestaje tłumaczenia, gdy osiągnie koniec tekstu lub napotka liczbą znaków.

Ta funkcja zwraca zero, jeśli przetłumaczone wartość jest większa niż INT_MAX (w przypadku liczb ze znakiem) lub UINT_MAX (w przypadku liczb bez znaku).

##  <a name="getdlgitemtext"></a>  COleControlContainer::GetDlgItemText

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
Wskaźnik do tekstu kontrolki.

*nMaxCount*<br/>
Określa maksymalną długość w znakach ciągu, które mają być kopiowane do bufor wskazywany przez *lpStr*. Jeśli długość ciągu przekracza limit, ciąg został obcięty.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana określa liczbę znaków skopiowane do buforu, nie wliczając kończącego znaku null.

Jeśli funkcja zawiedzie, wartość zwracana wynosi zero. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

##  <a name="handlesetfocus"></a>  COleControlContainer::HandleSetFocus

Określa, jeśli kontener obsługuje WM_SETFOCUS wiadomości.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli kontener obsługuje WM_SETFOCUS wiadomości. w przeciwnym razie wartość zero.

##  <a name="handlewindowlessmessage"></a>  COleControlContainer::HandleWindowlessMessage

Przetwarza komunikaty okna od kontrolek bez okien.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>Parametry

*komunikat*<br/>
Identyfikator dla komunikatów okien, dostarczonych przez Windows.

*wParam*<br/>
Parametr message; udostępniane przez Windows. Określa dodatkowe informacje specyficzne dla wiadomości. Zawartość tego parametru zależy od wartości *komunikat* parametru.

*lParam*<br/>
Parametr message; udostępniane przez Windows. Określa dodatkowe informacje specyficzne dla wiadomości. Zawartość tego parametru zależy od wartości *komunikat* parametru.

*plResult*<br/>
Kod wyniku Windows. Określa wyniku przetwarzania komunikatów i zależy od wiadomość została wysłana.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby dostosować obsługi komunikatów sterujących bez okien.

##  <a name="isdlgbuttonchecked"></a>  COleControlContainer::IsDlgButtonChecked

Określa stan określonego przycisku.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Parametry

*nIDButton*<br/>
Identyfikator formantu przycisku.

### <a name="return-value"></a>Wartość zwracana

Wartość zwracana z utworzonej przy użyciu stylu BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE BS_CHECKBOX, BS_RADIOBUTTON lub BS_3STATE przycisku. Może to być jeden z następujących elementów:

- BST_CHECKED przycisk jest sprawdzane.

- Przycisk BST_INDETERMINATE jest niedostępna, wskazując dla niego stan nieokreślony (ma zastosowanie tylko wtedy, gdy przycisk stylu BS_3STATE lub BS_AUTO3STATE).

- Przycisk BST_UNCHECKED jest wyczyszczone.

### <a name="remarks"></a>Uwagi

Jeśli przycisk znajduje się kontrolka trójstanowych, funkcja elementu członkowskiego Określa, czy go jest wygaszone, zaznaczone, lub ani.

##  <a name="m_crback"></a>  COleControlContainer::m_crBack

Kolor tła kontenera.

```
COLORREF m_crBack;
```

##  <a name="m_crfore"></a>  COleControlContainer::m_crFore

Kolor pierwszego planu kontenera.

```
COLORREF m_crFore;
```

##  <a name="m_listsitesorwnds"></a>  COleControlContainer::m_listSitesOrWnds

Lista witrynami kontrolek obsługiwanych przez kontener.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

##  <a name="m_nwindowlesscontrols"></a>  COleControlContainer::m_nWindowlessControls

Liczba hostowanych przez kontener formantu od kontrolek bez okien.

```
int m_nWindowlessControls;
```

##  <a name="m_polefont"></a>  COleControlContainer::m_pOleFont

Wskaźnik do czcionki OLE witryny kontrolki niestandardowej.

```
LPFONTDISP m_pOleFont;
```

##  <a name="m_psitecapture"></a>  COleControlContainer::m_pSiteCapture

Wskaźnik do przechwytywania kontroli lokacji.

```
COleControlSite* m_pSiteCapture;
```

##  <a name="m_psitefocus"></a>  COleControlContainer::m_pSiteFocus

Wskaźnik do sterowania lokacji, który aktualnie ma fokus wejścia.

```
COleControlSite* m_pSiteFocus;
```

##  <a name="m_psiteuiactive"></a>  COleControlContainer::m_pSiteUIActive

Wskaźnik do sterowania lokacji, który jest aktywowany w miejscu.

```
COleControlSite* m_pSiteUIActive;
```

##  <a name="m_pwnd"></a>  COleControlContainer::m_pWnd

Wskaźnik do obiektu okna skojarzonych z danym kontenerem.

```
CWnd* m_pWnd;
```

##  <a name="m_sitemap"></a>  COleControlContainer::m_siteMap

Mapa witryny.

```
CMapPtrToPtr m_siteMap;
```

##  <a name="onpaint"></a>  COleControlContainer::OnPaint

Metoda wywoływana przez platformę, by obsłużyć żądań WM_PAINT.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do kontekstu urządzenia używane przez kontener.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli komunikat został obsłużony; w przeciwnym razie wartość zero.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby dostosować proces rysowania.

##  <a name="onuiactivate"></a>  COleControlContainer::OnUIActivate

Wywoływane przez platformę, gdy witrynie formant wskazywany przez *pSite*, ma być aktywowany w miejscu.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parametry

*pSite*<br/>
Wskaźnik do sterowania lokacji zostanie aktywowany w miejscu.

### <a name="remarks"></a>Uwagi

Aktywacja w miejscu oznacza, że menu głównego kontenera jest zastępowany złożonego menu w miejscu.

##  <a name="onuideactivate"></a>  COleControlContainer::OnUIDeactivate

Wywoływane przez platformę, gdy witrynie formant wskazywany przez *pSite*, wkrótce zdezaktywowane.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parametry

*pSite*<br/>
Wskaźnik do sterowania lokacji o zdezaktywowane.

### <a name="remarks"></a>Uwagi

Po odebraniu tego powiadomienia kontenera należy ponownie zainstalować interfejs użytkownika i przyjąć fokusu.

##  <a name="scrollchildren"></a>  COleControlContainer::ScrollChildren

Wywoływane przez platformę, gdy przewijania komunikaty są odbierane z okna podrzędnego.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Parametry

*dx*<br/>
Wielkość, w pikselach, przewijania wzdłuż osi x.

*dy*<br/>
Wielkość, w pikselach, przewijania wzdłuż osi y.

##  <a name="senddlgitemmessage"></a>  COleControlContainer::SendDlgItemMessage

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
Określa identyfikator kontrolki, która odbiera komunikaty.

*komunikat*<br/>
Określa komunikat do wysłania.

*wParam*<br/>
Określa dodatkowe informacje specyficzne dla wiadomości.

*lParam*<br/>
Określa dodatkowe informacje specyficzne dla wiadomości.

##  <a name="setdlgitemint"></a>  COleControlContainer::SetDlgItemInt

Ustawia tekst kontrolki w oknie dialogowym do reprezentacji ciągu określonej liczby całkowitej.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator kontrolki.

*nWartość:*<br/>
Wartość całkowita, która ma być wyświetlany.

*bSigned*<br/>
Określa, czy *nWartość* parametru jest podpisane lub niepodpisane. Jeśli ten parametr ma wartość TRUE, *nWartość* jest podpisany. Jeśli ten parametr ma wartość TRUE i *nWartość* jest mniejsza niż zero, minus znak jest umieszczony przed pierwszym cyfrą w ciągu. Jeśli ten parametr ma wartość FALSE, *nWartość* jest niepodpisany.

##  <a name="setdlgitemtext"></a>  COleControlContainer::SetDlgItemText

Ustawia tekst kontrolki określonej za pomocą tekst zawarty w *lpszString*.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator kontrolki.

*lpszString*<br/>
Wskaźnik do tekstu kontrolki.

## <a name="see-also"></a>Zobacz także

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleControlSite](../../mfc/reference/colecontrolsite-class.md)<br/>
[Klasa COccManager](../../mfc/reference/coccmanager-class.md)
