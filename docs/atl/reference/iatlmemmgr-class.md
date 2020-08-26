---
title: Klasa IAtlMemMgr
ms.date: 11/04/2016
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
ms.openlocfilehash: a33414ec1c1b01742382150049f8e99f4a70ae34
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833429"
---
# <a name="iatlmemmgr-class"></a>Klasa IAtlMemMgr

Ta klasa reprezentuje interfejs Menedżera pamięci.

## <a name="syntax"></a>Składnia

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|Nazwa|Opis|
|-|-|
|[Alokacji](#allocate)|Wywołaj tę metodę, aby przydzielić blok pamięci.|
|[Bezpłatna](#free)|Wywołaj tę metodę, aby zwolnić blok pamięci.|
|[GetSize](#getsize)|Wywołaj tę metodę, aby pobrać rozmiar przydzielonych bloków pamięci.|
|[Ponowne przydzielenie](#reallocate)|Wywołaj tę metodę, aby ponownie przydzielić blok pamięci.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest implementowany przez [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md)lub [CWin32Heap](../../atl/reference/cwin32heap-class.md).

> [!NOTE]
> Lokalne i globalne funkcje sterty są wolniejsze niż inne funkcje zarządzania pamięcią i nie zapewniają jak wielu funkcji. W związku z tym nowe aplikacje powinny używać [funkcji sterty](/windows/win32/Memory/heap-functions). Są one dostępne w klasie [CWin32Heap](../../atl/reference/cwin32heap-class.md) .

## <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem. h

## <a name="iatlmemmgrallocate"></a><a name="allocate"></a> IAtlMemMgr:: Allocate

Wywołaj tę metodę, aby przydzielić blok pamięci.

```cpp
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Żądana liczba bajtów w nowym bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku nowo przydzielony blok pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie [IAtlMemMgr:: Free](#free) lub [IAtlMemMgr:: Reallocate](#reallocate) w celu zwolnienia pamięci przydzielonej przez tę metodę.

### <a name="example"></a>Przykład

Aby zapoznać się z przykładem, zobacz [Omówienie IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrfree"></a><a name="free"></a> IAtlMemMgr:: Free

Wywołaj tę metodę, aby zwolnić blok pamięci.

```cpp
void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
Wskaźnik do pamięci przydzielonej wcześniej przez ten Menedżer pamięci.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby zwolnić pamięć uzyskaną przez [IAtlMemMgr:: Allocate](#allocate) lub [IAtlMemMgr:: Reallocate](#reallocate).

### <a name="example"></a>Przykład

Aby zapoznać się z przykładem, zobacz [Omówienie IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrgetsize"></a><a name="getsize"></a> IAtlMemMgr:: GetSize

Wywołaj tę metodę, aby pobrać rozmiar przydzielonych bloków pamięci.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
Wskaźnik do pamięci przydzielonej wcześniej przez ten Menedżer pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar bloku pamięci w bajtach.

### <a name="example"></a>Przykład

Aby zapoznać się z przykładem, zobacz [Omówienie IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrreallocate"></a><a name="reallocate"></a> IAtlMemMgr:: Reallocate

Wywołaj tę metodę, aby ponownie przydzielić pamięć przydzieloną przez ten Menedżer pamięci.

```cpp
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
Wskaźnik do pamięci przydzielonej wcześniej przez ten Menedżer pamięci.

*nBytes*<br/>
Żądana liczba bajtów w nowym bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku nowo przydzielony blok pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie [IAtlMemMgr:: Free](#free) lub [IAtlMemMgr:: Reallocate](#reallocate) w celu zwolnienia pamięci przydzielonej przez tę metodę.

Koncepcyjnie ta metoda zwalnia istniejącą pamięć i przydziela nowy blok pamięci. W rzeczywistości istniejąca pamięć może zostać rozszerzona lub w inny sposób ponownie użyta.

### <a name="example"></a>Przykład

Aby zapoznać się z przykładem, zobacz [Omówienie IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

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

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a> IAxWinAmbientDispatchEx::SetAmbientDispatch

Ta metoda jest wywoływana w celu uzupełnienia domyślnego interfejsu właściwości otoczenia przy użyciu interfejsu zdefiniowanego przez użytkownika.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parametry

*pDispatch*<br/>
Wskaźnik do nowego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Gdy `SetAmbientDispatch` jest wywoływana za pomocą wskaźnika do nowego interfejsu, ten nowy interfejs zostanie użyty do wywołania wszelkich właściwości lub metod, do których żąda formant hostowany — Jeśli te właściwości nie są jeszcze udostępniane przez [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a> IAxWinHostWindow::AttachControl

Dołącza istniejący (i wcześniej zainicjowany) formant do obiektu hosta przy użyciu okna identyfikowanego przez *Właściwość HWND*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parametry

*pUnkControl*<br/>
podczas Wskaźnik do `IUnknown` interfejsu formantu, który ma zostać dołączony do obiektu hosta.

*Właściwość*<br/>
podczas Dojście do okna, które ma być używane na potrzeby hostingu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a> IAxWinHostWindow:: IsControl

Tworzy kontrolkę, inicjuje ją i hostuje w oknie identyfikowanym przez *Właściwość HWND*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parametry

*lpTricsData*<br/>
podczas Ciąg identyfikujący formant do utworzenia. Może to być identyfikator CLSID (musi zawierać nawiasy klamrowe), ProgID, URL lub nieprzetworzony kod HTML (poprzedzony przez **MSHTML:**).

*Właściwość*<br/>
podczas Dojście do okna, które ma być używane na potrzeby hostingu.

*pStream*<br/>
podczas Wskaźnik interfejsu dla strumienia zawierającego dane inicjujące dla kontrolki. Może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

To okno zostanie poddana podklasie obiektu hosta, który uwidacznia ten interfejs, tak aby komunikaty mogły być odzwierciedlone na kontrolce, a inne funkcje kontenera będą działać.

Wywołanie tej metody jest równoważne wywołaniu [IAxWinHostWindow:: CreateControlEx](#createcontrolex).

Aby utworzyć licencjonowany formant ActiveX, zobacz [IAxWinHostWindowLic::](#createcontrollicex)iscontroling.

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a> IAxWinHostWindow::CreateControlEx

Tworzy formant ActiveX, inicjuje go i hostuje w określonym oknie, podobnie jak [IAxWinHostWindow:: IsControl](#createcontrol).

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>Parametry

*lpTricsData*<br/>
podczas Ciąg identyfikujący formant do utworzenia. Może to być identyfikator CLSID (musi zawierać nawiasy klamrowe), ProgID, URL lub nieprzetworzony kod HTML (poprzedzony prefiksem **MSHTML:**).

*Właściwość*<br/>
podczas Dojście do okna, które ma być używane na potrzeby hostingu.

*pStream*<br/>
podczas Wskaźnik interfejsu dla strumienia zawierającego dane inicjujące dla kontrolki. Może mieć wartość NULL.

*ppUnk*<br/>
określoną Adres wskaźnika, który będzie otrzymywał `IUnknown` interfejs utworzonej kontrolki. Może mieć wartość NULL.

*riidAdvise*<br/>
podczas Identyfikator interfejsu interfejsu wychodzącego na zawartym obiekcie. Może być IID_NULL.

*punkAdvise*<br/>
podczas Wskaźnik do `IUnknown` interfejsu obiektu ujścia, który ma być połączony z punktem połączenia na zawartym obiekcie określonym przez `iidSink` .

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do `CreateControl` metody, `CreateControlEx` umożliwia również otrzymywanie wskaźnika interfejsu do nowo utworzonej kontrolki i Konfigurowanie ujścia zdarzeń do odbierania zdarzeń wyzwalanych przez formant.

Aby utworzyć licencjonowany formant ActiveX, zobacz [IAxWinHostWindowLic:: CreateControlLicEx](#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a> IAxWinHostWindow::QueryControl

Zwraca określony wskaźnik interfejsu dostarczony przez obsługiwaną kontrolę.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
podczas Identyfikator interfejsu na żądanym formancie.

*ppvObject*<br/>
określoną Adres wskaźnika, który będzie otrzymywał określony interfejs utworzonej kontrolki.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a> IAxWinHostWindow::SetExternalDispatch

Ustawia zewnętrzny dispinterface, który jest dostępny dla zawartych kontrolek za pomocą metody [IDocHostUIHandlerDispatch:: getexternal](../../atl/reference/idochostuihandlerdispatch-interface.md) .

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
podczas Wskaźnik do `IDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a> IAxWinHostWindow::SetExternalUIHandler

Wywołaj tę funkcję, aby ustawić zewnętrzny interfejs [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) dla `CAxWindow` obiektu.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
podczas Wskaźnik do `IDocHostUIHandlerDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana przez kontrolki (takie jak kontrolka przeglądarki sieci Web), które wysyła zapytanie do lokacji hosta dla `IDocHostUIHandlerDispatch` interfejsu.

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a> IAxWinHostWindowLic:: issterowane

Tworzy licencjonowaną kontrolę, inicjuje ją i hostuje w oknie identyfikowanym przez `hWnd` .

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrLic*<br/>
podczas BSTR, który zawiera klucz licencji dla kontrolki.

### <a name="remarks"></a>Uwagi

Aby uzyskać opis pozostałych parametrów i wartości zwracanej, zobacz [IAxWinHostWindow:: IsControl](#createcontrol) .

Wywołanie tej metody jest równoważne wywołaniu [IAxWinHostWindowLic:: CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Przykład

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego z programu `IAxWinHostWindowLic::CreateControlLic` .

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a> IAxWinHostWindowLic::CreateControlLicEx

Tworzy licencjonowany formant ActiveX, inicjuje go i hostuje w określonym oknie, podobnie jak [IAxWinHostWindow:: IsControl](#createcontrol).

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrLic*<br/>
podczas BSTR, który zawiera klucz licencji dla kontrolki.

### <a name="remarks"></a>Uwagi

Aby uzyskać opis pozostałych parametrów i wartości zwracanej, zobacz [IAxWinHostWindow:: CreateControlEx](#createcontrolex) .

### <a name="example"></a>Przykład

Zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego z programu `IAxWinHostWindowLic::CreateControlLicEx` .

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
