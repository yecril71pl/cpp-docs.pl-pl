---
title: Interfejs IAxWinAmbientDispatch
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatch
- ATLIFACE/ATL::IAxWinAmbientDispatch
- ATLIFACE/ATL::get_AllowContextMenu
- ATLIFACE/ATL::get_AllowShowUI
- ATLIFACE/ATL::get_AllowWindowlessActivation
- ATLIFACE/ATL::get_BackColor
- ATLIFACE/ATL::get_DisplayAsDefault
- ATLIFACE/ATL::get_DocHostDoubleClickFlags
- ATLIFACE/ATL::get_DocHostFlags
- ATLIFACE/ATL::get_Font
- ATLIFACE/ATL::get_ForeColor
- ATLIFACE/ATL::get_LocaleID
- ATLIFACE/ATL::get_MessageReflect
- ATLIFACE/ATL::get_OptionKeyPath
- ATLIFACE/ATL::get_ShowGrabHandles
- ATLIFACE/ATL::get_ShowHatching
- ATLIFACE/ATL::get_UserMode
- ATLIFACE/ATL::put_AllowContextMenu
- ATLIFACE/ATL::put_AllowShowUI
- ATLIFACE/ATL::put_AllowWindowlessActivation
- ATLIFACE/ATL::put_BackColor
- ATLIFACE/ATL::put_DisplayAsDefault
- ATLIFACE/ATL::put_DocHostDoubleClickFlags
- ATLIFACE/ATL::put_DocHostFlags
- ATLIFACE/ATL::put_Font
- ATLIFACE/ATL::put_ForeColor
- ATLIFACE/ATL::put_LocaleID
- ATLIFACE/ATL::put_MessageReflect
- ATLIFACE/ATL::put_OptionKeyPath
- ATLIFACE/ATL::put_UserMode
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
ms.openlocfilehash: 9b9557a76d133d81a07320f1a64482d17c955ef2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301600"
---
# <a name="iaxwinambientdispatch-interface"></a>Interfejs IAxWinAmbientDispatch

