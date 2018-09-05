---
title: Funkcje globalne kontrolek złożonych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91de6c09128acd3ef1a008437ae418b96b45ef66
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762895"
---
# <a name="composite-control-global-functions"></a>Funkcje globalne kontrolek złożonych

Te funkcje zapewniają obsługę do utworzenia okien dialogowych i tworzenie, hostowanie i licencjonowanie kontrolek ActiveX.

> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|Tworzy modalne okno dialogowe z szablonu okna dialogowego dostarczonego przez użytkownika. Okno dialogowe wynikowy może zawierać kontrolki ActiveX.|
|[AtlAxCreateDialog](#atlaxcreatedialog)|Tworzy niemodalne okno dialogowe z szablonu okna dialogowego dostarczonego przez użytkownika. Okno dialogowe wynikowy może zawierać kontrolki ActiveX.|
|[AtlAxCreateControl](#atlaxcreatecontrol)|Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie.|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie oraz pobiera wskaźnika interfejsu (lub wskaźniki) z formantu.|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie.|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie oraz pobiera wskaźnika interfejsu (lub wskaźniki) z formantu.|
|[AtlAxAttachControl](#atlaxattachcontrol)|Dołącza wcześniej utworzony formant do określonego okna.|
|[AtlAxGetHost](#atlaxgethost)|Używany do uzyskiwania bezpośredni wskaźnik interfejsu do kontenera dla określonego okna (jeśli istnieje), biorąc pod uwagę jego uchwyt.|
|[AtlAxGetControl](#atlaxgetcontrol)|Używany do uzyskiwania bezpośredni wskaźnik interfejsu do formantu zawartego wewnątrz określonego okna (jeśli istnieje), biorąc pod uwagę jego uchwyt.|
|[AtlSetChildSite](#atlsetchildsite)|Inicjuje `IUnknown` lokacji podrzędnych.|
|[AtlAxWinInit](#atlaxwininit)|Inicjuje kod hostingu AxWin obiektów.|
|[AtlAxWinTerm](#atlaxwinterm)|Deinicjuje kod hostingu AxWin obiektów.|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Zwraca informacje o domyślnym interfejsie źródła obiektu.|  

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlhost.h  

##  <a name="atlaxdialogbox"></a>  AtlAxDialogBox

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

*hInstance*  
[in] Identyfikuje wystąpienia modułu, którego pliku wykonywalnego zawiera szablonu okna dialogowego.

*lpTemplateName*  
[in] Identyfikuje szablonu okna dialogowego. Ten parametr jest wskaźnik do ciągu zakończonego znakiem null, który określa nazwę szablonu okna dialogowego lub wartość całkowitą, która określa identyfikator zasobu szablonu okna dialogowego. Jeśli parametr określa identyfikator zasobu, jego word wyższego rzędu musi mieć wartość zero, a jego word niskiego rzędu musi zawierać identyfikator. Możesz użyć [MAKEINTRESOURCE](https://msdn.microsoft.com/library/windows/desktop/ms648029) makra w celu utworzenia tej wartości.

*hWndParent*  
[in] Identyfikuje okna, który jest właścicielem okno dialogowe.

*lpDialogProc*  
[in] Wskazuje procedury okno dialogowe. Aby uzyskać więcej informacji na temat procedury okno dialogowe, zobacz [DialogProc](https://msdn.microsoft.com/library/windows/desktop/ms645469).

*dwInitParam*  
[in] Określa wartość do przekazania do okna dialogowego w *lParam* parametr / / Złap wiadomości.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Do użycia `AtlAxDialogBox` z szablonu okna dialogowego, który zawiera formant ActiveX, Określ prawidłowy ciąg identyfikatora CLSID, APPID lub adresu URL jako *tekstu* pole **kontroli** części zasobu okna dialogowego wraz z " AtlAxWin80 "jako *Nazwa klasy* pola w ramach tej samej sekcji. Następujące pokazuje, jakie prawidłową **kontroli** sekcja może wyglądać tak jak:

```  
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,  
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100  
```

Aby uzyskać więcej informacji na temat edytowania skryptów zasobów, zobacz [porady: otwieranie pliku skryptu zasobu w formacie tekstowym](../../windows/how-to-open-a-resource-script-file-in-text-format.md). Aby uzyskać więcej informacji na temat instrukcji definicji zasobu kontroli, zobacz [wspólne parametry sterujące](/windows/desktop/menurc/common-control-parameters) w ramach zestawu Windows SDK *: SDK Tools*.

Aby uzyskać więcej informacji o oknach dialogowych, ogólnie rzecz biorąc, zobacz [DialogBox](/windows/desktop/api/winuser/nf-winuser-dialogboxa) i [CreateDialogParam](/windows/desktop/api/winuser/nf-winuser-createdialogparama) w zestawie Windows SDK.

##  <a name="atlaxcreatedialog"></a>  AtlAxCreateDialog

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

*hInstance*  
[in] Identyfikuje wystąpienia modułu, którego pliku wykonywalnego zawiera szablonu okna dialogowego.

*lpTemplateName*  
[in] Identyfikuje szablonu okna dialogowego. Ten parametr jest wskaźnik do ciągu zakończonego znakiem null, który określa nazwę szablonu okna dialogowego lub wartość całkowitą, która określa identyfikator zasobu szablonu okna dialogowego. Jeśli parametr określa identyfikator zasobu, jego word wyższego rzędu musi mieć wartość zero, a jego word niskiego rzędu musi zawierać identyfikator. Możesz użyć [MAKEINTRESOURCE](https://msdn.microsoft.com/library/windows/desktop/ms648029) makra w celu utworzenia tej wartości.

*hWndParent*  
[in] Identyfikuje okna, który jest właścicielem okno dialogowe.

*lpDialogProc*  
[in] Wskazuje procedury okno dialogowe. Aby uzyskać więcej informacji na temat procedury okno dialogowe, zobacz [DialogProc](https://msdn.microsoft.com/library/windows/desktop/ms645469).

*dwInitParam*  
[in] Określa wartość do przekazania do okna dialogowego w *lParam* parametr / / Złap wiadomości.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Okno dialogowe wynikowy może zawierać kontrolki ActiveX.

Zobacz [CreateDialog](/windows/desktop/api/winuser/nf-winuser-createdialoga) i [CreateDialogParam](/windows/desktop/api/winuser/nf-winuser-createdialogparama) w Windows SDK.

##  <a name="atlaxcreatecontrol"></a>  AtlAxCreateControl

Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie.

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*lpszName*  
Wskaźnik do ciągu do przekazania do formantu. Musi być sformatowany w jednym z następujących sposobów:

- Identyfikator ProgID takich jak "MSCAL. Calendar.7 "

- CLSID, takie jak "{8E27C92B-1264-101C-8A2F-040224009C02}"

- Adres URL, takich jak "http://www.microsoft.com"

- Odwołanie do aktywnego dokumentu, takie jak "file://\\\Documents\MyDoc.doc"

- Fragment kodu HTML, takich jak "MSHTML:\<HTML >\<treści > jest to wiersz tekstu\</BODY >\<polecenia >"

   > [!NOTE]
   > "MSHTML:" musi poprzedzać fragment kodu HTML, dzięki czemu jest wyznaczony jako strumień MSHTML.

*hWnd*  
[in] Obsługa do kontrolki zostanie dołączony do okna.

*pStream*  
[in] Wskaźnik do strumienia, który służy do inicjowania właściwości formantu. Może mieć wartości NULL.

*ppUnkContainer*  
[out] Adres wskaźnika, który będzie otrzymywał `IUnknown` kontenera. Może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Ta funkcja globalna daje ten sam wynik co wywołanie metody [AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*, *hWnd*, *pStream*, NULL, NULL, WARTOŚĆ NULL, NULL);.

Aby utworzyć licencjonowany formant ActiveX, zobacz [AtlAxCreateControlLic](#atlaxcreatecontrollic).

##  <a name="atlaxcreatecontrolex"></a>  AtlAxCreateControlEx

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

*lpszName*  
Wskaźnik do ciągu do przekazania do formantu. Musi być sformatowany w jednym z następujących sposobów:

- Identyfikator ProgID takich jak "MSCAL. Calendar.7 "

- CLSID, takie jak "{8E27C92B-1264-101C-8A2F-040224009C02}"

- Adres URL, takich jak "http://www.microsoft.com"

- Odwołanie do aktywnego dokumentu, takie jak "file://\\\Documents\MyDoc.doc"

- Fragment kodu HTML, takich jak "MSHTML:\<HTML >\<treści > jest to wiersz tekstu\</BODY >\<polecenia >"

   > [!NOTE]
   > "MSHTML:" musi poprzedzać fragment kodu HTML, dzięki czemu jest wyznaczony jako strumień MSHTML.

*hWnd*  
[in] Obsługa do kontrolki zostanie dołączony do okna.

*pStream*  
[in] Wskaźnik do strumienia, który służy do inicjowania właściwości formantu. Może mieć wartości NULL.

*ppUnkContainer*  
[out] Adres wskaźnika, który będzie otrzymywał `IUnknown` kontenera. Może mieć wartości NULL.

*ppUnkControl*  
[out] Adres wskaźnika, który będzie otrzymywał `IUnknown` utworzonego formantu. Może mieć wartości NULL.

*iidSink*  
Identyfikator interfejsu interfejsu wychodzącego w zawartego w nim obiektu.

*punkSink*  
Wskaźnik do `IUnknown` interfejs obiektu sink do podłączenia do punktu połączenia z określonym przez *iidSink* zamkniętego obiektu po pomyślnym utworzeniu zawartego w nim obiektu.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

`AtlAxCreateControlEx` jest podobny do [AtlAxCreateControl](#atlaxcreatecontrol) , ale pozwala również na wyświetlony wskaźnik interfejsu do nowo utworzonego formantu i skonfigurować obiekt sink zdarzenia, aby odbierać zdarzenia wywoływane przez formant.

Aby utworzyć licencjonowany formant ActiveX, zobacz [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).

##  <a name="atlaxcreatecontrollic"></a>  AtlAxCreateControlLic

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

*lpszName*  
Wskaźnik do ciągu do przekazania do formantu. Musi być sformatowany w jednym z następujących sposobów:

- Identyfikator ProgID takich jak "MSCAL. Calendar.7 "

- CLSID, takie jak "{8E27C92B-1264-101C-8A2F-040224009C02}"

- Adres URL, takich jak "http://www.microsoft.com"

- Odwołanie do aktywnego dokumentu, takie jak "file://\\\Documents\MyDoc.doc"

- Fragment kodu HTML, takich jak "MSHTML:\<HTML >\<treści > jest to wiersz tekstu\</BODY >\<polecenia >"

   > [!NOTE]
   > "MSHTML:" musi poprzedzać fragment kodu HTML, dzięki czemu jest wyznaczony jako strumień MSHTML.

*hWnd*  
Obsługa do kontrolki zostanie dołączony do okna.

*pStream*  
Wskaźnik do strumienia, który służy do inicjowania właściwości formantu. Może mieć wartości NULL.

*ppUnkContainer*  
Adres wskaźnika, który będzie otrzymywał `IUnknown` kontenera. Może mieć wartości NULL.

*bstrLic*  
BSTR, zawierający licencji dla formantu.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="example"></a>Przykład

Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) przykład sposobu użycia `AtlAxCreateControlLic`.

##  <a name="atlaxcreatecontrollicex"></a>  AtlAxCreateControlLicEx

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

*lpszName*  
Wskaźnik do ciągu do przekazania do formantu. Musi być sformatowany w jednym z następujących sposobów:

- Identyfikator ProgID takich jak "MSCAL. Calendar.7 "

- CLSID, takie jak "{8E27C92B-1264-101C-8A2F-040224009C02}"

- Adres URL, takich jak "http://www.microsoft.com"

- Odwołanie do aktywnego dokumentu, takie jak "file://\\\Documents\MyDoc.doc"

- Fragment kodu HTML, takich jak "MSHTML:\<HTML >\<treści > jest to wiersz tekstu\</BODY >\<polecenia >"

   > [!NOTE]
   > "MSHTML:" musi poprzedzać fragment kodu HTML, dzięki czemu jest wyznaczony jako strumień MSHTML.

*hWnd*  
Obsługa do kontrolki zostanie dołączony do okna.

*pStream*  
Wskaźnik do strumienia, który służy do inicjowania właściwości formantu. Może mieć wartości NULL.

*ppUnkContainer*  
Adres wskaźnika, który będzie otrzymywał `IUnknown` kontenera. Może mieć wartości NULL.

*ppUnkControl*  
[out] Adres wskaźnika, który będzie otrzymywał `IUnknown` utworzonego formantu. Może mieć wartości NULL.

*iidSink*  
Identyfikator interfejsu interfejsu wychodzącego w zawartego w nim obiektu.

*punkSink*  
Wskaźnik do `IUnknown` interfejs obiektu sink do podłączenia do punktu połączenia z określonym przez *iidSink* zamkniętego obiektu po pomyślnym utworzeniu zawartego w nim obiektu.

*bstrLic*  
BSTR, zawierający licencji dla formantu.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

`AtlAxCreateControlLicEx` jest podobny do [AtlAxCreateControlLic](#atlaxcreatecontrollic) , ale pozwala również na wyświetlony wskaźnik interfejsu do nowo utworzonego formantu i skonfigurować obiekt sink zdarzenia, aby odbierać zdarzenia wywoływane przez formant.

### <a name="example"></a>Przykład

Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) przykład sposobu użycia `AtlAxCreateControlLicEx`.

##  <a name="atlaxattachcontrol"></a>  AtlAxAttachControl

Dołącza wcześniej utworzony formant do określonego okna.

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parametry

*pControl*  
[in] Wskaźnik do `IUnknown` formantu.

*hWnd*  
[in] Dojście do okna, które będą obsługiwać formant.

*ppUnkContainer*  
[out] Wskaźnik do wskaźnika do `IUnknown` obiektu kontenera.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Użyj [AtlAxCreateControlEx](#atlaxcreatecontrolex) i [AtlAxCreateControl](#atlaxcreatecontrol) Aby jednocześnie utworzyć i dołączyć kontrolki.

> [!NOTE]
>  Dołączany obiekt kontrolki musi zostać prawidłowo zainicjowany przed wywołaniem `AtlAxAttachControl`.

##  <a name="atlaxgethost"></a>  AtlAxGetHost

Uzyskuje bezpośredni wskaźnik interfejsu do kontenera dla określonego okna (o ile istnieje), biorąc pod uwagę jego uchwyt.

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parametry

*h*  
[in] Dojście do okna, który jest hostem formantu.

*strony*  
[out] `IUnknown` Kontenera kontrolki.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="atlaxgetcontrol"></a>  AtlAxGetControl

Uzyskuje bezpośredni wskaźnik interfejsu do formantu zawartego wewnątrz określonego okna, biorąc pod uwagę jego uchwyt.

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parametry

*h*  
[in] Dojście do okna, który jest hostem formantu.

*strony*  
[out] `IUnknown` Kontrolki hostowany.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

##  <a name="atlsetchildsite"></a>  AtlSetChildSite

Wywołaj tę funkcję, aby ustawić lokalizację obiektu podrzędnego do `IUnknown` obiektu nadrzędnego.

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>Parametry

*punkChild*  
[in] Wskaźnik do `IUnknown` interfejsu elementu podrzędnego.

*punkParent*  
[in] Wskaźnik do `IUnknown` interfejsu elementu nadrzędnego.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="atlaxwininit"></a>  AtlAxWinInit

Ta funkcja inicjuje kod hostingu, rejestrując formantu ATL **"AtlAxWin80"** i **"AtlAxWinLic80"** klasy okien, oraz kilka niestandardowych komunikatów okien.

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli inicjowanie kod hostingu formantu powiodła się. w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja musi być wywołana przed rozpoczęciem korzystania z formantu ATL, hostowanie interfejsu API. Po wywołaniu tej funkcji **"AtlAxWin"** klasy okna może służyć w wywołaniach [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) lub [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa), zgodnie z opisem w zestawie Windows SDK.  

##  <a name="atlaxwinterm"></a>  AtlAxWinTerm

Ta funkcja deinicjuje kod hostingu wyrejestrowując formantu ATL **"AtlAxWin80"** i **"AtlAxWinLic80"** klasy okna.

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Ta funkcja po prostu wywołuje widok [UnregisterClass](https://msdn.microsoft.com/library/windows/desktop/ms644899) zgodnie z opisem w zestawie Windows SDK.

Wywołaj tę funkcję, aby wyczyścić po zniszczeniu wszystkich istniejących okien hosta, jeśli wywołano [klasy AtlAxWinInit](#atlaxwininit) nie są potrzebne do utworzenia hosta systemu windows. Jeśli nie chcesz wywołać tę funkcję, klasę okna będzie można wyrejestrować automatycznie, gdy proces zakończy się.

##  <a name="atlgetobjectsourceinterface"></a>  AtlGetObjectSourceInterface

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

*punkObj*  
[in] Wskaźnik do obiektu, dla którego ma zostać zwrócone informacje.

*plibid*  
[out] Wskaźnik do identyfikatora LIBID biblioteki typów z definicją interfejs źródłowy.

*piid*  
[out] Wskaźnik do interfejsu identyfikator obiektu domyślnym interfejsie źródła.

*pdwMajor*  
[out] Wskaźnik do główny numer wersji biblioteki typów z definicją interfejs źródłowy.

*pdwMinor*  
[out] Wskaźnik do pomocniczy numer wersji biblioteki typów z definicją interfejs źródłowy.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

`AtlGetObjectSourceInterface` można udostępnić z Identyfikatorem domyślnym interfejsie źródła, wraz z LIBID i główne i pomocnicze numery wersji biblioteki typów, opisujący tego interfejsu.

> [!NOTE]
>  Dla tej funkcji można pomyślnie pobrać żądanych informacji obiekt reprezentowany przez *punkObj* musi implementować `IDispatch` (i zwracają informacje o typie za pośrednictwem `IDispatch::GetTypeInfo`) oraz musi implementować też albo `IProvideClassInfo2` lub `IPersist`. Informacje o typie dla interfejs źródłowy musi należeć do tej samej biblioteki typów jako informacji o typie `IDispatch`.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak można zdefiniować klasę obiektu sink zdarzenia `CEasySink`, która zmniejsza liczbę argumentów szablonu, które można przekazać do `IDispEventImpl` do podstawy systemu od zera. `EasyAdvise` i `EasyUnadvise` użyj `AtlGetObjectSourceInterface` zainicjować [IDispEventImpl](../../atl/reference/idispeventimpl-class.md) członków przed wywołaniem [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) lub [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise).

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)   
[Makra kontrolek złożonych](../../atl/reference/composite-control-macros.md)
