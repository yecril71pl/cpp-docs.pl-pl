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
ms.openlocfilehash: fcecf716e9d865b1b8590a733216576e0da4c2fb
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746003"
---
# <a name="iatlmemmgr-class"></a>Klasa IAtlMemMgr

Ta klasa reprezentuje interfejs do menedżera pamięci.

## <a name="syntax"></a>Składnia

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Przydzielić](#allocate)|Wywołanie tej metody, aby przydzielić blok pamięci.|
|[Bezpłatna](#free)|Wywołanie tej metody, aby zwolnić blok pamięci.|
|[GetSize](#getsize)|Wywołanie tej metody, aby pobrać rozmiar przydzielonego bloku pamięci.|
|[Ponowne przydzielić](#reallocate)|Wywołanie tej metody, aby ponownie przydzielić blok pamięci.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest implementowany przez [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md)lub [CWin32Heap](../../atl/reference/cwin32heap-class.md).

> [!NOTE]
> Funkcje sterty lokalnej i globalnej są wolniejsze niż inne funkcje zarządzania pamięcią i nie zapewniają tylu funkcji. W związku z tym nowe aplikacje powinny używać [funkcji sterty](/windows/win32/Memory/heap-functions). Są one dostępne w [CWin32Heap](../../atl/reference/cwin32heap-class.md) klasy.

## <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem.h

## <a name="iatlmemmgrallocate"></a><a name="allocate"></a>IAtlmemmgr::Przydziel

Wywołanie tej metody, aby przydzielić blok pamięci.

```cpp
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*n Bajty*<br/>
Żądana liczba bajtów w nowym bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku nowo przydzielonego bloku pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie [IAtlMemMgr::Free](#free) lub [IAtlMemMgr::Reallocate](#reallocate) zwolnić pamięć przydzieloną przez tę metodę.

### <a name="example"></a>Przykład

Na przykład zobacz [Przegląd IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrfree"></a><a name="free"></a>IAtlMemMgr::Wolny

Wywołanie tej metody, aby zwolnić blok pamięci.

```cpp
void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do pamięci wcześniej przydzielonej przez tego menedżera pamięci.

### <a name="remarks"></a>Uwagi

Ta metoda służy do zwalniania pamięci uzyskanej przez [IAtlMemMgr::Allocate](#allocate) lub [IAtlMemMgr::Reallocate](#reallocate).

### <a name="example"></a>Przykład

Na przykład zobacz [Przegląd IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrgetsize"></a><a name="getsize"></a>IAtlmemmgr::GetSize

Wywołanie tej metody, aby pobrać rozmiar przydzielonego bloku pamięci.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do pamięci wcześniej przydzielonej przez tego menedżera pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar bloku pamięci w bajtach.

### <a name="example"></a>Przykład

Na przykład zobacz [Przegląd IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrreallocate"></a><a name="reallocate"></a>IAtlMemMgr::Reallocate

Wywołanie tej metody, aby ponownie przydzielić pamięć przydzieloną przez tego menedżera pamięci.

```cpp
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do pamięci wcześniej przydzielonej przez tego menedżera pamięci.

*n Bajty*<br/>
Żądana liczba bajtów w nowym bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku nowo przydzielonego bloku pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie [IAtlMemMgr::Free](#free) lub [IAtlMemMgr::Reallocate](#reallocate) zwolnić pamięć przydzieloną przez tę metodę.

Koncepcyjnie ta metoda zwalnia istniejącą pamięć i przydziela nowy blok pamięci. W rzeczywistości istniejąca pamięć może zostać rozszerzona lub w inny sposób ponownie usuowana.

### <a name="example"></a>Przykład

Na przykład zobacz [Przegląd IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

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

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch

Ta metoda jest wywoływana w celu uzupełnienia domyślnego interfejsu właściwości otoczenia za pomocą interfejsu zdefiniowanego przez użytkownika.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parametry

*pDispatch (Niedysp.*<br/>
Wskaźnik do nowego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Gdy `SetAmbientDispatch` jest wywoływana ze wskaźnikiem do nowego interfejsu, ten nowy interfejs będzie używany do wywoływania wszelkich właściwości lub metod żądanych przez hostowany formant — jeśli te właściwości nie są już dostarczone przez [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHostWindow::AttachControl

Dołącza istniejący (i wcześniej zainicjowany) formant do obiektu hosta przy użyciu okna identyfikowanego przez *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parametry

*pUnkControl (Kontrola nie)*<br/>
[w] Wskaźnik do `IUnknown` interfejsu formantu, który ma być dołączony do obiektu hosta.

*Hwnd*<br/>
[w] Dojście do okna, które ma być używane do hostingu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHostWindow::CreateControl

Tworzy formant, inicjuje go i hostuje go w oknie identyfikowanym przez *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parametry

*lpTricsData*<br/>
[w] Ciąg identyfikujący formant do utworzenia. Może to być identyfikator CLSID (musi zawierać nawiasy klamrowe), progid, adres URL lub nieprzetworzony kod HTML (poprzedzony **mshtml:**).

*Hwnd*<br/>
[w] Dojście do okna, które ma być używane do hostingu.

*pStream (Strumień)*<br/>
[w] Wskaźnik interfejsu dla strumienia zawierającego dane inicjowania dla formantu. Może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

To okno będzie podklasyfikowane przez obiekt hosta ujawniający ten interfejs, dzięki czemu wiadomości mogą być odzwierciedlane do formantu i inne funkcje kontenera będą działać.

Wywołanie tej metody jest równoznaczne z [wywołaniem IAxWinHostWindow::CreateControlEx](#createcontrolex).

Aby utworzyć licencjonowany formant ActiveX, zobacz [IAxWinHostWindowLic::CreateControlLic](#createcontrollicex).

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx

Tworzy formant ActiveX, inicjuje go i obsługuje w określonym oknie, podobnie jak [IAxWinHostWindow::CreateControl](#createcontrol).

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
[w] Ciąg identyfikujący formant do utworzenia. Może to być identyfikator CLSID (musi zawierać nawiasy klamrowe), progid, adres URL lub nieprzetworzony kod HTML (poprzedzony **mshtml:**).

*Hwnd*<br/>
[w] Dojście do okna, które ma być używane do hostingu.

*pStream (Strumień)*<br/>
[w] Wskaźnik interfejsu dla strumienia zawierającego dane inicjowania dla formantu. Może mieć wartość NULL.

*ppUnk (polski)*<br/>
[na zewnątrz] Adres wskaźnika, który otrzyma `IUnknown` interfejs utworzonego formantu. Może mieć wartość NULL.

*riidAdvise*<br/>
[w] Identyfikator interfejsu wychodzącego interfejsu w contained object. Można IID_NULL.

*punkAdvise*<br/>
[w] Wskaźnik do `IUnknown` interfejsu obiektu ujścia, który ma być połączony z punktem połączenia na zawartym obiekcie określonym przez `iidSink`program .

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

W `CreateControl` przeciwieństwie `CreateControlEx` do metody, umożliwia również odbieranie wskaźnik interfejsu do nowo utworzonego formantu i skonfigurować ujście zdarzeń, aby odbierać zdarzenia uruchamiane przez formant.

Aby utworzyć licencjonowany formant ActiveX, zobacz [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHostWindow::QueryControl

Zwraca określony wskaźnik interfejsu dostarczony przez kontrolę hosta.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Riid*<br/>
[w] Identyfikator interfejsu na formancie, o który się prosi.

*ppvObiekt*<br/>
[na zewnątrz] Adres wskaźnika, który otrzyma określony interfejs utworzonego formantu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch

Ustawia zewnętrzny dispinterface, który jest dostępny do zawartych formantów za pośrednictwem [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) metody.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp (Niem.*<br/>
[w] Wskaźnik do `IDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUiHandler

Wywołanie tej funkcji, aby ustawić zewnętrzny interfejs [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) dla `CAxWindow` obiektu.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp (Niem.*<br/>
[w] Wskaźnik do `IDocHostUIHandlerDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana przez formanty (takie jak formant przeglądarki `IDocHostUIHandlerDispatch` sieci Web), które przeszukują witrynę hosta dla interfejsu.

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic

Tworzy licencjonowany formant, inicjuje go i hostuje `hWnd`w oknie identyfikowanym przez program .

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrLic (bstrlic)*<br/>
[w] BSTR, który zawiera klucz licencyjny formantu.

### <a name="remarks"></a>Uwagi

Zobacz [IAxWinHostWindow::CreateControl](#createcontrol) opis pozostałych parametrów i zwracanej wartości.

Wywołanie tej metody jest równoznaczne z [wywołaniem IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Przykład

Zobacz [Hosting ActiveX Formanty przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla próbki, która używa `IAxWinHostWindowLic::CreateControlLic`.

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx

Tworzy licencjonowany formant ActiveX, inicjuje go i obsługuje w określonym oknie, podobnie jak [IAxWinHostWindow::CreateControl](#createcontrol).

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

*bstrLic (bstrlic)*<br/>
[w] BSTR, który zawiera klucz licencyjny formantu.

### <a name="remarks"></a>Uwagi

Zobacz [IAxWinHostWindow::CreateControlEx](#createcontrolex) opis pozostałych parametrów i zwracanej wartości.

### <a name="example"></a>Przykład

Zobacz [Hosting ActiveX Formanty przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla próbki, która używa `IAxWinHostWindowLic::CreateControlLicEx`.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
