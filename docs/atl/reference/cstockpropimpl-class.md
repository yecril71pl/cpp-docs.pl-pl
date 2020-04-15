---
title: CStockPropImpl Klasa
ms.date: 05/06/2019
f1_keywords:
- CStockPropImpl
- ATLCTL/ATL::CStockPropImpl
- ATLCTL/ATL::get_Appearance
- ATLCTL/ATL::get_AutoSize
- ATLCTL/ATL::get_BackColor
- ATLCTL/ATL::get_BackStyle
- ATLCTL/ATL::get_BorderColor
- ATLCTL/ATL::get_BorderStyle
- ATLCTL/ATL::get_BorderVisible
- ATLCTL/ATL::get_BorderWidth
- ATLCTL/ATL::get_Caption
- ATLCTL/ATL::get_DrawMode
- ATLCTL/ATL::get_DrawStyle
- ATLCTL/ATL::get_DrawWidth
- ATLCTL/ATL::get_Enabled
- ATLCTL/ATL::get_FillColor
- ATLCTL/ATL::get_FillStyle
- ATLCTL/ATL::get_Font
- ATLCTL/ATL::get_ForeColor
- ATLCTL/ATL::get_HWND
- ATLCTL/ATL::get_MouseIcon
- ATLCTL/ATL::get_MousePointer
- ATLCTL/ATL::get_Picture
- ATLCTL/ATL::get_ReadyState
- ATLCTL/ATL::get_TabStop
- ATLCTL/ATL::get_Text
- ATLCTL/ATL::getvalid
- ATLCTL/ATL::get_Window
- ATLCTL/ATL::put_Appearance
- ATLCTL/ATL::put_AutoSize
- ATLCTL/ATL::put_BackColor
- ATLCTL/ATL::put_BackStyle
- ATLCTL/ATL::put_BorderColor
- ATLCTL/ATL::put_BorderStyle
- ATLCTL/ATL::put_BorderVisible
- ATLCTL/ATL::put_BorderWidth
- ATLCTL/ATL::put_Caption
- ATLCTL/ATL::put_DrawMode
- ATLCTL/ATL::put_DrawStyle
- ATLCTL/ATL::put_DrawWidth
- ATLCTL/ATL::put_Enabled
- ATLCTL/ATL::put_FillColor
- ATLCTL/ATL::put_FillStyle
- ATLCTL/ATL::put_Font
- ATLCTL/ATL::put_ForeColor
- ATLCTL/ATL::put_HWND
- ATLCTL/ATL::put_MouseIcon
- ATLCTL/ATL::put_MousePointer
- ATLCTL/ATL::put_Picture
- ATLCTL/ATL::put_ReadyState
- ATLCTL/ATL::put_TabStop
- ATLCTL/ATL::put_Text
- ATLCTL/ATL::putvalid
- ATLCTL/ATL::put_Window
- ATLCTL/ATL::putref_Font
- ATLCTL/ATL::putref_MouseIcon
- ATLCTL/ATL::putref_Picture
helpviewer_keywords:
- CStockPropImpl class
- controls [ATL], stock properties
- stock properties, ATL controls
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
ms.openlocfilehash: 0aaeb1b6de0febfd5fc0d41cbcc7bad41c607af4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330674"
---
# <a name="cstockpropimpl-class"></a>CStockPropImpl Klasa

Ta klasa zawiera metody obsługi wartości właściwości magazynie.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <
    class T,
    class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE CStockPropImpl :
    public IDispatchImpl<InterfaceName, piid, plibid, wMajor, wMinor, tihclass>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa implementująca formant i `CStockPropImpl`wyprowadzająca z .

*Nazwa interfejsu*<br/>
Podwójny interfejs odsłaniający właściwości zapasów.

*piid*<br/>
Wskaźnik do identyfikatora `InterfaceName`.

*plibid ( plibid )*<br/>
Wskaźnik do LIBID biblioteki typów zawierającej `InterfaceName`definicję .

*wMajor*<br/>
Główna wersja biblioteki typów. Wartość domyślna to 1.

*wMinor*<br/>
Wersja pomocnicza biblioteki typów. Wartość domyślna to 0.

