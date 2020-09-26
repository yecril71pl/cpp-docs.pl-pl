---
title: IAxWinAmbientDispatch, interfejs
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
ms.openlocfilehash: dbd682451ca5499aef4b16b3b51feba8411bdd12
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352963"
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch, interfejs

Ten interfejs zapewnia metody określania właściwości hostowanej kontrolki lub kontenera.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|Nazwa|Opis|
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|`AllowContextMenu`Właściwość określa, czy formant hostowany może wyświetlać własne menu kontekstowe.|
|[get_AllowShowUI](#get_allowshowui)|`AllowShowUI`Właściwość określa, czy formant hostowany może wyświetlać własny interfejs użytkownika.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|`AllowWindowlessActivation`Właściwość określa, czy kontener będzie zezwalać na aktywację bez okien.|
|[get_BackColor](#get_backcolor)|`BackColor`Właściwość określa kolor tła otoczenia kontenera.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault` jest właściwością otoczenia, która pozwala formantowi sprawdzić, czy jest to formant domyślny.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|`DocHostDoubleClickFlags`Właściwość określa operację, która powinna zostać wykonana w odpowiedzi na dwukrotne kliknięcie.|
|[get_DocHostFlags](#get_dochostflags)|`DocHostFlags`Właściwość określa możliwości interfejsu użytkownika obiektu hosta.|
|[get_Font](#get_font)|`Font`Właściwość określa otaczającą czcionkę kontenera.|
|[get_ForeColor](#get_forecolor)|`ForeColor`Właściwość określa kolor pierwszego planu kontenera.|
|[get_LocaleID](#get_localeid)|`LocaleID`Właściwość określa identyfikator ustawień regionalnych otoczenia kontenera.|
|[get_MessageReflect](#get_messagereflect)|`MessageReflect`Właściwość otoczenia określa, czy kontener będzie odzwierciedlać komunikaty do hostowanej kontrolki.|
|[get_OptionKeyPath](#get_optionkeypath)|`OptionKeyPath`Właściwość określa ścieżkę klucza rejestru do ustawień użytkownika.|
|[get_ShowGrabHandles](#get_showgrabhandles)|`ShowGrabHandles`Właściwość otoczenia pozwala formantowi sprawdzić, czy powinien być rysowany z uchwytami.|
|[get_ShowHatching](#get_showhatching)|`ShowHatching`Właściwość otoczenia pozwala formantowi sprawdzić, czy powinien być rysowany z kreską.|
|[get_UserMode](#get_usermode)|`UserMode`Właściwość określa tryb otoczenia użytkownika kontenera.|
|[put_AllowContextMenu](#put_allowcontextmenu)|`AllowContextMenu`Właściwość określa, czy formant hostowany może wyświetlać własne menu kontekstowe.|
|[put_AllowShowUI](#put_allowshowui)|`AllowShowUI`Właściwość określa, czy formant hostowany może wyświetlać własny interfejs użytkownika.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|`AllowWindowlessActivation`Właściwość określa, czy kontener będzie zezwalać na aktywację bez okien.|
|[put_BackColor](#put_backcolor)|`BackColor`Właściwość określa kolor tła otoczenia kontenera.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault` jest właściwością otoczenia, która pozwala formantowi sprawdzić, czy jest to formant domyślny.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|`DocHostDoubleClickFlags`Właściwość określa operację, która powinna zostać wykonana w odpowiedzi na dwukrotne kliknięcie.|
|[put_DocHostFlags](#put_dochostflags)|`DocHostFlags`Właściwość określa możliwości interfejsu użytkownika obiektu hosta.|
|[put_Font](#put_font)|`Font`Właściwość określa otaczającą czcionkę kontenera.|
|[put_ForeColor](#put_forecolor)|`ForeColor`Właściwość określa kolor pierwszego planu kontenera.|
|[put_LocaleID](#put_localeid)|`LocaleID`Właściwość określa identyfikator ustawień regionalnych otoczenia kontenera.|
|[put_MessageReflect](#put_messagereflect)|`MessageReflect`Właściwość otoczenia określa, czy kontener będzie odzwierciedlać komunikaty do hostowanej kontrolki.|
|[put_OptionKeyPath](#put_optionkeypath)|`OptionKeyPath`Właściwość określa ścieżkę klucza rejestru do ustawień użytkownika.|
|[put_UserMode](#put_usermode)|`UserMode`Właściwość określa tryb otoczenia użytkownika kontenera.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest udostępniany przez obiekty obsługujące kontrolki ActiveX ATL. Wywołaj metody tego interfejsu, aby ustawić właściwości otoczenia dostępne dla hostowanej kontrolki lub określić inne aspekty zachowania kontenera. Aby uzupełnić właściwości dostarczone przez `IAxWinAmbientDispatch` , użyj [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).

<xref:System.Windows.Forms.AxHost> podejmie próbę załadowania informacji o typie `IAxWinAmbientDispatch` i `IAxWinAmbientDispatchEx` z biblioteki typów, która zawiera kod.

Jeśli łączysz się z ATL90.dll, **AxHost** załaduje informacje o typie z biblioteki typów w bibliotece DLL.

Aby uzyskać więcej informacji, zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) .

## <a name="requirements"></a>Wymagania

Definicja tego interfejsu jest dostępna w wielu formularzach, jak pokazano w poniższej tabeli.

|Typ definicji|Plik|
|---------------------|----------|
|IDL|atliface. idl|
|Biblioteka typów|ATL.dll|
|C++|atliface. h (również zawarte w ATLBase. h)|

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a> IAxWinAmbientDispatch:: get_AllowContextMenu

`AllowContextMenu`Właściwość określa, czy formant hostowany może wyświetlać własne menu kontekstowe.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Parametry

*pbAllowContextMenu*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a> IAxWinAmbientDispatch:: get_AllowShowUI

`AllowShowUI`Właściwość określa, czy formant hostowany może wyświetlać własny interfejs użytkownika.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Parametry

*pbAllowShowUI*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_FALSE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a> IAxWinAmbientDispatch:: get_AllowWindowlessActivation

`AllowWindowlessActivation`Właściwość określa, czy kontener będzie zezwalać na aktywację bez okien.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Parametry

*pbAllowWindowless*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a> IAxWinAmbientDispatch:: get_BackColor

`BackColor`Właściwość określa kolor tła otoczenia kontenera.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Parametry

*pclrBackground*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa COLOR_BTNFACE lub COLOR_WINDOW jako wartości domyślnej tej właściwości (w zależności od tego, czy element nadrzędny okna hosta jest oknem dialogowym, czy nie).

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a> IAxWinAmbientDispatch:: get_DisplayAsDefault

`DisplayAsDefault` jest właściwością otoczenia, która pozwala formantowi sprawdzić, czy jest to formant domyślny.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*pbDisplayAsDefault*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_FALSE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a> IAxWinAmbientDispatch:: get_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`Właściwość określa operację, która powinna zostać wykonana w odpowiedzi na dwukrotne kliknięcie.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parametry

*pdwDocHostDoubleClickFlags*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa DOCHOSTUIDBLCLK_DEFAULT jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a> IAxWinAmbientDispatch:: get_DocHostFlags

`DocHostFlags`Właściwość określa możliwości interfejsu użytkownika obiektu hosta.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Parametry

*pdwDocHostFlags*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa DOCHOSTUIFLAG_NO3DBORDER jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a> IAxWinAmbientDispatch:: get_Font

`Font`Właściwość określa otaczającą czcionkę kontenera.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
określoną Adres `IFontDisp` wskaźnika interfejsu używany do odbierania bieżącej wartości tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa domyślnej czcionki graficznego interfejsu użytkownika lub czcionki systemowej jako wartości domyślnej tej właściwości.

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a> IAxWinAmbientDispatch:: get_ForeColor

`ForeColor`Właściwość określa kolor pierwszego planu kontenera.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Parametry

*pclrForeground*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa koloru tekstu okna systemowego jako wartości domyślnej tej właściwości.

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a> IAxWinAmbientDispatch:: get_LocaleID

`LocaleID`Właściwość określa identyfikator ustawień regionalnych otoczenia kontenera.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Parametry

*plcidLocaleID*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa domyślnych ustawień regionalnych użytkownika jako wartości domyślnej tej właściwości.

Za pomocą tej metody można odkryć LocalID otoczenia, czyli LocaleID programu, w którym jest używana kontrolka. Po poznaniu LocaleID można wywołać kod w celu załadowania podpisów właściwych dla ustawień regionalnych, tekstu komunikatu o błędzie i tak dalej z pliku zasobów lub satelitarnej biblioteki DLL.

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a> IAxWinAmbientDispatch:: get_MessageReflect

`MessageReflect`Właściwość otoczenia określa, czy kontener będzie odzwierciedlać komunikaty do hostowanej kontrolki.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Parametry

*pbMessageReflect*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a> IAxWinAmbientDispatch:: get_OptionKeyPath

`OptionKeyPath`Właściwość określa ścieżkę klucza rejestru do ustawień użytkownika.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Parametry

*pbstrOptionKeyPath*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a> IAxWinAmbientDispatch:: get_ShowGrabHandles

`ShowGrabHandles`Właściwość otoczenia pozwala formantowi sprawdzić, czy powinien być rysowany z uchwytami.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Parametry

*pbShowGrabHandles*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL zawsze zwraca VARIANT_FALSE jako wartość tej właściwości.

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a> IAxWinAmbientDispatch:: get_ShowHatching

`ShowHatching`Właściwość otoczenia pozwala formantowi sprawdzić, czy powinien być rysowany z kreską.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Parametry

*pbShowHatching*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL zawsze zwraca VARIANT_FALSE jako wartość tej właściwości.

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a> IAxWinAmbientDispatch:: get_UserMode

`UserMode`Właściwość określa tryb otoczenia użytkownika kontenera.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Parametry

*pbUserMode*<br/>
określoną Adres zmiennej, która ma otrzymać bieżącą wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a> IAxWinAmbientDispatch::p ut_AllowContextMenu

`AllowContextMenu`Właściwość określa, czy formant hostowany może wyświetlać własne menu kontekstowe.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Parametry

*bAllowContextMenu*<br/>
podczas Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a> IAxWinAmbientDispatch::p ut_AllowShowUI

`AllowShowUI`Właściwość określa, czy formant hostowany może wyświetlać własny interfejs użytkownika.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Parametry

*bAllowShowUI*<br/>
podczas Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_FALSE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a> IAxWinAmbientDispatch::p ut_AllowWindowlessActivation

`AllowWindowlessActivation`Właściwość określa, czy kontener będzie zezwalać na aktywację bez okien.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Parametry

*bAllowWindowless*<br/>
podczas Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a> IAxWinAmbientDispatch::p ut_BackColor

`BackColor`Właściwość określa kolor tła otoczenia kontenera.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Parametry

*clrBackground*<br/>
podczas Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa COLOR_BTNFACE lub COLOR_WINDOW jako wartości domyślnej tej właściwości (w zależności od tego, czy element nadrzędny okna hosta jest oknem dialogowym, czy nie).

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a> IAxWinAmbientDispatch::p ut_DisplayAsDefault

`DisplayAsDefault` jest właściwością otoczenia, która pozwala formantowi sprawdzić, czy jest to formant domyślny.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*bDisplayAsDefault*<br/>
podczas Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_FALSE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a> IAxWinAmbientDispatch::p ut_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`Właściwość określa operację, która powinna zostać wykonana w odpowiedzi na dwukrotne kliknięcie.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parametry

*dwDocHostDoubleClickFlags*<br/>
podczas Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa DOCHOSTUIDBLCLK_DEFAULT jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a> IAxWinAmbientDispatch::p ut_DocHostFlags

`DocHostFlags`Właściwość określa możliwości interfejsu użytkownika obiektu hosta.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Parametry

*dwDocHostFlags*<br/>
podczas Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa DOCHOSTUIFLAG_NO3DBORDER jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a> IAxWinAmbientDispatch::p ut_Font

`Font`Właściwość określa otaczającą czcionkę kontenera.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
podczas Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa domyślnej czcionki graficznego interfejsu użytkownika lub czcionki systemowej jako wartości domyślnej tej właściwości.

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a> IAxWinAmbientDispatch::p ut_ForeColor

`ForeColor`Właściwość określa kolor pierwszego planu kontenera.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Parametry

*clrForeground*<br/>
podczas Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa koloru tekstu okna systemowego jako wartości domyślnej tej właściwości.

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a> IAxWinAmbientDispatch::p ut_LocaleID

`LocaleID`Właściwość określa identyfikator ustawień regionalnych otoczenia kontenera.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Parametry

*lcidLocaleID*<br/>
podczas Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa domyślnych ustawień regionalnych użytkownika jako wartości domyślnej tej właściwości.

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a> IAxWinAmbientDispatch::p ut_MessageReflect

`MessageReflect`Właściwość otoczenia określa, czy kontener będzie odzwierciedlać komunikaty do hostowanej kontrolki.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Parametry

*bMessageReflect*<br/>
podczas Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a> IAxWinAmbientDispatch::p ut_OptionKeyPath

`OptionKeyPath`Właściwość określa ścieżkę klucza rejestru do ustawień użytkownika.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Parametry

*bstrOptionKeyPath*<br/>
podczas Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a> IAxWinAmbientDispatch::p ut_UserMode

`UserMode`Właściwość określa tryb otoczenia użytkownika kontenera.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Parametry

*bUserMode*<br/>
podczas Nowa wartość tej właściwości.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Implementacja obiektu hosta ATL używa VARIANT_TRUE jako domyślnej wartości tej właściwości.

## <a name="see-also"></a>Zobacz też

[IAxWinAmbientDispatchEx, interfejs](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[IAxWinHostWindow, interfejs](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
