---
title: Funkcje globalne kontrolki złożonej
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
ms.openlocfilehash: 467925baf59598d743650d4f98d210f789f2b179
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833559"
---
# <a name="composite-control-global-functions"></a>Funkcje globalne kontrolki złożonej

Te funkcje zapewniają obsługę tworzenia okien dialogowych oraz do tworzenia, hostingu i licencjonowania formantów ActiveX.

> [!IMPORTANT]
> Funkcje wymienione w poniższej tabeli nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

|Funkcja|Opis|
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|Tworzy modalne okno dialogowe z szablonu okna dialogowego dostarczonego przez użytkownika. Wyniki okna dialogowego mogą zawierać kontrolki ActiveX.|
|[AtlAxCreateDialog](#atlaxcreatedialog)|Tworzy niemodalne okno dialogowe z szablonu okna dialogowego dostarczonego przez użytkownika. Wyniki okna dialogowego mogą zawierać kontrolki ActiveX.|
|[AtlAxCreateControl](#atlaxcreatecontrol)|Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie.|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Tworzy formant ActiveX, inicjuje go, hostuje w określonym oknie i Pobiera wskaźnik interfejsu (lub wskaźniki) z formantu.|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie.|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Tworzy licencjonowany formant ActiveX, inicjuje go, hostuje w określonym oknie i Pobiera wskaźnik interfejsu (lub wskaźniki) z formantu.|
|[AtlAxAttachControl](#atlaxattachcontrol)|Dołącza wcześniej utworzony formant do określonego okna.|
|[AtlAxGetHost](#atlaxgethost)|Służy do uzyskania bezpośredniego wskaźnika interfejsu do kontenera dla określonego okna (jeśli istnieje), z uwzględnieniem jego uchwytu.|
|[AtlAxGetControl](#atlaxgetcontrol)|Służy do uzyskania bezpośredniego wskaźnika interfejsu do kontrolki zawartej w określonym oknie (jeśli istnieje), z uwzględnieniem uchwytu.|
|[AtlSetChildSite](#atlsetchildsite)|Inicjuje `IUnknown` lokację podrzędną.|
|[AtlAxWinInit](#atlaxwininit)|Inicjuje kod hostingu dla obiektów AxWin.|
|[AtlAxWinTerm](#atlaxwinterm)|Odinicjalizuje kod hostingu dla obiektów AxWin.|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Zwraca informacje o domyślnym interfejsie źródłowym obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlhost. h

## <a name="atlaxdialogbox"></a><a name="atlaxdialogbox"></a> AtlAxDialogBox

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

*hInstance*<br/>
podczas Identyfikuje wystąpienie modułu, którego plik wykonywalny zawiera szablon okna dialogowego.

*lpTemplateName*<br/>
podczas Identyfikuje szablon okna dialogowego. Ten parametr jest wskaźnikiem do ciągu znaków, który jest zakończony znakiem null, który określa nazwę szablonu okna dialogowego lub wartość całkowitą określającą identyfikator zasobu szablonu okna dialogowego. Jeśli parametr określa identyfikator zasobu, jego słowo o wysokim porządku musi mieć wartość zero, a jego słowo w niskim porządku musi zawierać identyfikator. Aby utworzyć tę wartość, można użyć makra [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) .

*hWndParent*<br/>
podczas Identyfikuje okno, które jest właścicielem okna dialogowego.

*lpDialogProc*<br/>
podczas Wskazuje procedurę okna dialogowego. Aby uzyskać więcej informacji na temat procedury okna dialogowego, zobacz [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
podczas Określa wartość, która ma zostać przekazana do okna dialogowego w parametrze *lParam* komunikatu WM_INITDIALOG.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Aby użyć `AtlAxDialogBox` z szablonem okna dialogowego zawierającym formant ActiveX, określ prawidłowy identyfikator CLSID, identyfikator appid lub ciąg adresu URL jako pole *tekstowe* sekcji **kontrolki** zasobu okna dialogowego wraz z "AtlAxWin80" jako pole *nazwy klasy* w tej samej sekcji. Poniżej pokazano, jak może wyglądać prawidłowa sekcja **kontrolki** :

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

Aby uzyskać więcej informacji na temat edytowania skryptów zasobów, zobacz [jak: otwieranie pliku skryptu zasobu w formacie tekstowym](../../windows/how-to-open-a-resource-script-file-in-text-format.md). Aby uzyskać więcej informacji na temat sterowania instrukcjami definicji zasobów, zobacz [Parametry formantów wspólnych](/windows/win32/menurc/common-control-parameters) w obszarze Windows SDK: SDK Tools.

Aby uzyskać więcej informacji na temat ogólnych okien dialogowych, zobacz [DialogBox](/windows/win32/api/winuser/nf-winuser-dialogboxw) i [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) w Windows SDK.

## <a name="atlaxcreatedialog"></a><a name="atlaxcreatedialog"></a> AtlAxCreateDialog

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

*hInstance*<br/>
podczas Identyfikuje wystąpienie modułu, którego plik wykonywalny zawiera szablon okna dialogowego.

*lpTemplateName*<br/>
podczas Identyfikuje szablon okna dialogowego. Ten parametr jest wskaźnikiem do ciągu znaków, który jest zakończony znakiem null, który określa nazwę szablonu okna dialogowego lub wartość całkowitą określającą identyfikator zasobu szablonu okna dialogowego. Jeśli parametr określa identyfikator zasobu, jego słowo o wysokim porządku musi mieć wartość zero, a jego słowo w niskim porządku musi zawierać identyfikator. Aby utworzyć tę wartość, można użyć makra [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) .

*hWndParent*<br/>
podczas Identyfikuje okno, które jest właścicielem okna dialogowego.

*lpDialogProc*<br/>
podczas Wskazuje procedurę okna dialogowego. Aby uzyskać więcej informacji na temat procedury okna dialogowego, zobacz [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
podczas Określa wartość, która ma zostać przekazana do okna dialogowego w parametrze *lParam* komunikatu WM_INITDIALOG.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Wyniki okna dialogowego mogą zawierać kontrolki ActiveX.

Zobacz [okno dialogowe](/windows/win32/api/winuser/nf-winuser-createdialogw) i [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) w Windows SDK.

## <a name="atlaxcreatecontrol"></a><a name="atlaxcreatecontrol"></a> AtlAxCreateControl

Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie.

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do ciągu, który ma zostać przesłany do kontrolki. Muszą być sformatowane w jeden z następujących sposobów:

- Identyfikator ProgID, taki jak `"MSCAL.Calendar.7"`

- Identyfikator CLSID, taki jak `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adres URL, taki jak `"<https://www.microsoft.com>"`

- Odwołanie do aktywnego dokumentu, takiego jak `"file://\\\Documents\MyDoc.doc"`

- Fragment kodu HTML, taki jak `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` musi poprzedzać fragment kodu HTML, aby został wyznaczył jako strumień MSHTML.

*Właściwość*<br/>
podczas Dojście do okna, do którego zostanie dołączona kontrolka.

*pStream*<br/>
podczas Wskaźnik do strumienia, który jest używany do inicjowania właściwości formantu. Może mieć wartość NULL.

*ppUnkContainer*<br/>
określoną Adres wskaźnika, który będzie otrzymywał `IUnknown` kontener. Może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja globalna daje ten sam wynik jak wywołanie [AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*, *HWND*, *pStream*, null, null, null, null);.

Aby utworzyć licencjonowany formant ActiveX, zobacz [AtlAxCreateControlLic](#atlaxcreatecontrollic).

## <a name="atlaxcreatecontrolex"></a><a name="atlaxcreatecontrolex"></a> AtlAxCreateControlEx

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

*lpszName*<br/>
Wskaźnik do ciągu, który ma zostać przesłany do kontrolki. Muszą być sformatowane w jeden z następujących sposobów:

- Identyfikator ProgID, taki jak `"MSCAL.Calendar.7"`

- Identyfikator CLSID, taki jak `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adres URL, taki jak `"<https://www.microsoft.com>"`

- Odwołanie do aktywnego dokumentu, takiego jak `"file://\\\Documents\MyDoc.doc"`

- Fragment kodu HTML, taki jak `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` musi poprzedzać fragment kodu HTML, aby został wyznaczył jako strumień MSHTML.

*Właściwość*<br/>
podczas Dojście do okna, do którego zostanie dołączona kontrolka.

*pStream*<br/>
podczas Wskaźnik do strumienia, który jest używany do inicjowania właściwości formantu. Może mieć wartość NULL.

*ppUnkContainer*<br/>
określoną Adres wskaźnika, który będzie otrzymywał `IUnknown` kontener. Może mieć wartość NULL.

*ppUnkControl*<br/>
określoną Adres wskaźnika, który będzie otrzymywał `IUnknown` utworzony formant. Może mieć wartość NULL.

*iidSink*<br/>
Identyfikator interfejsu interfejsu wychodzącego na zawartym obiekcie.

*punkSink*<br/>
Wskaźnik do `IUnknown` interfejsu obiektu ujścia, który ma być połączony z punktem połączenia określonym przez *iidSink* na zawartym obiekcie po pomyślnym utworzeniu zawartego obiektu.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

`AtlAxCreateControlEx` jest podobny do [AtlAxCreateControl](#atlaxcreatecontrol) , ale umożliwia również otrzymywanie wskaźnika interfejsu do nowo utworzonej kontrolki i skonfigurowanie ujścia zdarzeń do odbierania zdarzeń wyzwalanych przez formant.

Aby utworzyć licencjonowany formant ActiveX, zobacz [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).

## <a name="atlaxcreatecontrollic"></a><a name="atlaxcreatecontrollic"></a> AtlAxCreateControlLic

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

*lpszName*<br/>
Wskaźnik do ciągu, który ma zostać przesłany do kontrolki. Muszą być sformatowane w jeden z następujących sposobów:

- Identyfikator ProgID, taki jak `"MSCAL.Calendar.7"`

- Identyfikator CLSID, taki jak `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adres URL, taki jak `"<https://www.microsoft.com>"`

- Odwołanie do aktywnego dokumentu, takiego jak `"file://\\\Documents\MyDoc.doc"`

- Fragment kodu HTML, taki jak `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` musi poprzedzać fragment kodu HTML, aby został wyznaczył jako strumień MSHTML.

*Właściwość*<br/>
Dojście do okna, do którego zostanie dołączona kontrolka.

*pStream*<br/>
Wskaźnik do strumienia, który jest używany do inicjowania właściwości formantu. Może mieć wartość NULL.

*ppUnkContainer*<br/>
Adres wskaźnika, który będzie otrzymywał `IUnknown` kontener. Może mieć wartość NULL.

*bstrLic*<br/>
BSTR zawierający licencję dla kontrolki.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="example"></a>Przykład

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) , aby uzyskać przykład użycia `AtlAxCreateControlLic` .

## <a name="atlaxcreatecontrollicex"></a><a name="atlaxcreatecontrollicex"></a> AtlAxCreateControlLicEx

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

*lpszName*<br/>
Wskaźnik do ciągu, który ma zostać przesłany do kontrolki. Muszą być sformatowane w jeden z następujących sposobów:

- Identyfikator ProgID, taki jak `"MSCAL.Calendar.7"`

- Identyfikator CLSID, taki jak `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Adres URL, taki jak `"<https://www.microsoft.com>"`

- Odwołanie do aktywnego dokumentu, takiego jak `"file://\\\Documents\MyDoc.doc"`

- Fragment kodu HTML, taki jak `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` musi poprzedzać fragment kodu HTML, aby został wyznaczył jako strumień MSHTML.

*Właściwość*<br/>
Dojście do okna, do którego zostanie dołączona kontrolka.

*pStream*<br/>
Wskaźnik do strumienia, który jest używany do inicjowania właściwości formantu. Może mieć wartość NULL.

*ppUnkContainer*<br/>
Adres wskaźnika, który będzie otrzymywał `IUnknown` kontener. Może mieć wartość NULL.

*ppUnkControl*<br/>
określoną Adres wskaźnika, który będzie otrzymywał `IUnknown` utworzony formant. Może mieć wartość NULL.

*iidSink*<br/>
Identyfikator interfejsu interfejsu wychodzącego na zawartym obiekcie.

*punkSink*<br/>
Wskaźnik do `IUnknown` interfejsu obiektu ujścia, który ma być połączony z punktem połączenia określonym przez *iidSink* na zawartym obiekcie po pomyślnym utworzeniu zawartego obiektu.

*bstrLic*<br/>
BSTR zawierający licencję dla kontrolki.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

`AtlAxCreateControlLicEx` jest podobny do [AtlAxCreateControlLic](#atlaxcreatecontrollic) , ale umożliwia również otrzymywanie wskaźnika interfejsu do nowo utworzonej kontrolki i skonfigurowanie ujścia zdarzeń do odbierania zdarzeń wyzwalanych przez formant.

### <a name="example"></a>Przykład

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) , aby uzyskać przykład użycia `AtlAxCreateControlLicEx` .

## <a name="atlaxattachcontrol"></a><a name="atlaxattachcontrol"></a> AtlAxAttachControl

Dołącza wcześniej utworzony formant do określonego okna.

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
podczas Wskaźnik do `IUnknown` kontrolki.

*Właściwość*<br/>
podczas Dojście do okna, które będzie hostować formant.

*ppUnkContainer*<br/>
określoną Wskaźnik do wskaźnika do `IUnknown` obiektu kontenera.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Aby jednocześnie utworzyć i dołączyć kontrolkę, użyj [AtlAxCreateControlEx](#atlaxcreatecontrolex) i [AtlAxCreateControl](#atlaxcreatecontrol) .

> [!NOTE]
> Dołączenie obiektu sterującego musi być poprawnie zainicjowane przed wywołaniem metody `AtlAxAttachControl` .

## <a name="atlaxgethost"></a><a name="atlaxgethost"></a> AtlAxGetHost

Uzyskuje bezpośredni wskaźnik interfejsu do kontenera dla określonego okna (o ile istnieje), biorąc pod uwagę jego uchwyt.

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parametry

*c*<br/>
podczas Uchwyt do okna, w którym znajduje się kontrolka.

*miesięcznie*<br/>
określoną `IUnknown` Kontener formantu.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="atlaxgetcontrol"></a><a name="atlaxgetcontrol"></a> AtlAxGetControl

Uzyskuje bezpośredni wskaźnik interfejsu do formantu zawartego wewnątrz określonego okna, biorąc pod uwagę jego uchwyt.

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parametry

*c*<br/>
podczas Uchwyt do okna, w którym znajduje się kontrolka.

*miesięcznie*<br/>
określoną Kontrolka, która jest `IUnknown` hostowana.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

## <a name="atlsetchildsite"></a><a name="atlsetchildsite"></a> AtlSetChildSite

Wywołaj tę funkcję, aby ustawić lokację obiektu podrzędnego z `IUnknown` obiektem nadrzędnym.

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>Parametry

*punkChild*<br/>
podczas Wskaźnik do `IUnknown` interfejsu podrzędnego.

*punkParent*<br/>
podczas Wskaźnik do `IUnknown` interfejsu elementu nadrzędnego.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="atlaxwininit"></a><a name="atlaxwininit"></a> AtlAxWinInit

Ta funkcja inicjuje kod hostingu formantu ATL przez zarejestrowanie klas okien **"AtlAxWin80"** i **"AtlAxWinLic80"** oraz kilka niestandardowych komunikatów okien.

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli Inicjalizacja kodu hostingu formantu zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja musi zostać wywołana przed użyciem interfejsu API hostingu kontrolki ATL. Po wywołaniu tej funkcji Klasa okna **"AtlAxWin"** może być używana w wywołaniach [do](/windows/win32/api/winuser/nf-winuser-createwindoww) lub [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw), zgodnie z opisem w Windows SDK.

## <a name="atlaxwinterm"></a><a name="atlaxwinterm"></a> AtlAxWinTerm

Ta funkcja umożliwia odinicjowanie kodu hostingu formantu ATL przez Wyrejestrowanie klas okien **"AtlAxWin80"** i **"AtlAxWinLic80"** .

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Ta funkcja po prostu wywołuje [UnregisterClass](/windows/win32/api/winuser/nf-winuser-unregisterclassw) zgodnie z opisem w Windows SDK.

Wywołaj tę funkcję, aby wyczyścić po usunięciu wszystkich istniejących okien hosta, jeśli wywołano [AtlAxWinInit](#atlaxwininit) , i nie musisz już tworzyć okien hosta. Jeśli ta funkcja nie zostanie wywołana, Klasa Window zostanie wyrejestrowana automatycznie po zakończeniu procesu.

## <a name="atlgetobjectsourceinterface"></a><a name="atlgetobjectsourceinterface"></a> AtlGetObjectSourceInterface

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
podczas Wskaźnik do obiektu, dla którego ma zostać zwrócona informacja.

*plibid*<br/>
określoną Wskaźnik do identyfikatora LIBID biblioteki typów zawierającej definicję interfejsu źródłowego.

*piid*<br/>
określoną Wskaźnik do identyfikatora interfejsu domyślnego interfejsu źródłowego obiektu.

*pdwMajor*<br/>
określoną Wskaźnik do głównego numeru wersji biblioteki typów zawierającej definicję interfejsu źródłowego.

*pdwMinor*<br/>
określoną Wskaźnik do pomocniczego numeru wersji biblioteki typów zawierającej definicję interfejsu źródłowego.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

`AtlGetObjectSourceInterface` może podać identyfikator interfejsu domyślnego interfejsu źródłowego oraz identyfikatora LIBID i główne i pomocnicze numery wersji biblioteki typów opisującej ten interfejs.

> [!NOTE]
> Aby ta funkcja pomyślnie pobiera żądane informacje, obiekt reprezentowany przez *punkObj* musi implementować `IDispatch` (i zwracać informacje o typie za pomocą elementu), a `IDispatch::GetTypeInfo` także musi implementować albo `IProvideClassInfo2` `IPersist` . Informacje o typie dla interfejsu źródłowego muszą znajdować się w tej samej bibliotece typów co informacje o typie `IDispatch` .

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak można zdefiniować klasę ujścia zdarzeń, `CEasySink` która zmniejsza liczbę argumentów szablonu, które można przekazać do `IDispEventImpl` systemu operacyjnego. `EasyAdvise` i `EasyUnadvise` Użyj, `AtlGetObjectSourceInterface` Aby zainicjować członków [IDispEventImpl](../../atl/reference/idispeventimpl-class.md) przed wywołaniem [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) lub [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise).

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Makra kontroli złożonej](../../atl/reference/composite-control-macros.md)