Ten interfejs zapewnia metody do określania właściwości kontrolki hostowanej lub kontenera.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|`AllowContextMenu` Właściwość określa, czy hostowanej formant może wyświetlić menu kontekstowe.|
|[get_AllowShowUI](#get_allowshowui)|`AllowShowUI` Właściwość określa, czy hostowanej formant może wyświetlić interfejs użytkownika.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|`AllowWindowlessActivation` Właściwość określa, czy kontener będzie zezwalał na aktywacji niepowiązanej z oknami.|
|[get_BackColor](#get_backcolor)|`BackColor` Właściwość określa kolor tła otoczenia kontenera.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault` jest zmieniono właściwość zapewnia kontrolę sprawdzić, czy jest domyślny formant.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|`DocHostDoubleClickFlags` Właściwości określa operację, które powinny zostać wykonane w odpowiedzi na dwukrotne kliknięcie.|
|[get_DocHostFlags](#get_dochostflags)|`DocHostFlags` Właściwość określa możliwości interfejsu użytkownika obiektu hosta.|
|[get_Font](#get_font)|`Font` Właściwości Określa czcionkę otoczenia kontenera.|
|[get_ForeColor](#get_forecolor)|`ForeColor` Właściwość określa kolor pierwszego planu otoczenia kontenera.|
|[get_LocaleID](#get_localeid)|`LocaleID` Właściwość określa identyfikator ustawień regionalnych otoczenia kontenera.|
|[get_MessageReflect](#get_messagereflect)|`MessageReflect` Zmieniono właściwość określa, czy kontener będzie odzwierciedlać wiadomości do obsługiwanego formantu.|
|[get_OptionKeyPath](#get_optionkeypath)|`OptionKeyPath` Właściwość określa ścieżkę klucza rejestru w celu ustawienia użytkownika.|
|[get_ShowGrabHandles](#get_showgrabhandles)|`ShowGrabHandles` Zmieniono właściwość zapewnia kontrolę dowiedzieć się, jeśli jego powinien być rysowany od samego za pomocą uchwytów.|
|[get_ShowHatching](#get_showhatching)|`ShowHatching` Właściwość otoczenia umożliwia formant Aby dowiedzieć się, jeśli jego powinien być rysowany od samego wyklutych.|
|[get_UserMode](#get_usermode)|`UserMode` Właściwość określa tryb otoczenia użytkownika kontenera.|
|[put_AllowContextMenu](#put_allowcontextmenu)|`AllowContextMenu` Właściwość określa, czy hostowanej formant może wyświetlić menu kontekstowe.|
|[put_AllowShowUI](#put_allowshowui)|`AllowShowUI` Właściwość określa, czy hostowanej formant może wyświetlić interfejs użytkownika.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|`AllowWindowlessActivation` Właściwość określa, czy kontener będzie zezwalał na aktywacji niepowiązanej z oknami.|
|[put_BackColor](#put_backcolor)|`BackColor` Właściwość określa kolor tła otoczenia kontenera.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault` jest zmieniono właściwość zapewnia kontrolę sprawdzić, czy jest domyślny formant.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|`DocHostDoubleClickFlags` Właściwości określa operację, które powinny zostać wykonane w odpowiedzi na dwukrotne kliknięcie.|
|[put_DocHostFlags](#put_dochostflags)|`DocHostFlags` Właściwość określa możliwości interfejsu użytkownika obiektu hosta.|
|[put_Font](#put_font)|`Font` Właściwości Określa czcionkę otoczenia kontenera.|
|[put_ForeColor](#put_forecolor)|`ForeColor` Właściwość określa kolor pierwszego planu otoczenia kontenera.|
|[put_LocaleID](#put_localeid)|`LocaleID` Właściwość określa identyfikator ustawień regionalnych otoczenia kontenera.|
|[put_MessageReflect](#put_messagereflect)|`MessageReflect` Zmieniono właściwość określa, czy kontener będzie odzwierciedlać wiadomości do obsługiwanego formantu.|
|[put_OptionKeyPath](#put_optionkeypath)|`OptionKeyPath` Właściwość określa ścieżkę klucza rejestru w celu ustawienia użytkownika.|
|[put_UserMode](#put_usermode)|`UserMode` Właściwość określa tryb otoczenia użytkownika kontenera.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest udostępniany przez ActiveX hostingu formantu ATL, obiekty. Wywołanie metody tego interfejsu, można ustawić właściwości otoczenia, która jest dostępna do sterowania hostowanej lub określić inne aspekty zachowania kontenera. Aby uzupełnić właściwości dostarczonych przez `IAxWinAmbientDispatch`, użyj [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).

[AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) spróbuje załadować informacji o typie o `IAxWinAmbientDispatch` i `IAxWinAmbientDispatchEx` z biblioteki typów, która zawiera kod.

Jeśli łączysz się ATL90.dll, **AXHost** zostaną załadowane informacje o typie z biblioteki typów w bibliotece DLL.

Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) Aby uzyskać więcej informacji.

## <a name="requirements"></a>Wymagania

Definicja ten interfejs jest dostępny w wielu formach, jak pokazano w poniższej tabeli.

|Typ definicji|Plik|
|---------------------|----------|
|IDL|atliface.IDL|
|Biblioteki typów|ATL.dll|
|C++|atliface.h (dołączone do dodatków ATLBase.h)|

##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu

`AllowContextMenu` Właściwość określa, czy hostowanej formant może wyświetlić menu kontekstowe.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Parametry

*pbAllowContextMenu*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako wartość domyślna tej właściwości.

##  <a name="get_allowshowui"></a>  IAxWinAmbientDispatch::get_AllowShowUI

`AllowShowUI` Właściwość określa, czy hostowanej formant może wyświetlić interfejs użytkownika.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Parametry

*pbAllowShowUI*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_FALSE, jako wartość domyślna tej właściwości.

##  <a name="get_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::get_AllowWindowlessActivation

`AllowWindowlessActivation` Właściwość określa, czy kontener będzie zezwalał na aktywacji niepowiązanej z oknami.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Parametry

*pbAllowWindowless*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako wartość domyślna tej właściwości.

##  <a name="get_backcolor"></a>  IAxWinAmbientDispatch::get_BackColor

`BackColor` Właściwość określa kolor tła otoczenia kontenera.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Parametry

*pclrBackground*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa COLOR_BTNFACE lub COLOR_WINDOW jako wartość domyślna tej właściwości (zależnie od tego, czy element nadrzędny okno hosta jest okno dialogowe, lub nie).

##  <a name="get_displayasdefault"></a>  IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault` jest zmieniono właściwość zapewnia kontrolę sprawdzić, czy jest domyślny formant.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*pbDisplayAsDefault*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_FALSE, jako wartość domyślna tej właściwości.

##  <a name="get_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

`DocHostDoubleClickFlags` Właściwości określa operację, które powinny zostać wykonane w odpowiedzi na dwukrotne kliknięcie.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parametry

*pdwDocHostDoubleClickFlags*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa DOCHOSTUIDBLCLK_DEFAULT jako wartość domyślna tej właściwości.

##  <a name="get_dochostflags"></a>  IAxWinAmbientDispatch::get_DocHostFlags

`DocHostFlags` Właściwość określa możliwości interfejsu użytkownika obiektu hosta.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Parametry

*pdwDocHostFlags*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa DOCHOSTUIFLAG_NO3DBORDER jako wartość domyślna tej właściwości.

##  <a name="get_font"></a>  IAxWinAmbientDispatch::get_Font

`Font` Właściwości Określa czcionkę otoczenia kontenera.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
[out] Adres `IFontDisp` wskaźnik interfejsu, używany do odbierania bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

W implementacji obiektu hosta ATL jest używana domyślna czcionka graficznego interfejsu użytkownika lub czcionki systemowej jako wartość domyślna tej właściwości.

##  <a name="get_forecolor"></a>  IAxWinAmbientDispatch::get_ForeColor

`ForeColor` Właściwość określa kolor pierwszego planu otoczenia kontenera.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Parametry

*pclrForeground*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa kolor tekstu w oknie system jako wartość domyślna tej właściwości.

##  <a name="get_localeid"></a>  IAxWinAmbientDispatch::get_LocaleID

`LocaleID` Właściwość określa identyfikator ustawień regionalnych otoczenia kontenera.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Parametry

*plcidLocaleID*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa użytkownika domyślnych ustawień regionalnych jako wartość domyślna tej właściwości.

Przy użyciu tej metody można wykryć otoczenia identyfikator LocalID, czyli identyfikator ustawień regionalnych programu formant jest używany w. Znając identyfikator ustawień regionalnych, możesz wywołać kod, aby załadować transkrypcji specyficzne dla ustawień regionalnych, tekst komunikatu o błędzie, i innych elementów z pliku zasobów lub satelitarnej biblioteki DLL.

##  <a name="get_messagereflect"></a>  IAxWinAmbientDispatch::get_MessageReflect

`MessageReflect` Zmieniono właściwość określa, czy kontener będzie odzwierciedlać wiadomości do obsługiwanego formantu.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Parametry

*pbMessageReflect*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako wartość domyślna tej właściwości.

##  <a name="get_optionkeypath"></a>  IAxWinAmbientDispatch::get_OptionKeyPath

`OptionKeyPath` Właściwość określa ścieżkę klucza rejestru w celu ustawienia użytkownika.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Parametry

*pbstrOptionKeyPath*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles

`ShowGrabHandles` Zmieniono właściwość zapewnia kontrolę dowiedzieć się, jeśli jego powinien być rysowany od samego za pomocą uchwytów.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Parametry

*pbShowGrabHandles*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL zawsze zwraca wartość VARIANT_FALSE jako wartość tej właściwości.

##  <a name="get_showhatching"></a>  IAxWinAmbientDispatch::get_ShowHatching

`ShowHatching` Właściwość otoczenia umożliwia formant Aby dowiedzieć się, jeśli jego powinien być rysowany od samego wyklutych.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Parametry

*pbShowHatching*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL zawsze zwraca wartość VARIANT_FALSE jako wartość tej właściwości.

##  <a name="get_usermode"></a>  IAxWinAmbientDispatch::get_UserMode

`UserMode` Właściwość określa tryb otoczenia użytkownika kontenera.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Parametry

*pbUserMode*<br/>
[out] Adres zmiennej, aby otrzymać bieżąca wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako wartość domyślna tej właściwości.

##  <a name="put_allowcontextmenu"></a>  IAxWinAmbientDispatch::put_AllowContextMenu

`AllowContextMenu` Właściwość określa, czy hostowanej formant może wyświetlić menu kontekstowe.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Parametry

*bAllowContextMenu*<br/>
[in] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako wartość domyślna tej właściwości.

##  <a name="put_allowshowui"></a>  IAxWinAmbientDispatch::put_AllowShowUI

`AllowShowUI` Właściwość określa, czy hostowanej formant może wyświetlić interfejs użytkownika.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Parametry

*bAllowShowUI*<br/>
[in] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_FALSE, jako wartość domyślna tej właściwości.

##  <a name="put_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::put_AllowWindowlessActivation

`AllowWindowlessActivation` Właściwość określa, czy kontener będzie zezwalał na aktywacji niepowiązanej z oknami.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Parametry

*bAllowWindowless*<br/>
[in] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako wartość domyślna tej właściwości.

##  <a name="put_backcolor"></a>  IAxWinAmbientDispatch::put_BackColor

`BackColor` Właściwość określa kolor tła otoczenia kontenera.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Parametry

*clrBackground*<br/>
[in] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa COLOR_BTNFACE lub COLOR_WINDOW jako wartość domyślna tej właściwości (zależnie od tego, czy element nadrzędny okno hosta jest okno dialogowe, lub nie).

##  <a name="put_displayasdefault"></a>  IAxWinAmbientDispatch::put_DisplayAsDefault

`DisplayAsDefault` jest zmieniono właściwość zapewnia kontrolę sprawdzić, czy jest domyślny formant.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*bDisplayAsDefault*<br/>
[in] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_FALSE, jako wartość domyślna tej właściwości.

##  <a name="put_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::put_DocHostDoubleClickFlags

`DocHostDoubleClickFlags` Właściwości określa operację, które powinny zostać wykonane w odpowiedzi na dwukrotne kliknięcie.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parametry

*dwDocHostDoubleClickFlags*<br/>
[in] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa DOCHOSTUIDBLCLK_DEFAULT jako wartość domyślna tej właściwości.

##  <a name="put_dochostflags"></a>  IAxWinAmbientDispatch::put_DocHostFlags

`DocHostFlags` Właściwość określa możliwości interfejsu użytkownika obiektu hosta.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Parametry

*dwDocHostFlags*<br/>
[in] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa DOCHOSTUIFLAG_NO3DBORDER jako wartość domyślna tej właściwości.

##  <a name="put_font"></a>  IAxWinAmbientDispatch::put_Font

`Font` Właściwości Określa czcionkę otoczenia kontenera.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
[in] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

W implementacji obiektu hosta ATL jest używana domyślna czcionka graficznego interfejsu użytkownika lub czcionki systemowej jako wartość domyślna tej właściwości.

##  <a name="put_forecolor"></a>  IAxWinAmbientDispatch::put_ForeColor

`ForeColor` Właściwość określa kolor pierwszego planu otoczenia kontenera.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Parametry

*clrForeground*<br/>
[in] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa kolor tekstu w oknie system jako wartość domyślna tej właściwości.

##  <a name="put_localeid"></a>  IAxWinAmbientDispatch::put_LocaleID

`LocaleID` Właściwość określa identyfikator ustawień regionalnych otoczenia kontenera.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Parametry

*lcidLocaleID*<br/>
[in] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa użytkownika domyślnych ustawień regionalnych jako wartość domyślna tej właściwości.

##  <a name="put_messagereflect"></a>  IAxWinAmbientDispatch::put_MessageReflect

`MessageReflect` Zmieniono właściwość określa, czy kontener będzie odzwierciedlać wiadomości do obsługiwanego formantu.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Parametry

*bMessageReflect*<br/>
[in] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako wartość domyślna tej właściwości.

##  <a name="put_optionkeypath"></a>  IAxWinAmbientDispatch::put_OptionKeyPath

`OptionKeyPath` Właściwość określa ścieżkę klucza rejestru w celu ustawienia użytkownika.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Parametry

*bstrOptionKeyPath*<br/>
[in] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode

`UserMode` Właściwość określa tryb otoczenia użytkownika kontenera.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Parametry

*bUserMode*<br/>
[in] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako wartość domyślna tej właściwości.

## <a name="see-also"></a>Zobacz także

[Interfejs IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[Interfejs IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
