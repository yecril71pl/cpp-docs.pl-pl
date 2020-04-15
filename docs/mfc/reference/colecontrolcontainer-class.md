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
ms.openlocfilehash: b1737b2ac114181a4245fff027b756ca30b64129
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366186"
---
# <a name="colecontrolcontainer-class"></a>Klasa COleControlContainer

Działa jako kontener formantu activex.

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
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Tworzy witrynę formantu, hostowane przez kontener.|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informuje wszystkie hostowane formanty, że właściwość otoczenia została zmieniona.|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Modyfikuje określony przycisk.|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Wybiera określony przycisk opcji grupy.|
|[COleControlContainer::CreateControl](#createcontrol)|Tworzy hostowany formant ActiveX.|
|[COleControlContainer::CreateOleFont](#createolefont)|Tworzy czcionkę OLE.|
|[COleControlContainer::FindItem](#finditem)|Zwraca niestandardową lokację określonego formantu.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Określa, czy witryna kontrolna akceptuje zdarzenia.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|Pobiera określoną właściwość otoczenia.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|Pobiera określony formant okna dialogowego.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Pobiera wartość określonego formantu okna dialogowego.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Pobiera podpis określonego formantu okna dialogowego.|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Określa, czy kontener obsługuje WM_SETFOCUS wiadomości.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Obsługuje wiadomości wysyłane do formantu bez okien.|
|[COleControlContainer::IsDlgButtonSprawdziony](#isdlgbuttonchecked)|Określa stan określonego przycisku.|
|[COleControlContainer::OnPaint](#onpaint)|Wywołany, aby przemalować część kontenera.|
|[COleControlContainer::OnUIActivate](#onuiactivate)|Wywoływana, gdy formant ma być aktywowany w miejscu.|
|[COleControlContainer::OnUIDeaktywacji](#onuideactivate)|Wywoływana, gdy formant ma zostać dezaktywowany.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|Wywoływane przez strukturę, gdy wiadomości przewijania są odbierane z okna podrzędnego.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Wysyła wiadomość do określonego formantu.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Ustawia wartość określonego formantu.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Ustawia tekst określonego formantu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|Kolor tła kontenera.|
|[COleControlContainer::m_crFore](#m_crfore)|Kolor pierwszego planu kontenera.|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Lista obsługiwanych witryn kontrolnych.|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|Liczba hostowanych formantów bez okien.|
|[COleControlContainer::m_pOleFont](#m_polefont)|Wskaźnik do czcionki OLE w witrynie formantu niestandardowego.|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Wskaźnik do witryny kontroli przechwytywania.|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Wskaźnik do formantu, który obecnie ma fokus wejściowy.|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Wskaźnik do formantu, który jest obecnie w miejscu aktywowane.|
|[COleControlContainer::m_pWnd](#m_pwnd)|Wskaźnik do okna implementując kontener formantu.|
|[COleControlContainer::m_siteMap](#m_sitemap)|Mapa witryny.|

## <a name="remarks"></a>Uwagi

Odbywa się to poprzez zapewnienie wsparcia dla jednej lub `COleControlSite`więcej witryn kontrolnych ActiveX (zaimplementowanych przez ). `COleControlContainer`w pełni implementuje interfejsy [IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe) i [IOleContainer,](/windows/win32/api/oleidl/nn-oleidl-iolecontainer) umożliwiając zawartym formantom ActiveX spełnienie ich kwalifikacji jako elementów w miejscu.

Zazwyczaj ta klasa jest używana `COccManager` w `COleControlSite` połączeniu z i do zaimplementowania niestandardowego kontenera formantu ActiveX, z witryn niestandardowych dla jednego lub więcej formantów ActiveX.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxocc.h

## <a name="colecontrolcontainerattachcontrolsite"></a><a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite

Wywoływana przez strukturę do tworzenia i dołączania witryny kontrolnej.

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do `CWnd` obiektu.

*nIDC (nIDC)*<br/>
Identyfikator formantu, który ma być dołączony.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji należy zastądić, jeśli chcesz dostosować ten proces.

> [!NOTE]
> Użyj pierwszej formy tej funkcji, jeśli statycznie łączysz się z biblioteką MFC. Użyj drugiego formularza, jeśli dynamicznie łączysz się z biblioteką MFC.

## <a name="colecontrolcontainerbroadcastambientpropertychange"></a><a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange

Informuje wszystkie hostowane formanty, że właściwość otoczenia została zmieniona.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
Identyfikator wysyłki właściwości otoczenia, która jest zmieniana.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przez platformę, gdy właściwość otoczenia została zmieniona wartość. Zastąd w tej funkcji należy dostosować tę funkcję.

## <a name="colecontrolcontainercheckdlgbutton"></a><a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton

Modyfikuje bieżący stan przycisku.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>Parametry

*nIDButton (przycisk NID)*<br/>
Identyfikator przycisku, który ma zostać zmodyfikowany.

*nSprawda*<br/>
Określa stan przycisku. Może być jedną z następujących czynności:

- BST_CHECKED Ustawia stan przycisku do sprawdzenia.

- BST_INDETERMINATE Ustawia stan przycisku na wyszarzony, wskazując stan nieokreślony. Tej wartości należy używać tylko wtedy, gdy przycisk ma styl BS_3STATE lub BS_AUTO3STATE.

- BST_UNCHECKED Ustawia stan przycisku na wyczyszczone.

## <a name="colecontrolcontainercheckradiobutton"></a><a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton

Wybiera określony przycisk opcji w grupie i czyści pozostałe przyciski w grupie.

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>Parametry

*nIDFirstButton*<br/>
Określa identyfikator pierwszego przycisku radiowego w grupie.

*nIDLastButton (Przycisk nIDLastButton)*<br/>
Określa identyfikator ostatniego przycisku radiowego w grupie.

*nIDCheckButton (Przycisk kontroli nIDCheck)*<br/>
Określa identyfikator zaznaczonego przycisku opcji.

## <a name="colecontrolcontainercolecontrolcontainer"></a><a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer

Konstruuje `COleControlContainer` obiekt.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do okna nadrzędnego kontenera formantu.

### <a name="remarks"></a>Uwagi

Po pomyślnym utworzeniu obiektu dodaj niestandardową witrynę `AttachControlSite`kontrolną z wywołaniem .

## <a name="colecontrolcontainercreatecontrol"></a><a name="createcontrol"></a>COleControlContainer::CreateControl

Tworzy formant ActiveX, obsługiwany `COleControlSite` przez określony obiekt.

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

*pWndCtrl (właśc.*<br/>
Wskaźnik do obiektu okna reprezentującego formant.

*Clsid*<br/>
Unikatowy identyfikator klasy formantu.

*lpszWindowName*<br/>
Wskaźnik do tekstu, który ma być wyświetlany w formancie. Ustawia wartość formantu Caption lub Text właściwości (jeśli istnieje). Jeśli NULL, podpis formantu lub text właściwość nie zostanie zmieniona.

*Dwstyle*<br/>
Style systemu Windows. Dostępne style są wymienione w sekcji **Uwagi.**

*Rect*<br/>
Określa rozmiar i położenie formantu. Może to być `CRect` obiekt lub `RECT` struktura.

*Nid*<br/>
Określa identyfikator okna podrzędnego formantu.

*pPersist*<br/>
Wskaźnik do `CFile` zawierającego stan trwały dla formantu. Wartością domyślną jest NULL, co oznacza, że formant inicjuje się bez przywracania jego stanu z dowolnego magazynu trwałego. Jeśli nie NULL, powinien być `CFile`wskaźnikiem do obiektu pochodnego, który zawiera trwałe dane formantu, w postaci strumienia lub magazynu. Te dane mogły zostać zapisane podczas poprzedniej aktywacji klienta. Może `CFile` zawierać inne dane, ale musi mieć ustawiony wskaźnik odczytu i zapisu na pierwszy `CreateControl`bajt danych trwałych w czasie wywołania .

*bSporównania*<br/>
Wskazuje, czy dane w *pPersist* powinny `IStorage` `IStream` być interpretowane jako lub danych. Jeśli dane w *pPersist* jest magazyn, *bSprzeczynienie* powinno być prawda. Jeśli dane w *pPersist* jest strumień, *bSprzeczynienie* powinno być FALSE. Wartością domyślną jest FAŁSZ.

*klawisz bstrLicKey*<br/>
Opcjonalne dane klucza licencyjnego. Te dane są potrzebne tylko do tworzenia formantów, które wymagają klucza licencji w czasie wykonywania. Jeśli formant obsługuje licencjonowanie, należy podać klucz licencji do tworzenia formantu, aby zakończyć się pomyślnie. Wartością domyślną jest NULL.

*ppNewWitła*<br/>
Wskaźnik do istniejącej lokacji kontrolnej, która będzie obsługiwać formant tworzony. Wartością domyślną jest NULL, co oznacza, że nowa lokacja formantu zostanie automatycznie utworzona i dołączona do nowego formantu.

*Ppt*<br/>
Wskaźnik do `POINT` struktury, która zawiera lewy górny róg formantu. Wielkość formantu zależy od wartości *psize*. Wartości *ppt* i *psize* są opcjonalną metodą określania rozmiaru i położenia formantu.

*psize (psize)*<br/>
Wskaźnik do `SIZE` struktury, która zawiera rozmiar formantu. Lewy górny róg jest określany przez wartość *ppt*. Wartości *ppt* i *psize* są opcjonalną metodą określania rozmiaru i położenia formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Tylko podzbiór flag systemu Windows *dwStyle* są obsługiwane przez: `CreateControl`

- WS_VISIBLE Tworzy okno, które jest początkowo widoczne. Wymagane, jeśli chcesz, aby formant był widoczny natychmiast, jak zwykłe okna.

- WS_DISABLED Tworzy okno, które jest początkowo wyłączone. Wyłączone okno nie może odbierać danych wejściowych od użytkownika. Można ustawić, jeśli formant ma Enabled właściwości.

- WS_BORDER Tworzy okno z cienką linią obramowania. Można ustawić, jeśli formant ma BorderStyle właściwości.

- WS_GROUP Określa pierwszą kontrolę grupy formantów. Użytkownik może zmienić fokus klawiatury z jednego formantu w grupie do następnego za pomocą klawiszy kierunku. Wszystkie formanty zdefiniowane za pomocą stylu WS_GROUP po pierwszym formancie należą do tej samej grupy. Następny formant ze stylem WS_GROUP kończy grupę i rozpoczyna następną grupę.

- WS_TABSTOP Określa formant, który może odbierać fokus klawiatury, gdy użytkownik naciśnie klawisz TAB. Naciśnięcie klawisza TAB powoduje zmianę fokusu klawiatury na następną kontrolkę stylu WS_TABSTOP.

Użyj drugiego przeciążenia, aby utworzyć domyślne formanty o rozmiarze.

## <a name="colecontrolcontainercreateolefont"></a><a name="createolefont"></a>COleControlContainer::CreateOleFont

Tworzy czcionkę OLE.

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont (pFont)*<br/>
Wskaźnik do czcionki, która ma być używana przez kontener formantu.

## <a name="colecontrolcontainerfinditem"></a><a name="finditem"></a>COleControlContainer::FindItem

Znajduje witrynę niestandardową, która obsługuje określony element.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identyfikator elementu, który należy znaleźć.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do witryny niestandardowej określonego elementu.

## <a name="colecontrolcontainerfreezeallevents"></a><a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents

Określa, czy kontener będzie ignorować zdarzenia z dołączonych witryn kontrolnych lub je zaakceptować.

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parametry

*bZamk.*<br/>
Nonzero, jeśli zdarzenia będą przetwarzane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Formant nie jest wymagane, aby zatrzymać zdarzenia wypalania, jeśli jest to wymagane przez kontener kontrolny. Może kontynuować wypalanie, ale wszystkie kolejne zdarzenia zostaną zignorowane przez kontener kontrolny.

## <a name="colecontrolcontainergetambientprop"></a><a name="getambientprop"></a>COleControlContainer::GetAmbientProp

Pobiera wartość określonej właściwości otoczenia.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>Parametry

*pWitła*<br/>
Wskaźnik do witryny kontrolnej, z której zostanie pobrana właściwość otoczenia.

*Dispid*<br/>
Identyfikator wysyłki żądanej właściwości otoczenia.

*pVarResult (Niesienie wyników)*<br/>
Wskaźnik do wartości właściwości otoczenia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

## <a name="colecontrolcontainergetdlgitem"></a><a name="getdlgitem"></a>COleControlContainer::GetDlgItem

Pobiera wskaźnik do określonego formantu lub okna podrzędnego w oknie dialogowym lub innym oknie.

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identyfikator elementu okna dialogowego do pobrania.

*phWnd (właśc.*<br/>
Wskaźnik do uchwytu obiektu okna określonego elementu okna okna.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna elementu okna dialogowego.

## <a name="colecontrolcontainergetdlgitemint"></a><a name="getdlgitemint"></a>COleControlContainer::GetDlgItemInt

Pobiera wartość przetłumaczonego tekstu danego formantu.

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identyfikator formantu.

*lpTrans (lpTrans)*<br/>
Wskaźnik do zmiennej logicznej, która otrzymuje wartość sukcesu/niepowodzenia funkcji (WARTOŚĆ TRUE wskazuje sukces, FALSE wskazuje niepowodzenie).

*bPodpisany*<br/>
Określa, czy funkcja powinna zbadać tekst dla znaku minus na początku i zwrócić podpisaną wartość całkowitą, jeśli ją znajdzie. Jeśli *parametrem bSigned* jest PRAWDA, określając, że wartość do pobrania jest podpisaną wartością całkowitą, należy rzutować wartość zwracaną na typ **int.** Aby uzyskać rozszerzone informacje o błędzie, zadzwoń [do GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zmienna wskazywała przez *lpTrans* jest ustawiona na WARTOŚĆ TRUE, a zwracana wartość jest przetłumaczoną wartością tekstu kontrolnego.

Jeśli funkcja nie powiedzie się, zmienna wskazywała przez *lpTrans* jest ustawiona na FAŁSZ, a zwracana wartość wynosi zero. Należy zauważyć, że ponieważ zero jest możliwą wartością przetłumaczoną, zwracana wartość zero sama w sobie nie oznacza błędu.

Jeśli *lpTrans* ma wartość NULL, funkcja zwraca żadnych informacji o sukcesie lub niepowodzeniu.

### <a name="remarks"></a>Uwagi

Funkcja tłumaczy pobrany tekst, usuwając dodatkowe spacje na początku tekstu, a następnie konwertując cyfry dziesiętne. Funkcja przestaje tłumaczyć, gdy osiągnie koniec tekstu lub napotka znak nieliczny.

Ta funkcja zwraca wartość zero, jeśli przetłumaczona wartość jest większa niż INT_MAX (dla podpisanych numerów) lub UINT_MAX (dla niepodpisanych liczb).

## <a name="colecontrolcontainergetdlgitemtext"></a><a name="getdlgitemtext"></a>COleControlContainer::GetDlgItemText

Pobiera tekst danego formantu.

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identyfikator formantu.

*Lpstr*<br/>
Wskaźnik do tekstu formantu.

*nMaxCount*<br/>
Określa maksymalną długość w znakach ciągu, który ma zostać skopiowany do buforu wskazywionego przez *lpStr*. Jeśli długość ciągu przekracza limit, ciąg jest obcinany.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość określa liczbę znaków skopiowanych do buforu, z wyłączeniem kończącego się znaku null.

Jeśli funkcja nie powiedzie się, zwracana wartość wynosi zero. Aby uzyskać rozszerzone informacje o błędzie, zadzwoń [do GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="colecontrolcontainerhandlesetfocus"></a><a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus

Określa, czy kontener obsługuje WM_SETFOCUS wiadomości.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli kontener obsługuje WM_SETFOCUS komunikatów; w przeciwnym razie zero.

## <a name="colecontrolcontainerhandlewindowlessmessage"></a><a name="handlewindowlessmessage"></a>COleControlContainer::HandleWindowlessMessage

Przetwarza komunikaty okien dla formantów bez okien.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>Parametry

*Komunikat*<br/>
Identyfikator komunikatu okna, dostarczony przez system Windows.

*Wparam*<br/>
Parametr wiadomości; przez system Windows. Określa dodatkowe informacje specyficzne dla wiadomości. Zawartość tego parametru zależy od wartości parametru *message.*

*Lparam*<br/>
Parametr wiadomości; przez system Windows. Określa dodatkowe informacje specyficzne dla wiadomości. Zawartość tego parametru zależy od wartości parametru *message.*

*plResult (wyniki)*<br/>
Kod wyniku systemu Windows. Określa wynik przetwarzania wiadomości i zależy od wysłanej wiadomości.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji można dostosować obsługę komunikatów sterujących bez okien.

## <a name="colecontrolcontainerisdlgbuttonchecked"></a><a name="isdlgbuttonchecked"></a>COleControlContainer::IsDlgButtonSprawdziony

Określa stan określonego przycisku.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Parametry

*nIDButton (przycisk NID)*<br/>
Identyfikator formantu przycisku.

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość za pomocą przycisku utworzonego w stylu BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON lub BS_3STATE. Może być jedną z następujących czynności:

- BST_CHECKED przycisk jest zaznaczony.

- BST_INDETERMINATE Przycisk jest wyszarzony, co oznacza stan nieokreślony (dotyczy tylko wtedy, gdy przycisk ma styl BS_3STATE lub BS_AUTO3STATE).

- BST_UNCHECKED Przycisk jest wyczyszczony.

### <a name="remarks"></a>Uwagi

Jeśli przycisk jest formantem trójstanowym, funkcja elementu członkowskiego określa, czy jest wyszarzona, zaznaczona, czy żadna.

## <a name="colecontrolcontainerm_crback"></a><a name="m_crback"></a>COleControlContainer::m_crBack

Kolor tła kontenera.

```
COLORREF m_crBack;
```

## <a name="colecontrolcontainerm_crfore"></a><a name="m_crfore"></a>COleControlContainer::m_crFore

Kolor pierwszego planu kontenera.

```
COLORREF m_crFore;
```

## <a name="colecontrolcontainerm_listsitesorwnds"></a><a name="m_listsitesorwnds"></a>COleControlContainer::m_listSitesOrWnds

Lista witryn kontrolnych hostowanych przez kontener.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

## <a name="colecontrolcontainerm_nwindowlesscontrols"></a><a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls

Liczba formantów bez okien obsługiwanych przez kontener formantu.

```
int m_nWindowlessControls;
```

## <a name="colecontrolcontainerm_polefont"></a><a name="m_polefont"></a>COleControlContainer::m_pOleFont

Wskaźnik do czcionki OLE w witrynie formantu niestandardowego.

```
LPFONTDISP m_pOleFont;
```

## <a name="colecontrolcontainerm_psitecapture"></a><a name="m_psitecapture"></a>COleControlContainer::m_pSiteCapture

Wskaźnik do witryny kontroli przechwytywania.

```
COleControlSite* m_pSiteCapture;
```

## <a name="colecontrolcontainerm_psitefocus"></a><a name="m_psitefocus"></a>COleControlContainer::m_pSiteFocus

Wskaźnik do witryny sterowania, która obecnie ma fokus wejściowy.

```
COleControlSite* m_pSiteFocus;
```

## <a name="colecontrolcontainerm_psiteuiactive"></a><a name="m_psiteuiactive"></a>COleControlContainer::m_pSiteUIActive

Wskaźnik do witryny sterowania, która jest w miejscu aktywowane.

```
COleControlSite* m_pSiteUIActive;
```

## <a name="colecontrolcontainerm_pwnd"></a><a name="m_pwnd"></a>COleControlContainer::m_pWnd

Wskaźnik do obiektu okna skojarzonego z kontenerem.

```
CWnd* m_pWnd;
```

## <a name="colecontrolcontainerm_sitemap"></a><a name="m_sitemap"></a>COleControlContainer::m_siteMap

Mapa witryny.

```
CMapPtrToPtr m_siteMap;
```

## <a name="colecontrolcontaineronpaint"></a><a name="onpaint"></a>COleControlContainer::OnPaint

Wywoływana przez platformę do obsługi żądań WM_PAINT.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia używanego przez kontener.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wiadomość została obsłużona; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji należy dostosować proces malowania.

## <a name="colecontrolcontaineronuiactivate"></a><a name="onuiactivate"></a>COleControlContainer::OnUIActivate

Wywoływane przez ramy, gdy miejsce kontroli, wskazane przez *pSite*, ma być aktywowany w miejscu.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parametry

*pWitła*<br/>
Wskaźnik do witryny sterowania, która ma być aktywowana w miejscu.

### <a name="remarks"></a>Uwagi

Aktywacja w miejscu oznacza, że menu główne kontenera jest zastępowane menu złożonym w miejscu.

## <a name="colecontrolcontaineronuideactivate"></a><a name="onuideactivate"></a>COleControlContainer::OnUIDeaktywacji

Wywoływana przez ramy, gdy miejsce kontroli, wskazane przez *pSite*, ma zostać dezaktywowane.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parametry

*pWitła*<br/>
Wskaźnik do witryny sterowania, który ma zostać dezaktywowany.

### <a name="remarks"></a>Uwagi

Po odebraniu tego powiadomienia kontener powinien ponownie zainstalować swój interfejs użytkownika i skupić się.

## <a name="colecontrolcontainerscrollchildren"></a><a name="scrollchildren"></a>COleControlContainer::ScrollChildren

Wywoływane przez strukturę, gdy wiadomości przewijania są odbierane z okna podrzędnego.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Parametry

*Dx*<br/>
Ilość przewijania wzdłuż osi x w pikselach.

*Dy*<br/>
Ilość przewijania wzdłuż osi y w pikselach.

## <a name="colecontrolcontainersenddlgitemmessage"></a><a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage

Wysyła wiadomość do określonego formantu.

```
virtual LRESULT SendDlgItemMessage(
    int nID,
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Określa identyfikator formantu odbieranego przez wiadomość.

*Komunikat*<br/>
Określa wiadomość, która ma zostać wysłana.

*Wparam*<br/>
Określa dodatkowe informacje specyficzne dla wiadomości.

*Lparam*<br/>
Określa dodatkowe informacje specyficzne dla wiadomości.

## <a name="colecontrolcontainersetdlgitemint"></a><a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt

Ustawia tekst formantu w oknie dialogowym na reprezentację ciągu określonej wartości całkowitej.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identyfikator formantu.

*wartość nValue*<br/>
Wartość całkowita, która ma być wyświetlana.

*bPodpisany*<br/>
Określa, czy parametr *nValue* jest podpisany, czy niepodpisany. Jeśli ten parametr ma wartość PRAWDA, *nValue* jest podpisany. Jeśli ten parametr ma wartość PRAWDA, a *wartość nValue* jest mniejsza niż zero, znak minus jest umieszczany przed pierwszą cyfrą w ciągu. Jeśli ten parametr ma wartość FAŁSZ, *wartość nValue* jest niepodpisywalna.

## <a name="colecontrolcontainersetdlgitemtext"></a><a name="setdlgitemtext"></a>COleControlContainer::SetDlgItemText

Ustawia tekst określonego formantu, używając tekstu zawartego w *lpszString*.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identyfikator formantu.

*lpszString*<br/>
Wskaźnik do tekstu formantu.

## <a name="see-also"></a>Zobacz też

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleControlSite](../../mfc/reference/colecontrolsite-class.md)<br/>
[Klasa COccManager](../../mfc/reference/coccmanager-class.md)
