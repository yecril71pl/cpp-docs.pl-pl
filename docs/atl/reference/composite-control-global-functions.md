---
title: "Funkcje globalne formantu złożonego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords: composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d5a062ea9477df9db026c75bc775df804ed86da4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="composite-control-global-functions"></a>Funkcje globalne złożonych kontrolek
Funkcje te zapewniają obsługę tworzenia okna dialogowe, a także do tworzenia, obsługi i licencjonowanie formantów ActiveX.  
  
> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
|||  
|-|-|  
|[AtlAxDialogBox](#atlaxdialogbox)|Tworzy modalne okno dialogowe z szablonu okna dialogowego dostarczonego przez użytkownika. Okno dialogowe wynikowy może zawierać formantów ActiveX.|  
|[AtlAxCreateDialog](#atlaxcreatedialog)|Tworzy niemodalne okno dialogowe z szablonu okna dialogowego dostarczonego przez użytkownika. Okno dialogowe wynikowy może zawierać formantów ActiveX.|  
|[AtlAxCreateControl](#atlaxcreatecontrol)|Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie.|  
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Tworzy formantu ActiveX, inicjowane znajduje się w określonym oknie i pobiera wskaźnika interfejsu (lub wskaźniki) z formantu.|  
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie.|  
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Tworzy licencjonowanego formantu ActiveX, inicjowane znajduje się w określonym oknie i pobiera wskaźnika interfejsu (lub wskaźniki) z formantu.|  
|[AtlAxAttachControl](#atlaxattachcontrol)|Dołącza wcześniej utworzony formant do określonego okna.|  
|[AtlAxGetHost](#atlaxgethost)|Używany do uzyskania bezpośredniego interfejsu wskaźnik do kontenera w ramach określonego okna (jeśli istnieje), podane uchwytu.|  
|[AtlAxGetControl](#atlaxgetcontrol)|Używany do uzyskania bezpośredniego interfejsu wskaźnik do sterowania znajdująca się wewnątrz określonego okna (jeśli istnieje), podane uchwytu.|  
|[AtlSetChildSite](#atlsetchildsite)|Inicjuje **IUnknown** lokacji podrzędnych.|  
|[AtlAxWinInit](#atlaxwininit)|Inicjuje hostingu kod AxWin obiektów.|  
|[AtlAxWinTerm](#atlaxwinterm)|Uninitializes AxWin obiekty kod hostingu.|  
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Zwraca informacje na temat domyślnego interfejsu źródłowego obiektu.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlhost.h  

##  <a name="atlaxdialogbox"></a>AtlAxDialogBox  
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
 `hInstance`  
 [in] Identyfikuje wystąpienia modułu, którego pliku wykonywalnego zawiera szablon okno dialogowe.  
  
 `lpTemplateName`  
 [in] Identyfikuje szablon — okno dialogowe. Ten parametr jest wskaźnik do ciąg znaków zakończony znakiem null, który określa nazwę szablonu — okno dialogowe lub wartość całkowitą, która określa identyfikator zasobu szablon okno dialogowe. Jeśli parametr określa identyfikator zasobu, jego word znaczących musi być równa zero i jego znaczącymi bitami wyraz musi zawierać identyfikator. Można użyć [MAKEINTRESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms648029) makra w celu utworzenia tej wartości.  
  
 `hWndParent`  
 [in] Identyfikuje okna, który jest właścicielem okna dialogowego.  
  
 `lpDialogProc`  
 [in] Wskazuje procedury — okno dialogowe. Aby uzyskać więcej informacji na temat procedury — okno dialogowe, zobacz [DialogProc](http://msdn.microsoft.com/library/windows/desktop/ms645469).  
  
 `dwInitParam`  
 [in] Określa wartość do przekazania do okna dialogowego w **lParam** parametr **WM_INITDIALOG** wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Aby użyć **AtlAxDialogBox** z szablonu okna dialogowego, który zawiera kontrolki ActiveX, Określ prawidłowy **CLSID**, **APPID** lub ciągu adresu URL jako *tekst* pole **kontroli** sekcji zasobu okna dialogowego, wraz z "AtlAxWin80" jako *Nazwa klasy* pole w tej samej sekcji. Następujące pokazuje, jakie prawidłowy **kontroli** sekcji może wyglądać tak:  
  
```  
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,  
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100  
```  
  
 Aby uzyskać więcej informacji na edycji skryptów zasobów, zobacz [porady: otwieranie pliku skryptu zasobu w formacie tekstowym](../../windows/how-to-open-a-resource-script-file-in-text-format.md). Uzyskać więcej informacji o instrukcji sterowania definicji zasobu, zobacz [typowych parametrów sterujących](http://msdn.microsoft.com/library/windows/desktop/aa380902) w obszarze zestaw Windows SDK*: narzędzia zestawu SDK*.  
  
 Więcej informacji o oknach dialogowych ogólnie, można znaleźć w [DialogBox](http://msdn.microsoft.com/library/windows/desktop/ms645452) i [CreateDialogParam](http://msdn.microsoft.com/library/windows/desktop/ms645445) w zestawie Windows SDK.  
  
##  <a name="atlaxcreatedialog"></a>AtlAxCreateDialog  
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
 `hInstance`  
 [in] Identyfikuje wystąpienia modułu, którego pliku wykonywalnego zawiera szablon okno dialogowe.  
  
 `lpTemplateName`  
 [in] Identyfikuje szablon — okno dialogowe. Ten parametr jest wskaźnik do ciąg znaków zakończony znakiem null, który określa nazwę szablonu — okno dialogowe lub wartość całkowitą, która określa identyfikator zasobu szablon okno dialogowe. Jeśli parametr określa identyfikator zasobu, jego word znaczących musi być równa zero i jego znaczącymi bitami wyraz musi zawierać identyfikator. Można użyć [MAKEINTRESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms648029) makra w celu utworzenia tej wartości.  
  
 `hWndParent`  
 [in] Identyfikuje okna, który jest właścicielem okna dialogowego.  
  
 `lpDialogProc`  
 [in] Wskazuje procedury — okno dialogowe. Aby uzyskać więcej informacji na temat procedury — okno dialogowe, zobacz [DialogProc](http://msdn.microsoft.com/library/windows/desktop/ms645469).  
  
 `dwInitParam`  
 [in] Określa wartość do przekazania do okna dialogowego w **lParam** parametr **WM_INITDIALOG** wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Okno dialogowe wynikowy może zawierać formantów ActiveX.  
  
 Zobacz [CreateDialog](http://msdn.microsoft.com/library/windows/desktop/ms645434) i [CreateDialogParam](http://msdn.microsoft.com/library/windows/desktop/ms645445) w systemie Windows SDK.  
  
##  <a name="atlaxcreatecontrol"></a>AtlAxCreateControl  
 Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie.  
  

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Wskaźnik do parametry do przekazania do formantu. Musi być sformatowany w jednym z następujących sposobów:  
  
-   ProgID takie jak "MSCAL. Calendar.7 "  
  
-   Identyfikatora CLSID, takie jak "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adres URL, takie jak "http://www.microsoft.com"  
  
-   Odwołanie do aktywnego dokumentu, takie jak "file://\\\Documents\MyDoc.doc"  
  
-   Fragment kodu HTML, takie jak "MSHTML:\<HTML >\<treści > to jest wiersza tekstu\</BODY >\<polecenia >"  
  
    > [!NOTE]
    >  "MSHTML:" musi występować przed fragment kodu HTML, dzięki czemu jest wyznaczony jako strumień MSHTML.  
  
 `hWnd`  
 [in] Dojście do okna formantu zostanie dołączona do.  
  
 `pStream`  
 [in] Wskaźnik do strumienia, który służy do inicjowania właściwości formantu. Może być **NULL**.  
  
 `ppUnkContainer`  
 [out] Adres wskaźnika, który będzie otrzymywał **IUnknown** kontenera. Może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja globalna daje to samo co wywołanie [AtlAxCreateControlEx](#atlaxcreatecontrolex)( `lpszName` **,** `hWnd` **,** `pStream` **, NULL, NULL, NULL, NULL** );.  
  
 Aby utworzyć licencjonowanego formantu ActiveX, zobacz [AtlAxCreateControlLic](#atlaxcreatecontrollic).  
  
##  <a name="atlaxcreatecontrolex"></a>AtlAxCreateControlEx  
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
 `lpszName`  
 Wskaźnik do parametry do przekazania do formantu. Musi być sformatowany w jednym z następujących sposobów:  
  
-   ProgID takie jak "MSCAL. Calendar.7 "  
  
-   Identyfikatora CLSID, takie jak "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adres URL, takie jak "http://www.microsoft.com"  
  
-   Odwołanie do aktywnego dokumentu, takie jak "file://\\\Documents\MyDoc.doc"  
  
-   Fragment kodu HTML, takie jak "MSHTML:\<HTML >\<treści > to jest wiersza tekstu\</BODY >\<polecenia >"  
  
    > [!NOTE]
    >  "MSHTML:" musi występować przed fragment kodu HTML, dzięki czemu jest wyznaczony jako strumień MSHTML.  
  
 `hWnd`  
 [in] Dojście do okna formantu zostanie dołączona do.  
  
 `pStream`  
 [in] Wskaźnik do strumienia, który służy do inicjowania właściwości formantu. Może być **NULL**.  
  
 `ppUnkContainer`  
 [out] Adres wskaźnika, który będzie otrzymywał **IUnknown** kontenera. Może być **NULL**.  
  
 `ppUnkControl`  
 [out] Adres wskaźnika, który będzie otrzymywał **IUnknown** utworzony formantu. Może być **NULL**.  
  
 `iidSink`  
 Identyfikator interfejsu interfejs wychodzących w zawartego w nim obiektu.  
  
 *punkSink*  
 Wskaźnik do **IUnknown** interfejsu połączenia z punktem połączenia z określonym przez obiekt sink `iidSink` zawartych w niej obiektu po pomyślnym utworzeniu zawartego w nim obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 `AtlAxCreateControlEx`przypomina [AtlAxCreateControl](#atlaxcreatecontrol) , ale umożliwia również otrzymywać wskaźnik interfejsu do sterowania nowo utworzony i skonfigurowany obiekt sink zdarzenia do odbierania zdarzenia wywoływane przez formant.  
  
 Aby utworzyć licencjonowanego formantu ActiveX, zobacz [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).  
  
##  <a name="atlaxcreatecontrollic"></a>AtlAxCreateControlLic  
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
 `lpszName`  
 Wskaźnik do parametry do przekazania do formantu. Musi być sformatowany w jednym z następujących sposobów:  
  
-   ProgID takie jak "MSCAL. Calendar.7 "  
  
-   Identyfikatora CLSID, takie jak "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adres URL, takie jak "http://www.microsoft.com"  
  
-   Odwołanie do aktywnego dokumentu, takie jak "file://\\\Documents\MyDoc.doc"  
  
-   Fragment kodu HTML, takie jak "MSHTML:\<HTML >\<treści > to jest wiersza tekstu\</BODY >\<polecenia >"  
  
    > [!NOTE]
    >  "MSHTML:" musi występować przed fragment kodu HTML, dzięki czemu jest wyznaczony jako strumień MSHTML.  
  
 `hWnd`  
 Dojście do okna formantu zostanie dołączona do.  
  
 `pStream`  
 Wskaźnik do strumienia, który służy do inicjowania właściwości formantu. Może być **NULL**.  
  
 `ppUnkContainer`  
 Adres wskaźnika, który będzie otrzymywał **IUnknown** kontenera. Może być **NULL**.  
  
 `bstrLic`  
 BSTR, zawierający licencji dla formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="example"></a>Przykład  
 Zobacz [Hosting AXHost za pomocą biblioteki ATL programu ActiveX formanty](../../atl/hosting-activex-controls-using-atl-axhost.md) przykładowy sposób użycia `AtlAxCreateControlLic`.  
  
##  <a name="atlaxcreatecontrollicex"></a>AtlAxCreateControlLicEx  
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
 `lpszName`  
 Wskaźnik do parametry do przekazania do formantu. Musi być sformatowany w jednym z następujących sposobów:  
  
-   ProgID takie jak "MSCAL. Calendar.7 "  
  
-   Identyfikatora CLSID, takie jak "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Adres URL, takie jak "http://www.microsoft.com"  
  
-   Odwołanie do aktywnego dokumentu, takie jak "file://\\\Documents\MyDoc.doc"  
  
-   Fragment kodu HTML, takie jak "MSHTML:\<HTML >\<treści > to jest wiersza tekstu\</BODY >\<polecenia >"  
  
    > [!NOTE]
    >  "MSHTML:" musi występować przed fragment kodu HTML, dzięki czemu jest wyznaczony jako strumień MSHTML.  
  
 `hWnd`  
 Dojście do okna formantu zostanie dołączona do.  
  
 `pStream`  
 Wskaźnik do strumienia, który służy do inicjowania właściwości formantu. Może być **NULL**.  
  
 `ppUnkContainer`  
 Adres wskaźnika, który będzie otrzymywał **IUnknown** kontenera. Może być **NULL**.  
  
 `ppUnkControl`  
 [out] Adres wskaźnika, który będzie otrzymywał **IUnknown** utworzony formantu. Może być **NULL**.  
  
 `iidSink`  
 Identyfikator interfejsu interfejs wychodzących w zawartego w nim obiektu.  
  
 *punkSink*  
 Wskaźnik do **IUnknown** interfejsu połączenia z punktem połączenia z określonym przez obiekt sink `iidSink` zawartych w niej obiektu po pomyślnym utworzeniu zawartego w nim obiektu.  
  
 `bstrLic`  
 BSTR, zawierający licencji dla formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 `AtlAxCreateControlLicEx`przypomina [AtlAxCreateControlLic](#atlaxcreatecontrollic) , ale umożliwia również otrzymywać wskaźnik interfejsu do sterowania nowo utworzony i skonfigurowany obiekt sink zdarzenia do odbierania zdarzenia wywoływane przez formant.  
  
### <a name="example"></a>Przykład  
 Zobacz [Hosting AXHost za pomocą biblioteki ATL programu ActiveX formanty](../../atl/hosting-activex-controls-using-atl-axhost.md) przykładowy sposób użycia `AtlAxCreateControlLicEx`.  
  
##  <a name="atlaxattachcontrol"></a>AtlAxAttachControl  
 Dołącza wcześniej utworzony formant do określonego okna.  
  
```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>Parametry  
 `pControl`  
 [in] Wskaźnik do **IUnknown** formantu.  
  
 `hWnd`  
 [in] Dojście do okna, który będzie obsługiwał formantu.  
  
 `ppUnkContainer`  
 [out] Wskaźnik na wskaźnik do **IUnknown** obiektu kontenera.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [AtlAxCreateControlEx](#atlaxcreatecontrolex) i [AtlAxCreateControl](#atlaxcreatecontrol) jednocześnie Utwórz i Dołącz formantu.  
  
> [!NOTE]
>  Dołączany obiekt formantu musi być poprawnie zainicjowana przed wywołaniem `AtlAxAttachControl`.  
  
##  <a name="atlaxgethost"></a>AtlAxGetHost  
 Uzyskuje bezpośredni wskaźnik interfejsu do kontenera dla określonego okna (o ile istnieje), biorąc pod uwagę jego uchwyt.  
  
```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `h`  
 [in] Dojście do okna, które obsługuje formantu.  
  
 `pp`  
 [out] **IUnknown** formantu kontenera.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="atlaxgetcontrol"></a>AtlAxGetControl  
 Uzyskuje bezpośredni wskaźnik interfejsu do formantu zawartego wewnątrz określonego okna, biorąc pod uwagę jego uchwyt.  
  
```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `h`  
 [in] Dojście do okna, które obsługuje formantu.  
  
 `pp`  
 [out] **IUnknown** formantu obsługiwane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
##  <a name="atlsetchildsite"></a>AtlSetChildSite  
 Wywołanie tej funkcji można ustawić lokacji obiekt podrzędny, aby **IUnknown** obiektu nadrzędnego.  
  
```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```  
  
### <a name="parameters"></a>Parametry  
 *punkChild*  
 [in] Wskaźnik do **IUnknown** interfejsu podrzędnego.  
  
 `punkParent`  
 [in] Wskaźnik do **IUnknown** interfejsu elementu nadrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
##  <a name="atlaxwininit"></a>AtlAxWinInit  
 Ta funkcja inicjuje formantu ATL przez kod hostowania rejestrując **"AtlAxWin80"** i **"AtlAxWinLic80"** klasy okien oraz kilka niestandardowych komunikatów okien.  
  
```
ATLAPI_(BOOL) AtlAxWinInit();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli inicjowanie kontrolki kod hostowania zakończyło się pomyślnie; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja musi zostać wywołana przed za pomocą formantu ATL hosting interfejsu API. Po wywołaniu tej funkcji **"AtlAxWin"** okna klasa może być używana w wywołaniach [właściwości CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) lub [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680), zgodnie z opisem w zestawie Windows SDK.  

##  <a name="atlaxwinterm"></a>AtlAxWinTerm  
 Ta funkcja uninitializes formantu ATL przez kod hostowania wyrejestrowując **"AtlAxWin80"** i **"AtlAxWinLic80"** klasy okien.  
  
```
inline BOOL AtlAxWinTerm();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca **TRUE**.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest po prostu wywołuje [UnregisterClass](http://msdn.microsoft.com/library/windows/desktop/ms644899) zgodnie z opisem w zestawie Windows SDK.  
  
 Wywołanie tej funkcji, aby wyczyścić po wszystkich istniejących windows hosta zostały zniszczone Jeśli wywołujesz [AtlAxWinInit](#atlaxwininit) i nie będzie konieczne utworzenie hosta z systemem windows. Nie można wywołać tej funkcji, klasę okna zostanie wyrejestrowane automatycznie gdy zakończenie procesu.  
  
##  <a name="atlgetobjectsourceinterface"></a>AtlGetObjectSourceInterface  
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
 `punkObj`  
 [in] Wskaźnik do obiektu, dla którego ma zostać zwrócone informacje.  
  
 `plibid`  
 [out] Wskaźnik do identyfikatora LIBID biblioteki typów z definicją interfejsu źródłowego.  
  
 `piid`  
 [out] Wskaźnik do Identyfikatora interfejsu interfejs źródłowy domyślnego obiektu.  
  
 *pdwMajor*  
 [out] Wskaźnik do głównego numeru wersji biblioteki typów z definicją interfejsu źródłowego.  
  
 *pdwMinor*  
 [out] Wskaźnik do podrzędny numer wersji biblioteki typów z definicją interfejsu źródłowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 `AtlGetObjectSourceInterface`można podać użytkownik o identyfikatorze interfejsu domyślnego interfejsu źródłowego, wraz z identyfikatora LIBID i główne i pomocnicze numery wersji biblioteki typów opisujący ten interfejs.  
  
> [!NOTE]
>  Dla tej funkcji można pomyślnie pobrać żądanych informacji obiektu reprezentowanego przez `punkObj` musi implementować `IDispatch` (i zwracają informacje o typie za pośrednictwem **IDispatch::GetTypeInfo**) oraz musi także Implementowanie albo `IProvideClassInfo2` lub `IPersist`. Informacje dotyczące interfejsu źródłowego musi należeć do tej samej biblioteki typów jako informacji o typie `IDispatch`.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak można zdefiniować klasę obiektu sink zdarzenia `CEasySink`, która ogranicza liczbę argumentów szablonu, które można przekazać do `IDispEventImpl` do essentials systemu od zera. `EasyAdvise`i `EasyUnadvise` użyj `AtlGetObjectSourceInterface` zainicjować [IDispEventImpl](../../atl/reference/idispeventimpl-class.md) członków przed wywołaniem [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) lub [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise).  
  
 [!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)   
 [Makra kontrolek złożonych](../../atl/reference/composite-control-macros.md)
