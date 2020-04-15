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
ms.openlocfilehash: 6a4f5322d957b1e978bd123db3b4796be6b300da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330008"
---
# <a name="iaxwinambientdispatch-interface"></a>Interfejs IAxWinAmbientDispatch

Ten interfejs zawiera metody określania właściwości hostowanego formantu lub kontenera.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|Właściwość `AllowContextMenu` określa, czy hostowany formant może wyświetlać własne menu kontekstowe.|
|[get_AllowShowUI](#get_allowshowui)|Właściwość `AllowShowUI` określa, czy hostowany formant może wyświetlać własny interfejs użytkownika.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|Właściwość `AllowWindowlessActivation` określa, czy kontener pozwoli na aktywację bez okien.|
|[get_BackColor](#get_backcolor)|Właściwość `BackColor` określa kolor otoczenia tła kontenera.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault`jest właściwość otoczenia, która pozwala formantu, aby dowiedzieć się, czy jest to formant domyślny.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|Właściwość `DocHostDoubleClickFlags` określa operację, która powinna mieć miejsce w odpowiedzi na podwójne kliknięcie.|
|[get_DocHostFlags](#get_dochostflags)|Właściwość `DocHostFlags` określa możliwości interfejsu użytkownika obiektu hosta.|
|[get_Font](#get_font)|Właściwość `Font` określa czcionkę otoczenia kontenera.|
|[get_ForeColor](#get_forecolor)|Właściwość `ForeColor` określa otaczający kolor pierwszego planu kontenera.|
|[get_LocaleID](#get_localeid)|Właściwość `LocaleID` określa identyfikator ustawień regionalnych otoczenia kontenera.|
|[get_MessageReflect](#get_messagereflect)|Właściwość otoczenia `MessageReflect` określa, czy kontener będzie odzwierciedlać komunikaty do hostowanego formantu.|
|[get_OptionKeyPath](#get_optionkeypath)|Właściwość `OptionKeyPath` określa ścieżkę klucza rejestru do ustawień użytkownika.|
|[get_ShowGrabHandles](#get_showgrabhandles)|Właściwość otoczenia `ShowGrabHandles` pozwala formantu, aby dowiedzieć się, czy należy rysować się za pomocą uchwytów.|
|[get_ShowHatching](#get_showhatching)|Właściwość otoczenia `ShowHatching` pozwala formantu, aby dowiedzieć się, czy należy narysować się kreskować.|
|[get_UserMode](#get_usermode)|Właściwość `UserMode` określa tryb użytkownika otoczenia kontenera.|
|[put_AllowContextMenu](#put_allowcontextmenu)|Właściwość `AllowContextMenu` określa, czy hostowany formant może wyświetlać własne menu kontekstowe.|
|[put_AllowShowUI](#put_allowshowui)|Właściwość `AllowShowUI` określa, czy hostowany formant może wyświetlać własny interfejs użytkownika.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|Właściwość `AllowWindowlessActivation` określa, czy kontener pozwoli na aktywację bez okien.|
|[put_BackColor](#put_backcolor)|Właściwość `BackColor` określa kolor otoczenia tła kontenera.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault`jest właściwość otoczenia, która pozwala formantu, aby dowiedzieć się, czy jest to formant domyślny.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|Właściwość `DocHostDoubleClickFlags` określa operację, która powinna mieć miejsce w odpowiedzi na podwójne kliknięcie.|
|[put_DocHostFlags](#put_dochostflags)|Właściwość `DocHostFlags` określa możliwości interfejsu użytkownika obiektu hosta.|
|[put_Font](#put_font)|Właściwość `Font` określa czcionkę otoczenia kontenera.|
|[put_ForeColor](#put_forecolor)|Właściwość `ForeColor` określa otaczający kolor pierwszego planu kontenera.|
|[put_LocaleID](#put_localeid)|Właściwość `LocaleID` określa identyfikator ustawień regionalnych otoczenia kontenera.|
|[put_MessageReflect](#put_messagereflect)|Właściwość otoczenia `MessageReflect` określa, czy kontener będzie odzwierciedlać komunikaty do hostowanego formantu.|
|[put_OptionKeyPath](#put_optionkeypath)|Właściwość `OptionKeyPath` określa ścieżkę klucza rejestru do ustawień użytkownika.|
|[put_UserMode](#put_usermode)|Właściwość `UserMode` określa tryb użytkownika otoczenia kontenera.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest narażony przez obiekty hostingowe activex formantu ATL. Wywołanie metod w tym interfejsie, aby ustawić właściwości otoczenia dostępne dla hostowanego formantu lub określić inne aspekty zachowania kontenera. Aby uzupełnić właściwości `IAxWinAmbientDispatch`dostarczone przez program [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).

<xref:System.Windows.Forms.AxHost>spróbuje załadować informacje `IAxWinAmbientDispatch` `IAxWinAmbientDispatchEx` o typie o i z typelib, który zawiera kod.

Jeśli łączysz się z plikum ATL90.dll, **AXHost** załaduje informacje o typie z typelib w pliku DLL.

Aby uzyskać więcej informacji, zobacz [Hostowanie formantów ActiveX za pomocą AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) a.

## <a name="requirements"></a>Wymagania

Definicja tego interfejsu jest dostępna w wielu formach, jak pokazano w poniższej tabeli.

|Typ definicji|Plik|
|---------------------|----------|
|Idl|atliface.idl|
|Biblioteka typów|Plik ATL.dll|
|C++|atliface.h (również w ATLBase.h)|

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a>IAxWinAmbientDispatch::get_AllowContextMenu

Właściwość `AllowContextMenu` określa, czy hostowany formant może wyświetlać własne menu kontekstowe.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Parametry

*pbAllowContextMenu*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a>IAxWinAmbientDispatch::get_AllowShowUI

Właściwość `AllowShowUI` określa, czy hostowany formant może wyświetlać własny interfejs użytkownika.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Parametry

*pbAllowShowUI*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_FALSE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a>IAxWinAmbientDispatch::get_AllowWindowlessActivation

Właściwość `AllowWindowlessActivation` określa, czy kontener pozwoli na aktywację bez okien.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Parametry

*pbAllowWindowless*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a>IAxWinAmbientDispatch::get_BackColor

Właściwość `BackColor` określa kolor otoczenia tła kontenera.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Parametry

*pclrBackground*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa COLOR_BTNFACE lub COLOR_WINDOW jako domyślnej wartości tej właściwości (w zależności od tego, czy element nadrzędny okna hosta jest dialogowym, czy nie).

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a>IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault`jest właściwość otoczenia, która pozwala formantu, aby dowiedzieć się, czy jest to formant domyślny.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*pbDisplayAsDefault*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_FALSE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

Właściwość `DocHostDoubleClickFlags` określa operację, która powinna mieć miejsce w odpowiedzi na podwójne kliknięcie.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parametry

*pdwDocHostDoubleClickFlags*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa DOCHOSTUIDBLCLK_DEFAULT jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a>IAxWinAmbientDispatch::get_DocHostFlags

Właściwość `DocHostFlags` określa możliwości interfejsu użytkownika obiektu hosta.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Parametry

*pdwDocHostSlags*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa DOCHOSTUIFLAG_NO3DBORDER jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a>IAxWinAmbientDispatch::get_Font

Właściwość `Font` określa czcionkę otoczenia kontenera.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Parametry

*pFont (pFont)*<br/>
[na zewnątrz] Adres wskaźnika `IFontDisp` interfejsu używanego do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa domyślnej czcionki GUI lub czcionki systemowej jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a>IAxWinAmbientDispatch::get_ForeColor

Właściwość `ForeColor` określa otaczający kolor pierwszego planu kontenera.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Parametry

*pclrForeground*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa koloru tekstu okna systemowego jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a>IAxWinAmbientDispatch::get_LocaleID

Właściwość `LocaleID` określa identyfikator ustawień regionalnych otoczenia kontenera.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Parametry

*plcidLocaleID*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa domyślnych ustawień regionalnych użytkownika jako domyślnej wartości tej właściwości.

Za pomocą tej metody można odnajdyć Ambient LocalID, czyli LocaleID programu, w który jest używany formant. Po poznaniu localeID, można wywołać kod, aby załadować podpisy specyficzne dla ustawień regionalnych, tekst komunikatu o błędzie i tak dalej z pliku zasobów lub biblioteki DLL satelitarnej.

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a>IAxWinAmbientDispatch::get_MessageReflect

Właściwość otoczenia `MessageReflect` określa, czy kontener będzie odzwierciedlać komunikaty do hostowanego formantu.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Parametry

*pbMessageReflect*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a>IAxWinAmbientDispatch::get_OptionKeyPath

Właściwość `OptionKeyPath` określa ścieżkę klucza rejestru do ustawień użytkownika.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Parametry

*pbstrOptionKeyPath*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a>IAxWinAmbientDispatch::get_ShowGrabHandles

Właściwość otoczenia `ShowGrabHandles` pozwala formantu, aby dowiedzieć się, czy należy rysować się za pomocą uchwytów.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Parametry

*pbShowGrabHandle*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL zawsze zwraca VARIANT_FALSE jako wartość tej właściwości.

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a>IAxWinAmbientDispatch::get_ShowHatching

Właściwość otoczenia `ShowHatching` pozwala formantu, aby dowiedzieć się, czy należy narysować się kreskować.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Parametry

*pbShowHatching*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL zawsze zwraca VARIANT_FALSE jako wartość tej właściwości.

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a>IAxWinAmbientDispatch::get_UserMode

Właściwość `UserMode` określa tryb użytkownika otoczenia kontenera.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Parametry

*pbUżytnikmode*<br/>
[na zewnątrz] Adres zmiennej do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a>IAxWinAmbientDispatch::put_AllowContextMenu

Właściwość `AllowContextMenu` określa, czy hostowany formant może wyświetlać własne menu kontekstowe.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Parametry

*bAllowContextMenu*<br/>
[w] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a>IAxWinAmbientDispatch::put_AllowShowUI

Właściwość `AllowShowUI` określa, czy hostowany formant może wyświetlać własny interfejs użytkownika.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Parametry

*bAllowShowUI*<br/>
[w] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_FALSE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a>IAxWinAmbientDispatch::put_AllowWindowlessActivation

Właściwość `AllowWindowlessActivation` określa, czy kontener pozwoli na aktywację bez okien.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Parametry

*bAllowWindowless*<br/>
[w] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a>IAxWinAmbientDispatch::put_BackColor

Właściwość `BackColor` określa kolor otoczenia tła kontenera.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Parametry

*clrBackground (ziemia powrotna)*<br/>
[w] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa COLOR_BTNFACE lub COLOR_WINDOW jako domyślnej wartości tej właściwości (w zależności od tego, czy element nadrzędny okna hosta jest dialogowym, czy nie).

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a>IAxWinAmbientDispatch::put_DisplayAsDefault

`DisplayAsDefault`jest właściwość otoczenia, która pozwala formantu, aby dowiedzieć się, czy jest to formant domyślny.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*bDisplayAsDefault*<br/>
[w] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_FALSE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::put_DocHostDoubleClickFlags

Właściwość `DocHostDoubleClickFlags` określa operację, która powinna mieć miejsce w odpowiedzi na podwójne kliknięcie.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parametry

*dwDocHostDoubleClickSlagi*<br/>
[w] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa DOCHOSTUIDBLCLK_DEFAULT jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a>IAxWinAmbientDispatch::put_DocHostFlags

Właściwość `DocHostFlags` określa możliwości interfejsu użytkownika obiektu hosta.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Parametry

*dwDocHostSlags*<br/>
[w] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa DOCHOSTUIFLAG_NO3DBORDER jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a>IAxWinAmbientDispatch::put_Font

Właściwość `Font` określa czcionkę otoczenia kontenera.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont (pFont)*<br/>
[w] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa domyślnej czcionki GUI lub czcionki systemowej jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a>IAxWinAmbientDispatch::put_ForeColor

Właściwość `ForeColor` określa otaczający kolor pierwszego planu kontenera.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Parametry

*clrForeground (na terenie*<br/>
[w] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa koloru tekstu okna systemowego jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a>IAxWinAmbientDispatch::put_LocaleID

Właściwość `LocaleID` określa identyfikator ustawień regionalnych otoczenia kontenera.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Parametry

*lcidLocaleID (lcidLocaleID)*<br/>
[w] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa domyślnych ustawień regionalnych użytkownika jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a>IAxWinAmbientDispatch::put_MessageReflect

Właściwość otoczenia `MessageReflect` określa, czy kontener będzie odzwierciedlać komunikaty do hostowanego formantu.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Parametry

*bMessageReflect*<br/>
[w] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a>IAxWinAmbientDispatch::put_OptionKeyPath

Właściwość `OptionKeyPath` określa ścieżkę klucza rejestru do ustawień użytkownika.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Parametry

*ścieżka bstrOptionKeyPath*<br/>
[w] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a>IAxWinAmbientDispatch::put_UserMode

Właściwość `UserMode` określa tryb użytkownika otoczenia kontenera.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Parametry

*BMode dla typuuser*<br/>
[w] Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="see-also"></a>Zobacz też

[Interfejs IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[Interfejs IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost (AtlAxGetHost)](composite-control-global-functions.md#atlaxgethost)
