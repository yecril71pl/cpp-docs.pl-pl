---
title: Funkcje globalne sterowania kompozytowymi
ms.date: 11/04/2016
f1_keywords:
- atlhost/ATL::AtlAxDialogBox
- atlhost/ATL::AtlAxCreateDialog
- atlhost/ATL::AtlAxCreateControl
- atlhost/ATL::AtlAxCreateControlEx
- atlhost/ATL::AtlAxCreateControlLic
- atlhost/ATL::AtlAxCreateControlLicEx
- atlhost/ATL::AtlAxAttachControl
- atlhost/ATL::AtlAxGetHost
- atlhost/ATL::AtlAxGetControl
- atlhost/ATL::AtlSetChildSite
- atlhost/ATL::AtlAxWinInit
- atlhost/ATL::AtlAxWinTerm
- atlhost/ATL::AtlGetObjectSourceInterface
helpviewer_keywords:
- composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
ms.openlocfilehash: 99ecd4cf04b3eb696f897d6ef5a5e3839d46ef17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331609"
---
# <a name="composite-control-global-functions"></a>Funkcje globalne sterowania kompozytowymi

Te funkcje zapewniają obsługę tworzenia okien dialogowych oraz tworzenia, hostingu i licencjonowania formantów ActiveX.

> [!IMPORTANT]
> Funkcji wymienionych w poniższej tabeli nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

