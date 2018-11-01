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
ms.openlocfilehash: ed1dfd1dc8767b4f198ec6cc8dd626a04800bffd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596771"
---
# <a name="iatlmemmgr-class"></a>Klasa IAtlMemMgr

Ta klasa reprezentuje interfejs do Menedżera pamięci.

## <a name="syntax"></a>Składnia

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Przydziel](#allocate)|Wywołaj tę metodę można przydzielić bloku pamięci.|
|[Bezpłatne](#free)|Wywołaj tę metodę w celu zwolnienia bloku pamięci.|
|[GetSize](#getsize)|Wywołaj tę metodę można pobrać rozmiaru bloku ilość przydzielonej pamięci.|
|[Ponowne przydzielenie](#reallocate)|Wywołaj tę metodę, aby ponowne przydzielenie bloków pamięci.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest implementowany przez [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md), lub [CWin32Heap](../../atl/reference/cwin32heap-class.md).

> [!NOTE]
>  Funkcje sterty lokalne i globalne wolniej niż inne funkcje zarządzania pamięcią i nie są oferowane jako wiele funkcji. W związku z tym, nowe aplikacje powinny używać [sterty funkcji](/windows/desktop/Memory/heap-functions). Są one dostępne w [CWin32Heap](../../atl/reference/cwin32heap-class.md) klasy.

## <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem.h

##  <a name="allocate"></a>  IAtlMemMgr::Allocate

Wywołaj tę metodę można przydzielić bloku pamięci.

```
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Żądana liczba bajtów w nowy blok pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku bloku nowo alokacji pamięci.

### <a name="remarks"></a>Uwagi

Wywołaj [IAtlMemMgr::Free](#free) lub [IAtlMemMgr::Reallocate](#reallocate) zwolnienie pamięci przydzielonej przez tę metodę.

### <a name="example"></a>Przykład

Aby uzyskać przykład, zobacz [Przegląd IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="free"></a>  IAtlMemMgr::Free

Wywołaj tę metodę w celu zwolnienia bloku pamięci.

```
void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do pamięci uprzednio przydzielonej przez tego menedżera pamięci.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby zwolnić pamięć, uzyskaną przez [IAtlMemMgr::Allocate](#allocate) lub [IAtlMemMgr::Reallocate](#reallocate).

### <a name="example"></a>Przykład

Aby uzyskać przykład, zobacz [Przegląd IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="getsize"></a>  IAtlMemMgr::GetSize

Wywołaj tę metodę można pobrać rozmiaru bloku ilość przydzielonej pamięci.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do pamięci uprzednio przydzielonej przez tego menedżera pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar bloku pamięci w bajtach.

### <a name="example"></a>Przykład

Aby uzyskać przykład, zobacz [Przegląd IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="reallocate"></a>  IAtlMemMgr::Reallocate

Wywołaj tę metodę w celu ponownego przydzielenia pamięci przydzielonej przez tego menedżera pamięci.

```
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do pamięci uprzednio przydzielonej przez tego menedżera pamięci.

*nBytes*<br/>
Żądana liczba bajtów w nowy blok pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku bloku nowo alokacji pamięci.

### <a name="remarks"></a>Uwagi

Wywołaj [IAtlMemMgr::Free](#free) lub [IAtlMemMgr::Reallocate](#reallocate) zwolnienie pamięci przydzielonej przez tę metodę.

Koncepcyjnie ta metoda zwalnia pamięć istniejących i przydziela nowy blok pamięci. W rzeczywistości może być rozszerzony lub w przeciwnym razie ponownie istniejącej pamięci.

### <a name="example"></a>Przykład

Aby uzyskać przykład, zobacz [Przegląd IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

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

##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch

Ta metoda jest wywoływana, aby uzupełnić domyślny interfejs zmieniono właściwość przy użyciu interfejsu użytkownika.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parametry

*pDispatch*<br/>
Wskaźnik do nowego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Gdy `SetAmbientDispatch` jest wywoływana za pomocą wskaźnika do nowego interfejsu ten nowy interfejs będzie służyć do wywołania dowolnego właściwości lub metody wymagane przez obsługiwanego formantu — jeśli te właściwości nie są już udostępniane przez [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl

Dołącza kontrolkę istniejących (i wcześniej zainicjowane) do obiektu hosta, za pomocą okna identyfikowane przez *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parametry

*pUnkControl*<br/>
[in] Wskaźnik do `IUnknown` interfejsu formant mógł być dołączony do obiektu hosta.

*hWnd*<br/>
[in] Dojście do okna, które ma być używany do hostowania.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl

Tworzy formant, inicjuje go i umieszcza w oknie identyfikowane przez *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parametry

*lpTricsData*<br/>
[in] Ciąg identyfikujący formantu do utworzenia. Może być CLSID (musi zawierać nawiasów klamrowych), identyfikator ProgID, adres URL lub kod HTML (poprzedzony **MSHTML:**).

*hWnd*<br/>
[in] Dojście do okna, które ma być używany do hostowania.

*pStream*<br/>
[in] Wskaźnik interfejsu dla strumienia zawierający dane inicjowania dla formantu. Może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

To okno zostanie należy do podklasy przez obiekt hosta udostępnianie tego interfejsu, tak aby komunikaty mogą pojawiają się do kontrolki i inne funkcje kontenera będzie działać.

Wywołanie tej metody jest równoważne z wywoływaniem [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Aby utworzyć licencjonowany formant ActiveX, zobacz [IAxWinHostWindowLic::CreateControlLic](#createcontrollicex).

##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx

Tworzy formant ActiveX, inicjuje go i umieszcza w określonym oknie, podobnie jak [IAxWinHostWindow::CreateControl](#createcontrol).

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
[in] Ciąg identyfikujący formantu do utworzenia. Może być CLSID (musi zawierać nawiasów klamrowych), identyfikator ProgID, adres URL lub kod HTML (z prefiksem **MSHTML:**).

*hWnd*<br/>
[in] Dojście do okna, które ma być używany do hostowania.

*pStream*<br/>
[in] Wskaźnik interfejsu dla strumienia zawierający dane inicjowania dla formantu. Może mieć wartości NULL.

*ppUnk*<br/>
[out] Adres wskaźnika, który będzie otrzymywał `IUnknown` interfejsu utworzony formant. Może mieć wartości NULL.

*riidAdvise*<br/>
[in] Identyfikator interfejsu interfejsu wychodzącego w zawartego w nim obiektu. Może być wartością IID_NULL.

*punkAdvise*<br/>
[in] Wskaźnik do `IUnknown` interfejs obiektu sink połączenia z punktem połączenia na przechowywany obiekt określony przez `iidSink`.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

W odróżnieniu od `CreateControl` metody `CreateControlEx` umożliwia również odbierać wskaźnika interfejsu do nowo utworzonego formantu i skonfigurować obiekt sink zdarzenia, aby odbierać zdarzenia wywoływane przez formant.

Aby utworzyć licencjonowany formant ActiveX, zobacz [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex).

##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl

Zwraca określony wskaźnik interfejsu dostarczone przez obsługiwanego formantu.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Parametr riid*<br/>
[in] Identyfikator kontrolki żądanego interfejsu.

*ppvObject*<br/>
[out] Adres wskaźnika, który otrzyma określony interfejs utworzony formant.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch

Zestawy zewnętrzne dispinterface, która jest dostępna dla zawartych w nim formantów za pośrednictwem [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) metody.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
[in] Wskaźnik do `IDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler

Wywołaj tę funkcję, aby ustawić zewnętrzne [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) interfejs na potrzeby `CAxWindow` obiektu.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
[in] Wskaźnik do `IDocHostUIHandlerDispatch` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana przez formanty (na przykład formant przeglądarki sieci Web), które tworzą zapytania dotyczące witryny hosta dla `IDocHostUIHandlerDispatch` interfejsu.

##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic

Tworzy licencjonowany formant, inicjuje go i umieszcza w oknie identyfikowane przez `hWnd`.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrLic*<br/>
[in] BSTR, który zawiera klucz licencji dla formantu.

### <a name="remarks"></a>Uwagi

Zobacz [IAxWinHostWindow::CreateControl](#createcontrol) opis pozostałych parametrów i zwracanej wartości.

Wywołanie tej metody jest równoważne z wywoływaniem [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Przykład

Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu, który używa `IAxWinHostWindowLic::CreateControlLic`.

##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx

Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie, podobnie jak [IAxWinHostWindow::CreateControl](#createcontrol).

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
[in] BSTR, który zawiera klucz licencji dla formantu.

### <a name="remarks"></a>Uwagi

Zobacz [IAxWinHostWindow::CreateControlEx](#createcontrolex) opis pozostałych parametrów i zwracanej wartości.

### <a name="example"></a>Przykład

Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu, który używa `IAxWinHostWindowLic::CreateControlLicEx`.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