*tihclass (klasa tihclass)*<br/>
Klasa używana do zarządzania informacjami o typie *dla T*. Wartością domyślną jest `CComTypeInfoHolder`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|[get_Appearance](#get_appearance)|Wywołanie tej metody, aby uzyskać styl malowania używany przez formant, na przykład płaski lub 3D.|
|[get_AutoSize](#get_autosize)|Wywołanie tej metody, aby uzyskać stan flagi, która wskazuje, czy formant nie może być inny rozmiar.|
|[get_BackColor](#get_backcolor)|Wywołanie tej metody, aby uzyskać kolor tła formantu.|
|[get_BackStyle](#get_backstyle)|Wywołanie tej metody, aby uzyskać styl tła formantu, przezroczyste lub nieprzezroczyste.|
|[get_BorderColor](#get_bordercolor)|Wywołanie tej metody, aby uzyskać kolor obramowania formantu.|
|[get_BorderStyle](#get_borderstyle)|Wywołanie tej metody, aby uzyskać styl obramowania formantu.|
|[get_BorderVisible](#get_bordervisible)|Wywołanie tej metody, aby uzyskać stan flagi, która wskazuje, czy obramowanie formantu jest widoczne, czy nie.|
|[get_BorderWidth](#get_borderwidth)|Wywołanie tej metody, aby uzyskać szerokość (w pikselach) obramowania formantu.|
|[get_Caption](#get_caption)|Wywołanie tej metody, aby uzyskać tekst określony w podpisie obiektu.|
|[get_DrawMode](#get_drawmode)|Wywołanie tej metody, aby uzyskać tryb rysowania formantu, na przykład XOR Pióro lub Odwróć kolory.|
|[get_DrawStyle](#get_drawstyle)|Wywołanie tej metody, aby uzyskać styl rysowania formantu, na przykład bryła, przerywane lub kropkowane.|
|[get_DrawWidth](#get_drawwidth)|Wywołanie tej metody, aby uzyskać szerokość rysunku (w pikselach) używane przez metody rysowania formantu.|
|[get_Enabled](#get_enabled)|Wywołanie tej metody, aby uzyskać stan flagi, która wskazuje, czy formant jest włączony.|
|[get_FillColor](#get_fillcolor)|Wywołanie tej metody, aby uzyskać kolor wypełnienia formantu.|
|[get_FillStyle](#get_fillstyle)|Wywołanie tej metody, aby uzyskać styl wypełnienia formantu, na przykład bryła, przezroczyste lub kreskowane.|
|[get_Font](#get_font)|Wywołanie tej metody, aby uzyskać wskaźnik do właściwości czcionki formantu.|
|[get_ForeColor](#get_forecolor)|Wywołanie tej metody, aby uzyskać kolor pierwszego planu formantu.|
|[get_HWND](#get_hwnd)|Wywołanie tej metody, aby uzyskać dojście okna skojarzone z formantem.|
|[get_MouseIcon](#get_mouseicon)|Wywołanie tej metody, aby uzyskać właściwości obrazu grafiki (ikona, bitmapa lub metaplik) mają być wyświetlane, gdy mysz jest nad formantem.|
|[get_MousePointer](#get_mousepointer)|Wywołanie tej metody, aby uzyskać typ wskaźnika myszy wyświetlane, gdy mysz jest nad formantem, na przykład strzałka, krzyż lub klepsydry.|
|[get_Picture](#get_picture)|Wywołanie tej metody, aby uzyskać wskaźnik do właściwości obrazu grafiki (ikona, bitmapa lub metaplik), które mają być wyświetlane.|
|[get_ReadyState](#get_readystate)|Wywołanie tej metody, aby uzyskać stan gotowości formantu, na przykład ładowania lub załadowania.|
|[get_TabStop](#get_tabstop)|Wywołanie tej metody, aby uzyskać flagę, która wskazuje, czy formant jest tabulatorem, czy nie.|
|[get_Text](#get_text)|Wywołanie tej metody, aby uzyskać tekst, który jest wyświetlany z formantem.|
|[getvalid ( getvalid )](#get_valid)|Wywołanie tej metody, aby uzyskać stan flagi, która wskazuje, czy formant jest prawidłowy, czy nie.|
|[get_Window](#get_window)|Wywołanie tej metody, aby uzyskać dojście okna skojarzone z formantem. Identyczne z [CStockPropImpl::get_HWND](#get_hwnd).|
|[put_Appearance](#put_appearance)|Wywołanie tej metody, aby ustawić styl malowania używany przez formant, na przykład płaski lub 3D.|
|[put_AutoSize](#put_autosize)|Wywołanie tej metody, aby ustawić wartość flagi, która wskazuje, jeśli formant nie może być inny rozmiar.|
|[put_BackColor](#put_backcolor)|Wywołanie tej metody, aby ustawić kolor tła formantu.|
|[put_BackStyle](#put_backstyle)|Wywołanie tej metody, aby ustawić styl tła formantu.|
|[put_BorderColor](#put_bordercolor)|Wywołanie tej metody, aby ustawić kolor obramowania formantu.|
|[put_BorderStyle](#put_borderstyle)|Wywołanie tej metody, aby ustawić styl obramowania formantu.|
|[put_BorderVisible](#put_bordervisible)|Wywołanie tej metody, aby ustawić wartość flagi, która wskazuje, czy obramowanie formantu jest widoczne, czy nie.|
|[put_BorderWidth](#put_borderwidth)|Wywołanie tej metody, aby ustawić szerokość obramowania formantu.|
|[put_Caption](#put_caption)|Wywołanie tej metody, aby ustawić tekst, który ma być wyświetlany z formantem.|
|[put_DrawMode](#put_drawmode)|Wywołanie tej metody, aby ustawić tryb rysowania formantu, na przykład XOR Pióro lub Odwróć kolory.|
|[put_DrawStyle](#put_drawstyle)|Wywołanie tej metody, aby ustawić styl rysowania formantu, na przykład bryła, przerywane lub kropkowane.|
|[put_DrawWidth](#put_drawwidth)|Wywołanie tej metody, aby ustawić szerokość (w pikselach) używane przez metody rysowania formantu.|
|[put_Enabled](#put_enabled)|Wywołanie tej metody, aby ustawić flagę, która wskazuje, czy formant jest włączony.|
|[put_FillColor](#put_fillcolor)|Wywołanie tej metody, aby ustawić kolor wypełnienia formantu.|
|[put_FillStyle](#put_fillstyle)|Wywołanie tej metody, aby ustawić styl wypełnienia formantu, na przykład bryła, przezroczyste lub kreskowane.|
|[put_Font](#put_font)|Wywołanie tej metody, aby ustawić właściwości czcionki formantu.|
|[put_ForeColor](#put_forecolor)|Wywołanie tej metody, aby ustawić kolor pierwszego planu formantu.|
|[put_HWND](#put_hwnd)|Ta metoda zwraca E_FAIL.|
|[put_MouseIcon](#put_mouseicon)|Wywołanie tej metody, aby ustawić właściwości obrazu grafiki (ikona, bitmapa lub metaplik) mają być wyświetlane, gdy mysz jest nad formantem.|
|[put_MousePointer](#put_mousepointer)|Wywołanie tej metody, aby ustawić typ wskaźnika myszy wyświetlany, gdy mysz jest nad formantem, na przykład strzałka, krzyż lub klepsydra.|
|[put_Picture](#put_picture)|Wywołanie tej metody, aby ustawić właściwości obrazu grafiki (ikona, bitmapa lub metaplik) mają być wyświetlane.|
|[put_ReadyState](#put_readystate)|Wywołanie tej metody, aby ustawić stan gotowości formantu, na przykład ładowania lub załadowania.|
|[put_TabStop](#put_tabstop)|Wywołanie tej metody, aby ustawić wartość flagi, która wskazuje, czy formant jest tabulatorem, czy nie.|
|[put_Text](#put_text)|Wywołanie tej metody, aby ustawić tekst, który jest wyświetlany z formantem.|
|[putvalid ( putvalid )](#put_valid)|Wywołanie tej metody, aby ustawić flagę, która wskazuje, czy formant jest prawidłowy, czy nie.|
|[put_Window](#put_window)|Ta metoda wywołuje [CStockPropImpl::put_HWND](#put_hwnd), który zwraca E_FAIL.|
|[putref_Font](#putref_font)|Wywołanie tej metody, aby ustawić właściwości czcionki formantu, z liczbą odwołań.|
|[putref_MouseIcon](#putref_mouseicon)|Wywołanie tej metody, aby ustawić właściwości obrazu grafiki (ikona, bitmapa lub metaplik) mają być wyświetlane, gdy mysz jest nad formantem, z liczbą odwołań.|
|[putref_Picture](#putref_picture)|Wywołanie tej metody, aby ustawić właściwości obrazu grafiki (ikona, bitmapa lub metaplik) mają być wyświetlane, z liczbą odwołań.|

## <a name="remarks"></a>Uwagi

`CStockPropImpl`zapewnia **metody put** and **get** dla każdej właściwości magazynowych. Te metody zapewniają kod niezbędny do skonfigurowania lub uzyskania elementu członkowskiego danych skojarzonego z każdą właściwością oraz powiadamiania i synchronizowania z kontenerem, gdy zmieni się jakakolwiek właściwość.

Visual Studio zapewnia obsługę właściwości zapasów za pośrednictwem swoich kreatorów. Aby uzyskać więcej informacji na temat dodawania właściwości zapasów do formantu, zobacz [samouczek ATL](../../atl/active-template-library-atl-tutorial.md).

W celu zapewnienia zgodności `CStockPropImpl` z `get_Window` powrotem, również udostępnia i `put_Window` metody, które po prostu wywołać `get_HWND` i `put_HWND`, odpowiednio. Domyślna implementacja `put_HWND` zwraca E_FAIL ponieważ HWND powinna być właściwością tylko do odczytu.

Następujące właściwości mają również implementację **gniw:**

- Czcionka

- MouseIcon ( MouseIcon )

- Obraz

Te same trzy właściwości magazynowe wymagają, aby `CComPtr` ich odpowiedni element członkowski danych był typu lub innej klasy, która zapewnia poprawne zliczanie odwołania do interfejsu za pomocą operatora przypisania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`T`

[Idispatchimpl](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="cstockpropimplget_appearance"></a><a name="get_appearance"></a>CStockPropImpl::get_Appearance

Wywołanie tej metody, aby uzyskać styl malowania używany przez formant, na przykład płaski lub 3D.

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>Parametry

*pnPokaz*<br/>
Zmienna, która odbiera styl malowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_autosize"></a><a name="get_autosize"></a>CStockPropImpl::get_AutoSize

Wywołanie tej metody, aby uzyskać stan flagi, która wskazuje, czy formant nie może być inny rozmiar.

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>Parametry

*rozmiar pbAutoSize*<br/>
Zmienna, która odbiera stan flagi. WARTOŚĆ TRUE wskazuje, że formant nie może mieć innego rozmiaru.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_backcolor"></a><a name="get_backcolor"></a>CStockPropImpl::get_BackColor

Wywołanie tej metody, aby uzyskać kolor tła formantu.

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>Parametry

*pclrBackColor*<br/>
Zmienna, która odbiera kolor tła formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_backstyle"></a><a name="get_backstyle"></a>CStockPropImpl::get_BackStyle

Wywołanie tej metody, aby uzyskać styl tła formantu, przezroczyste lub nieprzezroczyste.

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>Parametry

*Styl pnBackstyle*<br/>
Zmienna, która odbiera styl tła formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_bordercolor"></a><a name="get_bordercolor"></a>CStockPropImpl::get_BorderColor

Wywołanie tej metody, aby uzyskać kolor obramowania formantu.

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>Parametry

*pclrBorderColor*<br/>
Zmienna, która odbiera kolor obramowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_borderstyle"></a><a name="get_borderstyle"></a>CStockPropImpl::get_BorderStyle

Wywołanie tej metody, aby uzyskać styl obramowania formantu.

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>Parametry

*pnBorderStyle*<br/>
Zmienna, która odbiera styl obramowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_bordervisible"></a><a name="get_bordervisible"></a>CStockPropImpl::get_BorderVisible

Wywołanie tej metody, aby uzyskać stan flagi, która wskazuje, czy obramowanie formantu jest widoczne, czy nie.

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>Parametry

*pbBorderVisible (Widoczne)*<br/>
Zmienna, która odbiera stan flagi. WARTOŚĆ TRUE wskazuje, że obramowanie formantu jest widoczne.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_borderwidth"></a><a name="get_borderwidth"></a>CStockPropImpl::get_BorderWidth

Wywołanie tej metody, aby uzyskać szerokość obramowania formantu.

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>Parametry

*pnBorderWidth*<br/>
Zmienna, która odbiera szerokość obramowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_caption"></a><a name="get_caption"></a>CStockPropImpl::get_Caption

Wywołanie tej metody, aby uzyskać tekst określony w podpisie obiektu.

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>Parametry

*pbstrCaption (pbstrCaption)*<br/>
Tekst, który ma być wyświetlany z formantem.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_drawmode"></a><a name="get_drawmode"></a>CStockPropImpl::get_DrawMode

Wywołanie tej metody, aby uzyskać tryb rysowania formantu, na przykład XOR Pióro lub Odwróć kolory.

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>Parametry

*pnDrawMode*<br/>
Zmienna odbiera tryb rysowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_drawstyle"></a><a name="get_drawstyle"></a>CStockPropImpl::get_DrawStyle

Wywołanie tej metody, aby uzyskać styl rysowania formantu, na przykład bryła, przerywane lub kropkowane.

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>Parametry

*PnDrawStyle*<br/>
Zmienna odbiera styl rysowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_drawwidth"></a><a name="get_drawwidth"></a>CStockPropImpl::get_DrawWidth

Wywołanie tej metody, aby uzyskać szerokość rysunku (w pikselach) używane przez metody rysowania formantu.

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>Parametry

*pnDrawWidth*<br/>
Zmienna, która odbiera wartość szerokości formantu w pikselach.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_enabled"></a><a name="get_enabled"></a>CStockPropImpl::get_Enabled

Wywołanie tej metody, aby uzyskać stan flagi, która wskazuje, czy formant jest włączony.

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>Parametry

*pbWsają*<br/>
Zmienna, która odbiera stan flagi. FUNKCJA TRUE wskazuje, że formant jest włączony.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_fillcolor"></a><a name="get_fillcolor"></a>CStockPropImpl::get_FillColor

Wywołanie tej metody, aby uzyskać kolor wypełnienia formantu.

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>Parametry

*pclrFillColor*<br/>
Zmienna, która odbiera kolor wypełnienia formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_fillstyle"></a><a name="get_fillstyle"></a>CStockPropImpl::get_FillStyle

Wywołanie tej metody, aby uzyskać styl wypełnienia formantu, na przykład bryła, przezroczyste lub crosshatched.

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>Parametry

*pnFillStyle (polski)*<br/>
Zmienna, która odbiera styl wypełnienia formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_font"></a><a name="get_font"></a>CStockPropImpl::get_Font

Wywołanie tej metody, aby uzyskać wskaźnik do właściwości czcionki formantu.

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont (polski)*<br/>
Zmienna, która odbiera wskaźnik do właściwości czcionki formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_forecolor"></a><a name="get_forecolor"></a>CStockPropImpl::get_ForeColor

Wywołanie tej metody, aby uzyskać kolor pierwszego planu formantu.

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>Parametry

*pclrForeColor (PclrForeColor)*<br/>
Zmienna odbierana przez formanty kolor pierwszego planu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_hwnd"></a><a name="get_hwnd"></a>CStockPropImpl::get_HWND

Wywołanie tej metody, aby uzyskać dojście okna skojarzone z formantem.

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parametry

*phWnd (właśc.*<br/>
Uchwyt okna skojarzony z formantem.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_mouseicon"></a><a name="get_mouseicon"></a>CStockPropImpl::get_MouseIcon

Wywołanie tej metody, aby uzyskać właściwości obrazu grafiki (ikona, bitmapa lub metaplik) mają być wyświetlane, gdy mysz jest nad formantem.

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parametry

*ppZdjęcie*<br/>
Zmienna, która odbiera wskaźnik do właściwości obrazu grafiki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_mousepointer"></a><a name="get_mousepointer"></a>CStockPropImpl::get_MousePointer

Wywołanie tej metody, aby uzyskać typ wskaźnika myszy wyświetlane, gdy mysz jest nad formantem, na przykład strzałka, krzyż lub klepsydry.

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>Parametry

*pnMousePointer (pnMousePointer)*<br/>
Zmienna odbiera typ wskaźnika myszy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_picture"></a><a name="get_picture"></a>CStockPropImpl::get_Picture

Wywołanie tej metody, aby uzyskać wskaźnik do właściwości obrazu grafiki (ikona, bitmapa lub metaplik), które mają być wyświetlane.

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parametry

*ppZdjęcie*<br/>
Zmienna, która odbiera wskaźnik do właściwości obrazu. Zobacz [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_readystate"></a><a name="get_readystate"></a>CStockPropImpl::get_ReadyState

Wywołanie tej metody, aby uzyskać stan gotowości formantu, na przykład ładowania lub załadowania.

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>Parametry

*pnReadyState*<br/>
Zmienna, która odbiera stan gotowości formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_tabstop"></a><a name="get_tabstop"></a>CStockPropImpl::get_TabStop

Wywołanie tej metody, aby uzyskać stan flagi, która wskazuje, czy formant jest tabulatorem, czy nie.

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>Parametry

*pbTabStop*<br/>
Zmienna, która odbiera stan flagi. WARTOŚĆ TRUE oznacza, że formant jest tabulatorem.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_text"></a><a name="get_text"></a>CStockPropImpl::get_Text

Wywołanie tej metody, aby uzyskać tekst, który jest wyświetlany z formantem.

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>Parametry

*pbstrText (tekst pbstrText)*<br/>
Tekst, który jest wyświetlany z formantem.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplgetvalid"></a><a name="get_valid"></a>CStockPropImpl::getvalid

Wywołanie tej metody, aby uzyskać stan flagi, która wskazuje, czy formant jest prawidłowy, czy nie.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>Parametry

*pbValid (Polski)*<br/>
Zmienna, która odbiera stan flagi. WARTOŚĆ TRUE wskazuje, że formant jest prawidłowy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplget_window"></a><a name="get_window"></a>CStockPropImpl::get_Window

Wywołanie tej metody, aby uzyskać dojście okna skojarzone z formantem. Identyczne z [CStockPropImpl::get_HWND](#get_hwnd).

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parametry

*phWnd (właśc.*<br/>
Uchwyt okna skojarzony z formantem.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_appearance"></a><a name="put_appearance"></a>CStockPropImpl::put_Appearance

Wywołanie tej metody, aby ustawić styl malowania używany przez formant, na przykład płaski lub 3D.

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>Parametry

*nPojatrakcja*<br/>
Nowy styl malowania do użycia przez formant.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_autosize"></a><a name="put_autosize"></a>CStockPropImpl::put_AutoSize

Wywołanie tej metody, aby ustawić wartość flagi, która wskazuje, jeśli formant nie może być inny rozmiar.

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>Parametry

*bAutoSize*<br/>
PRAWDA, jeśli formant nie może mieć innego rozmiaru.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_backcolor"></a><a name="put_backcolor"></a>CStockPropImpl::put_BackColor

Wywołanie tej metody, aby ustawić kolor tła formantu.

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>Parametry

*clrBackColor (clrBackColor)*<br/>
Nowy kolor tła sterowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_backstyle"></a><a name="put_backstyle"></a>CStockPropImpl::put_BackStyle

Wywołanie tej metody, aby ustawić styl tła formantu.

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>Parametry

*styl nBack*<br/>
Nowy styl sterowania tła.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_bordercolor"></a><a name="put_bordercolor"></a>CStockPropImpl::put_BorderColor

Wywołanie tej metody, aby ustawić kolor obramowania formantu.

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>Parametry

*clrBorderColor*<br/>
Nowy kolor obramowania. Typ danych OLE_COLOR jest wewnętrznie reprezentowany jako 32-bitowa liczba całkowita.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_borderstyle"></a><a name="put_borderstyle"></a>CStockPropImpl::put_BorderStyle

Wywołanie tej metody, aby ustawić styl obramowania formantu.

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>Parametry

*nBorderStyle*<br/>
Nowy styl obramowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_bordervisible"></a><a name="put_bordervisible"></a>CStockPropImpl::put_BorderVisible

Wywołanie tej metody, aby ustawić wartość flagi, która wskazuje, czy obramowanie formantu jest widoczne, czy nie.

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>Parametry

*bDojwiększy*<br/>
PRAWDA, jeśli obramowanie ma być widoczne.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_borderwidth"></a><a name="put_borderwidth"></a>CStockPropImpl::put_BorderWidth

Wywołanie tej metody, aby ustawić szerokość obramowania formantu.

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>Parametry

*nBorderWidth (właso)*<br/>
Nowa szerokość obramowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_caption"></a><a name="put_caption"></a>CStockPropImpl::put_Caption

Wywołanie tej metody, aby ustawić tekst, który ma być wyświetlany z formantem.

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>Parametry

*bstrCaption (bstrCaption)*<br/>
Tekst, który ma być wyświetlany z formantem.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_drawmode"></a><a name="put_drawmode"></a>CStockPropImpl::put_DrawMode

Wywołanie tej metody, aby ustawić tryb rysowania formantu, na przykład XOR Pióro lub Odwróć kolory.

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>Parametry

*nDrawMode (nDrawMode)*<br/>
Nowy tryb rysowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_drawstyle"></a><a name="put_drawstyle"></a>CStockPropImpl::put_DrawStyle

Wywołanie tej metody, aby ustawić styl rysowania formantu, na przykład bryła, przerywane lub kropkowane.

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>Parametry

*styl nDrawStyle*<br/>
Nowy styl rysowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_drawwidth"></a><a name="put_drawwidth"></a>CStockPropImpl::put_DrawWidth

Wywołanie tej metody, aby ustawić szerokość (w pikselach) używane przez metody rysowania formantu.

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>Parametry

*nDrawWidth (właswoi)*<br/>
Nowa szerokość, która ma być używana przez metody rysowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_enabled"></a><a name="put_enabled"></a>CStockPropImpl::put_Enabled

Wywołanie tej metody, aby ustawić wartość flagi, która wskazuje, czy formant jest włączony.

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*bWłach*<br/>
PRAWDA, jeśli formant jest włączony.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_fillcolor"></a><a name="put_fillcolor"></a>CStockPropImpl::put_FillColor

Wywołanie tej metody, aby ustawić kolor wypełnienia formantu.

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>Parametry

*clrFillColor (kolor clrFillColor)*<br/>
Nowy kolor wypełnienia formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_fillstyle"></a><a name="put_fillstyle"></a>CStockPropImpl::put_FillStyle

Wywołanie tej metody, aby ustawić styl wypełnienia formantu, na przykład bryła, przezroczyste lub kreskowane.

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>Parametry

*styl wypełnienia*<br/>
Nowy styl wypełnienia formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_font"></a><a name="put_font"></a>CStockPropImpl::put_Font

Wywołanie tej metody, aby ustawić właściwości czcionki formantu.

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont (pFont)*<br/>
Wskaźnik do właściwości czcionki formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_forecolor"></a><a name="put_forecolor"></a>CStockPropImpl::put_ForeColor

Wywołanie tej metody, aby ustawić kolor pierwszego planu formantu.

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>Parametry

*clrForeColor (właso)*<br/>
Nowy kolor pierwszego planu formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_hwnd"></a><a name="put_hwnd"></a>CStockPropImpl::put_HWND

Ta metoda zwraca E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Zarezerwowany.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_FAIL.

### <a name="remarks"></a>Uwagi

Uchwyt okna jest wartością tylko do odczytu.

## <a name="cstockpropimplput_mouseicon"></a><a name="put_mouseicon"></a>CStockPropImpl::put_MouseIcon

Wywołanie tej metody, aby ustawić właściwości obrazu grafiki (ikona, bitmapa lub metaplik) mają być wyświetlane, gdy mysz jest nad formantem.

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pZdaję*<br/>
Wskaźnik do właściwości obrazu grafiki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_mousepointer"></a><a name="put_mousepointer"></a>CStockPropImpl::put_MousePointer

Wywołanie tej metody, aby ustawić typ wskaźnika myszy wyświetlany, gdy mysz jest nad formantem, na przykład strzałka, krzyż lub klepsydra.

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>Parametry

*nMousePointer (Program zmysłami)*<br/>
Typ wskaźnika myszy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_picture"></a><a name="put_picture"></a>CStockPropImpl::put_Picture

Wywołanie tej metody, aby ustawić właściwości obrazu grafiki (ikona, bitmapa lub metaplik) mają być wyświetlane.

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pZdaję*<br/>
Wskaźnik do właściwości obrazu. Zobacz [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_readystate"></a><a name="put_readystate"></a>CStockPropImpl::put_ReadyState

Wywołanie tej metody, aby ustawić stan gotowości formantu, na przykład ładowania lub załadowania.

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>Parametry

*nWłasny stan*<br/>
Stan gotowości formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_tabstop"></a><a name="put_tabstop"></a>CStockPropImpl::put_TabStop

Wywołanie tej metody, aby ustawić flagę, która wskazuje, czy formant jest tabulatorem, czy nie.

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>Parametry

*bTabStop*<br/>
PRAWDA, jeśli formant jest tabulatorem.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_text"></a><a name="put_text"></a>CStockPropImpl::put_Text

Wywołanie tej metody, aby ustawić tekst, który jest wyświetlany z formantem.

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>Parametry

*tekst bstrText*<br/>
Tekst, który jest wyświetlany z formantem.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplputvalid"></a><a name="put_valid"></a>CStockPropImpl::putvalid

Wywołanie tej metody, aby ustawić flagę, która wskazuje, czy formant jest prawidłowy, czy nie.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>Parametry

*bValid (Niem.*<br/>
PRAWDA, jeśli formant jest prawidłowy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="cstockpropimplput_window"></a><a name="put_window"></a>CStockPropImpl::put_Window

Ta metoda wywołuje [CStockPropImpl::put_HWND](#put_hwnd), który zwraca E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Uchwyt okna.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_FAIL.

### <a name="remarks"></a>Uwagi

Uchwyt okna jest wartością tylko do odczytu.

## <a name="cstockpropimplputref_font"></a><a name="putref_font"></a>CStockPropImpl::putref_Font

Wywołanie tej metody, aby ustawić właściwości czcionki formantu, z liczbą odwołań.

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont (pFont)*<br/>
Wskaźnik do właściwości czcionki formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Tak samo jak [CStockPropImpl::put_Font](#put_font), ale z liczbą odwołań.

## <a name="cstockpropimplputref_mouseicon"></a><a name="putref_mouseicon"></a>CStockPropImpl::putref_MouseIcon

Wywołanie tej metody, aby ustawić właściwości obrazu grafiki (ikona, bitmapa lub metaplik) mają być wyświetlane, gdy mysz jest nad formantem, z liczbą odwołań.

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pZdaję*<br/>
Wskaźnik do właściwości obrazu grafiki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Tak samo jak [CStockPropImpl::put_MouseIcon](#put_mouseicon), ale z liczbą odwołań.

## <a name="cstockpropimplputref_picture"></a><a name="putref_picture"></a>CStockPropImpl::putref_Picture

Wywołanie tej metody, aby ustawić właściwości obrazu grafiki (ikona, bitmapa lub metaplik) mają być wyświetlane, z liczbą odwołań.

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pZdaję*<br/>
Wskaźnik do właściwości obrazu. Zobacz [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Tak samo jak [CStockPropImpl::put_Picture](#put_picture), ale z liczbą odwołań.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa IDispatchImpl](../../atl/reference/idispatchimpl-class.md)