|||
|-|-|
|[Skrzynka z promieniami 2010](#atlaxdialogbox)|Tworzy modalne okno dialogowe z szablonu okna dialogowego dostarczonego przez użytkownika. Wynikowe okno dialogowe może zawierać kontrolki ActiveX.|
|[AtlAxCreateDialog](#atlaxcreatedialog)|Tworzy niemodalne okno dialogowe z szablonu okna dialogowego dostarczonego przez użytkownika. Wynikowe okno dialogowe może zawierać kontrolki ActiveX.|
|[AtlAxCreateControl](#atlaxcreatecontrol)|Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie.|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Tworzy formant ActiveX, inicjuje go, hostuje go w określonym oknie i pobiera wskaźnik interfejsu (lub wskaźniki) z formantu.|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie.|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Tworzy licencjonowany formant ActiveX, inicjuje go, hostuje go w określonym oknie i pobiera wskaźnik interfejsu (lub wskaźniki) z formantu.|
|[AtlAxAttachControl (AtlAxAttachControl)](#atlaxattachcontrol)|Dołącza wcześniej utworzony formant do określonego okna.|
|[AtlAxGetHost (AtlAxGetHost)](#atlaxgethost)|Służy do uzyskania bezpośredniego wskaźnika interfejsu do kontenera dla określonego okna (jeśli istnieje), biorąc pod uwagę jego dojście.|
|[Kontrola AtlAxGetControl](#atlaxgetcontrol)|Służy do uzyskania bezpośredniego wskaźnika interfejsu do formantu znajdującego się wewnątrz określonego okna (jeśli istnieje), biorąc pod uwagę jego dojście.|
|[AtlSetChildWita](#atlsetchildsite)|Inicjuje `IUnknown` witrynę podrzędną.|
|[AtlAxWinInit (AtlAxWinInit)](#atlaxwininit)|Inicjuje kod hostingu obiektów AxWin.|
|[AtlAxWinTerm (własnoręcznisze)](#atlaxwinterm)|Uninitializes kod hostingu dla obiektów AxWin.|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Zwraca informacje o domyślnym interfejsie źródłowym obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlhost.h

## <a name="atlaxdialogbox"></a><a name="atlaxdialogbox"></a>Skrzynka z promieniami 2010

Tworzy modalne okno dialogowe z szablonu okna dialogowego dostarczonego przez użytkownika.

```
ATLAPI_(int) AtlAxDialogBox(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>Parametry

*hInstance (Nieumieja)*<br/>
[w] Identyfikuje wystąpienie modułu, którego plik wykonywalny zawiera szablon okna dialogowego.

*lpTemplateName*<br/>
[w] Identyfikuje szablon okna dialogowego. Ten parametr jest wskaźnikiem do ciągu znaków zakończonym z wartością null, który określa nazwę szablonu okna dialogowego lub wartością całkowitą określającą identyfikator zasobu szablonu okna dialogowego. Jeśli parametr określa identyfikator zasobu, jego słowo wysokiego rzędu musi wynosić zero, a jego słowo niskiego rzędu musi zawierać identyfikator. Do utworzenia tej wartości można użyć makra [MAKEINTRESOURCE.](/windows/win32/api/winuser/nf-winuser-makeintresourcew)

*hWndRodziciek*<br/>
[w] Identyfikuje okno, które jest właścicielem okna dialogowego.

*lpDialogProc*<br/>
[w] Wskazuje procedurę okna dialogowego. Aby uzyskać więcej informacji na temat procedury okna dialogowego, zobacz [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
[w] Określa wartość, która ma być przekazywalna do okna dialogowego w parametrze *lParam* komunikatu WM_INITDIALOG.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Aby `AtlAxDialogBox` użyć z szablonem okna dialogowego zawierającym kontrolkę ActiveX, należy określić prawidłowy identyfikator CLSID, identyfikator APPID lub ciąg ADRESU URL jako pole *tekstowe* sekcji **CONTROL** zasobu okna dialogowego wraz z "AtlAxWin80" jako pole *nazwy klasy* w tej samej sekcji. Poniżej przedstawiono, jak może wyglądać prawidłowa sekcja **CONTROL:**

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

Aby uzyskać więcej informacji na temat edytowania skryptów zasobów, zobacz [Jak: Otwieranie pliku skryptu zasobu w formacie tekstowym](../../windows/how-to-open-a-resource-script-file-in-text-format.md). Aby uzyskać więcej informacji na temat instrukcji definicji zasobów kontroli, zobacz [typowe parametry kontroli](/windows/win32/menurc/common-control-parameters) w obszarze Zestaw Windows SDK: Narzędzia zestawu SDK.

Aby uzyskać więcej informacji na temat okien dialogowych w ogóle, zobacz [DialogBox](/windows/win32/api/winuser/nf-winuser-dialogboxw) i [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) w windows SDK.

## <a name="atlaxcreatedialog"></a><a name="atlaxcreatedialog"></a>AtlAxCreateDialog

Tworzy niemodalne okno dialogowe z szablonu okna dialogowego dostarczonego przez użytkownika.

```
ATLAPI_(HWND) AtlAxCreateDialog(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>Parametry

*hInstance (Nieumieja)*<br/>
[w] Identyfikuje wystąpienie modułu, którego plik wykonywalny zawiera szablon okna dialogowego.

*lpTemplateName*<br/>
[w] Identyfikuje szablon okna dialogowego. Ten parametr jest wskaźnikiem do ciągu znaków zakończonym z wartością null, który określa nazwę szablonu okna dialogowego lub wartością całkowitą określającą identyfikator zasobu szablonu okna dialogowego. Jeśli parametr określa identyfikator zasobu, jego słowo wysokiego rzędu musi wynosić zero, a jego słowo niskiego rzędu musi zawierać identyfikator. Do utworzenia tej wartości można użyć makra [MAKEINTRESOURCE.](/windows/win32/api/winuser/nf-winuser-makeintresourcew)

*hWndRodziciek*<br/>
[w] Identyfikuje okno, które jest właścicielem okna dialogowego.

*lpDialogProc*<br/>
[w] Wskazuje procedurę okna dialogowego. Aby uzyskać więcej informacji na temat procedury okna dialogowego, zobacz [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
[w] Określa wartość, która ma być przekazywalna do okna dialogowego w parametrze *lParam* komunikatu WM_INITDIALOG.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Wynikowe okno dialogowe może zawierać kontrolki ActiveX.

Zobacz [CreateDialog](/windows/win32/api/winuser/nf-winuser-createdialogw) i [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) w windows SDK.

## <a name="atlaxcreatecontrol"></a><a name="atlaxcreatecontrol"></a>Sterowanie AtlAxCreateControl

Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie.

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wskaźnik do ciągu, który ma być przekazany do formantu. Musi być sformatowany w jeden z następujących sposobów:

- ProgID, taki jak`"MSCAL.Calendar.7"`

- ClSID, taki jak`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adres URL, taki jak`"<https://www.microsoft.com>"`

- Odwołanie do aktywnego dokumentu, takiego jak`"file://\\\Documents\MyDoc.doc"`

- Fragment html, taki jak`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musi poprzedzać fragment HTML, tak aby został wyznaczony jako strumień MSHTML.

*Hwnd*<br/>
[w] Dojście do okna, do które zostanie dołączony formant.

*pStream (Strumień)*<br/>
[w] Wskaźnik do strumienia, który jest używany do inicjowania właściwości formantu. Może mieć wartość NULL.

*PpUnkContainer*<br/>
[na zewnątrz] Adres wskaźnika, który otrzyma `IUnknown` kontenera. Może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja globalna daje taki sam wynik jak wywołanie [AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*, *hWnd*, *pStream*, NULL, NULL, NULL, NULL);.

Aby utworzyć licencjonowany formant ActiveX, zobacz [AtlAxCreateControlLic](#atlaxcreatecontrollic).

## <a name="atlaxcreatecontrolex"></a><a name="atlaxcreatecontrolex"></a>AtlAxCreateControlEx

Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie. Można również utworzyć wskaźnik interfejsu i zbiornik zdarzenia dla nowego formantu.

```
ATLAPI AtlAxCreateControlEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wskaźnik do ciągu, który ma być przekazany do formantu. Musi być sformatowany w jeden z następujących sposobów:

- ProgID, taki jak`"MSCAL.Calendar.7"`

- ClSID, taki jak`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adres URL, taki jak`"<https://www.microsoft.com>"`

- Odwołanie do aktywnego dokumentu, takiego jak`"file://\\\Documents\MyDoc.doc"`

- Fragment html, taki jak`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musi poprzedzać fragment HTML, tak aby został wyznaczony jako strumień MSHTML.

*Hwnd*<br/>
[w] Dojście do okna, do które zostanie dołączony formant.

*pStream (Strumień)*<br/>
[w] Wskaźnik do strumienia, który jest używany do inicjowania właściwości formantu. Może mieć wartość NULL.

*PpUnkContainer*<br/>
[na zewnątrz] Adres wskaźnika, który otrzyma `IUnknown` kontenera. Może mieć wartość NULL.

*kontrola ppUnkControl*<br/>
[na zewnątrz] Adres wskaźnika, który otrzyma `IUnknown` utworzonego formantu. Może mieć wartość NULL.

*iidSink ( iidSink )*<br/>
Identyfikator interfejsu wychodzącego interfejsu w contained object.

*punkSink (polski)*<br/>
Wskaźnik do `IUnknown` interfejsu obiektu ujścia, który ma być połączony z punktem połączenia określonym przez *iidSink* na contained object po pomyślnym utworzeniu obiektu zawartego.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

`AtlAxCreateControlEx`jest podobny do [AtlAxCreateControl,](#atlaxcreatecontrol) ale również pozwala na odbieranie wskaźnik interfejsu do nowo utworzonego formantu i skonfigurować ujście zdarzeń, aby odbierać zdarzenia uruchamiane przez formant.

Aby utworzyć licencjonowany formant ActiveX, zobacz [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).

## <a name="atlaxcreatecontrollic"></a><a name="atlaxcreatecontrollic"></a>AtlAxCreateControlLic (AtlAxCreateControlLic)

Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie.

```
ATLAPI AtlAxCreateControlLic(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wskaźnik do ciągu, który ma być przekazany do formantu. Musi być sformatowany w jeden z następujących sposobów:

- ProgID, taki jak`"MSCAL.Calendar.7"`

- ClSID, taki jak`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adres URL, taki jak`"<https://www.microsoft.com>"`

- Odwołanie do aktywnego dokumentu, takiego jak`"file://\\\Documents\MyDoc.doc"`

- Fragment html, taki jak`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musi poprzedzać fragment HTML, tak aby został wyznaczony jako strumień MSHTML.

*Hwnd*<br/>
Dojście do okna, do które zostanie dołączony formant.

*pStream (Strumień)*<br/>
Wskaźnik do strumienia, który jest używany do inicjowania właściwości formantu. Może mieć wartość NULL.

*PpUnkContainer*<br/>
Adres wskaźnika, który otrzyma `IUnknown` kontenera. Może mieć wartość NULL.

*bstrLic (bstrlic)*<br/>
BSTR zawierający licencję na formant.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="example"></a>Przykład

Zobacz [Hosting ActiveX Formanty za pomocą ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) przykład jak używać `AtlAxCreateControlLic`.

## <a name="atlaxcreatecontrollicex"></a><a name="atlaxcreatecontrollicex"></a>AtlAxCreateControlLicEx

Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie. Można również utworzyć wskaźnik interfejsu i zbiornik zdarzenia dla nowego formantu.

```
ATLAPI AtlAxCreateControlLicEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wskaźnik do ciągu, który ma być przekazany do formantu. Musi być sformatowany w jeden z następujących sposobów:

- ProgID, taki jak`"MSCAL.Calendar.7"`

- ClSID, taki jak`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adres URL, taki jak`"<https://www.microsoft.com>"`

- Odwołanie do aktywnego dokumentu, takiego jak`"file://\\\Documents\MyDoc.doc"`

- Fragment html, taki jak`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`musi poprzedzać fragment HTML, tak aby został wyznaczony jako strumień MSHTML.

*Hwnd*<br/>
Dojście do okna, do które zostanie dołączony formant.

*pStream (Strumień)*<br/>
Wskaźnik do strumienia, który jest używany do inicjowania właściwości formantu. Może mieć wartość NULL.

*PpUnkContainer*<br/>
Adres wskaźnika, który otrzyma `IUnknown` kontenera. Może mieć wartość NULL.

*kontrola ppUnkControl*<br/>
[na zewnątrz] Adres wskaźnika, który otrzyma `IUnknown` utworzonego formantu. Może mieć wartość NULL.

*iidSink ( iidSink )*<br/>
Identyfikator interfejsu wychodzącego interfejsu w contained object.

*punkSink (polski)*<br/>
Wskaźnik do `IUnknown` interfejsu obiektu ujścia, który ma być połączony z punktem połączenia określonym przez *iidSink* na contained object po pomyślnym utworzeniu obiektu zawartego.

*bstrLic (bstrlic)*<br/>
BSTR zawierający licencję na formant.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

`AtlAxCreateControlLicEx`jest podobny do [AtlAxCreateControlLic,](#atlaxcreatecontrollic) ale również pozwala na odbieranie wskaźnik interfejsu do nowo utworzonego formantu i skonfigurować ujście zdarzeń, aby odbierać zdarzenia uruchamiane przez formant.

### <a name="example"></a>Przykład

Zobacz [Hosting ActiveX Formanty za pomocą ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) przykład jak używać `AtlAxCreateControlLicEx`.

## <a name="atlaxattachcontrol"></a><a name="atlaxattachcontrol"></a>AtlAxAttachControl (AtlAxAttachControl)

Dołącza wcześniej utworzony formant do określonego okna.

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*pKontroluj*<br/>
[w] Wskaźnik do `IUnknown` formantu.

*Hwnd*<br/>
[w] Dojście do okna, które będzie hostować formant.

*PpUnkContainer*<br/>
[na zewnątrz] Wskaźnik do wskaźnika `IUnknown` do obiektu kontenera.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Za pomocą [atlAxCreateControlEx](#atlaxcreatecontrolex) i [AtlAxCreateControl](#atlaxcreatecontrol) jednocześnie utworzyć i dołączyć formant.

> [!NOTE]
> Dołączony obiekt sterujący musi zostać poprawnie `AtlAxAttachControl`zainicjowany przed wywołaniem .

## <a name="atlaxgethost"></a><a name="atlaxgethost"></a>AtlAxGetHost (AtlAxGetHost)

Uzyskuje bezpośredni wskaźnik interfejsu do kontenera dla określonego okna (o ile istnieje), biorąc pod uwagę jego uchwyt.

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parametry

*H*<br/>
[w] Dojście do okna, które obsługuje formant.

*S*<br/>
[na zewnątrz] Kontener `IUnknown` formantu.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="atlaxgetcontrol"></a><a name="atlaxgetcontrol"></a>Kontrola AtlAxGetControl

Uzyskuje bezpośredni wskaźnik interfejsu do formantu zawartego wewnątrz określonego okna, biorąc pod uwagę jego uchwyt.

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parametry

*H*<br/>
[w] Dojście do okna, które obsługuje formant.

*S*<br/>
[na zewnątrz] Kontrolka `IUnknown` jest hostowana.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="atlsetchildsite"></a><a name="atlsetchildsite"></a>AtlSetChildWita

Wywołanie tej funkcji, aby ustawić miejsce `IUnknown` obiektu podrzędnego do obiektu nadrzędnego.

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>Parametry

*punkChild*<br/>
[w] Wskaźnik do `IUnknown` interfejsu podrzędnego.

*punkRożka*<br/>
[w] Wskaźnik do `IUnknown` interfejsu nadrzędnego.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="atlaxwininit"></a><a name="atlaxwininit"></a>AtlAxWinInit (AtlAxWinInit)

Ta funkcja inicjuje kod hostingu sterowania ATL, rejestrując klasy okien **"AtlAxWin80"** i **"AtlAxWinLic80"** oraz kilka niestandardowych komunikatów okiennych.

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli inicjowanie kodu hostingu formantu zakończyło się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja musi być wywołana przed użyciem interfejsu API hostingu hosta formantu ATL. Po wywołaniu tej funkcji klasa okna **"AtlAxWin"** może być używana w wywołaniach [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) lub [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw), zgodnie z opisem w programie Windows SDK.

## <a name="atlaxwinterm"></a><a name="atlaxwinterm"></a>AtlAxWinTerm (własnoręcznisze)

Ta funkcja nie jest innitializuje kod hostingu sterowania ATL przez wyrejestrowanie klas okien **"AtlAxWin80"** i **"AtlAxWinLic80".**

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Ta funkcja po prostu wywołuje [UnregisterClass](/windows/win32/api/winuser/nf-winuser-unregisterclassw) zgodnie z opisem w windows SDK.

Wywołanie tej funkcji, aby oczyścić po wszystkich istniejących okien hosta zostały zniszczone, jeśli nazywasz [AtlAxWinInit](#atlaxwininit) i nie trzeba już tworzyć okna hosta. Jeśli ta funkcja nie zostanie wywołana, klasa okna zostanie automatycznie wyrejestrowana po zakończeniu procesu.

## <a name="atlgetobjectsourceinterface"></a><a name="atlgetobjectsourceinterface"></a>AtlGetObjectSourceInterface

Wywołaj tę funkcję, aby pobrać informacje o domyślnym interfejsie źródła obiektu.

```
ATLAPI AtlGetObjectSourceInterface(
    IUnknown* punkObj,
    GUID* plibid,
    IID* piid,
    unsigned short* pdwMajor,
    unsigned short* pdwMinor);
```

### <a name="parameters"></a>Parametry

*punkObj*<br/>
[w] Wskaźnik do obiektu, dla którego mają być zwracane informacje.

*plibid ( plibid )*<br/>
[na zewnątrz] Wskaźnik do libid biblioteki typów zawierającej definicję interfejsu źródłowego.

*piid*<br/>
[na zewnątrz] Wskaźnik do identyfikatora interfejsu domyślnego interfejsu źródłowego obiektu.

*pdwMajor*<br/>
[na zewnątrz] Wskaźnik do głównego numeru wersji biblioteki typów zawierającej definicję interfejsu źródłowego.

*pdwMinor*<br/>
[na zewnątrz] Wskaźnik do pomocniczego numeru wersji biblioteki typów zawierającej definicję interfejsu źródłowego.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

`AtlGetObjectSourceInterface`może dostarczyć identyfikator interfejsu domyślnego interfejsu źródłowego, wraz z LIBID i głównych i pomocniczych numerów wersji biblioteki typów opisujących ten interfejs.

> [!NOTE]
> Aby ta funkcja pomyślnie pobrać żądane informacje, obiekt reprezentowany przez `IDispatch` *punkObj* musi implementować (i zwracać `IPersist`informacje o typie za pośrednictwem) `IDispatch::GetTypeInfo`plus musi również implementować albo `IProvideClassInfo2` lub . Informacje o typie interfejsu źródłowego muszą znajdować się w `IDispatch`tej samej bibliotece typów, co informacje o typie dla programu .

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak można zdefiniować klasę ujścia zdarzeń, co zmniejsza liczbę argumentów szablonu, `CEasySink`które można przekazać do `IDispEventImpl` gołych essentials. `EasyAdvise`i `EasyUnadvise` `AtlGetObjectSourceInterface` użyć do zainicjowania [iDispEventImpl](../../atl/reference/idispeventimpl-class.md) członków przed wywołaniem [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) lub [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise).

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Makra sterowania złożonego](../../atl/reference/composite-control-macros.md)
