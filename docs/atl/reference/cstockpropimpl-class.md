---
title: Klasa CStockPropImpl
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
ms.openlocfilehash: 9d54e4e5c49e73a12fc5d360c3963c2bcf5b2b38
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835587"
---
# <a name="cstockpropimpl-class"></a>Klasa CStockPropImpl

Ta klasa udostępnia metody obsługi wartości właściwości podstawowych.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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
Klasa implementująca formant i wyprowadzania z `CStockPropImpl` .

*InterfaceName*<br/>
Podwójny interfejs uwidaczniający właściwości giełdowe.

*piid*<br/>
Wskaźnik do identyfikatora IID `InterfaceName` .

*plibid*<br/>
Wskaźnik do identyfikatora LIBID biblioteki typów zawierającej definicję `InterfaceName` .

*wMajor*<br/>
Główna wersja biblioteki typów. Wartość domyślna to 1.

*wMinor*<br/>
Wersja pomocnicza biblioteki typów. Wartość domyślna to 0.

*tihclass*<br/>
Klasa używana do zarządzania informacjami o typie dla *T*. Wartość domyślna to `CComTypeInfoHolder` .

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|-|-|
|[get_Appearance](#get_appearance)|Wywołaj tę metodę, aby uzyskać styl farby używany przez kontrolkę, na przykład płaski lub 3W.|
|[get_AutoSize](#get_autosize)|Wywołaj tę metodę, aby uzyskać stan flagi wskazującej, czy kontrolka nie może być żadnym innym rozmiarem.|
|[get_BackColor](#get_backcolor)|Wywołaj tę metodę, aby uzyskać kolor tła kontrolki.|
|[get_BackStyle](#get_backstyle)|Wywołaj tę metodę, aby uzyskać styl tła kontrolki, jako przezroczysty lub nieprzezroczysty.|
|[get_BorderColor](#get_bordercolor)|Wywołaj tę metodę, aby uzyskać kolor obramowania kontrolki.|
|[get_BorderStyle](#get_borderstyle)|Wywołaj tę metodę, aby uzyskać styl obramowania kontrolki.|
|[get_BorderVisible](#get_bordervisible)|Wywołaj tę metodę, aby uzyskać stan flagi wskazującej, czy obramowanie kontrolki jest widoczne, czy nie.|
|[get_BorderWidth](#get_borderwidth)|Wywołaj tę metodę, aby uzyskać szerokość (w pikselach) obramowania kontrolki.|
|[get_Caption](#get_caption)|Wywołaj tę metodę, aby uzyskać tekst określony w podpisie obiektu.|
|[get_DrawMode](#get_drawmode)|Wywołaj tę metodę, aby uzyskać tryb rysowania kontrolki, na przykład pióro XOR lub Odwróć kolory.|
|[get_DrawStyle](#get_drawstyle)|Wywołaj tę metodę, aby uzyskać styl rysowania kontrolki, na przykład Solid, kreskowany lub kropkowany.|
|[get_DrawWidth](#get_drawwidth)|Wywołaj tę metodę, aby uzyskać szerokość rysunku (w pikselach) używaną przez metody rysowania kontrolki.|
|[get_Enabled](#get_enabled)|Wywołaj tę metodę, aby uzyskać stan flagi wskazującej, czy kontrolka jest włączona.|
|[get_FillColor](#get_fillcolor)|Wywołaj tę metodę, aby uzyskać kolor wypełnienia formantu.|
|[get_FillStyle](#get_fillstyle)|Wywołaj tę metodę, aby uzyskać styl wypełnienia kontrolki, na przykład pełny, przezroczysty lub wylęgowe krzyżowo.|
|[get_Font](#get_font)|Wywołaj tę metodę, aby uzyskać wskaźnik do właściwości czcionki kontrolki.|
|[get_ForeColor](#get_forecolor)|Wywołaj tę metodę, aby uzyskać kolor pierwszego planu formantu.|
|[get_HWND](#get_hwnd)|Wywołaj tę metodę, aby uzyskać uchwyt okna skojarzonego z kontrolką.|
|[get_MouseIcon](#get_mouseicon)|Wywołaj tę metodę, aby uzyskać właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), które mają być wyświetlane, gdy wskaźnik myszy znajduje się nad kontrolką.|
|[get_MousePointer](#get_mousepointer)|Wywołaj tę metodę, aby uzyskać typ wskaźnika myszy wyświetlanego, gdy wskaźnik myszy znajduje się nad kontrolką, na przykład strzałką, krzyżykiem lub klepsydrą.|
|[get_Picture](#get_picture)|Wywołaj tę metodę, aby uzyskać wskaźnik do właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), która ma zostać wyświetlona.|
|[get_ReadyState](#get_readystate)|Wywołaj tę metodę, aby uzyskać stan gotowości kontrolki, na przykład ładowania lub ładowania.|
|[get_TabStop](#get_tabstop)|Wywołaj tę metodę, aby uzyskać flagę wskazującą, czy kontrolka jest tabulatorem.|
|[get_Text](#get_text)|Wywołaj tę metodę, aby uzyskać tekst wyświetlany z kontrolką.|
|[getprawidłowy](#get_valid)|Wywołaj tę metodę, aby uzyskać stan flagi wskazującej, czy formant jest prawidłowy, czy nie.|
|[get_Window](#get_window)|Wywołaj tę metodę, aby uzyskać uchwyt okna skojarzonego z kontrolką. Identyczny z [CStockPropImpl:: get_HWND](#get_hwnd).|
|[put_Appearance](#put_appearance)|Wywołaj tę metodę, aby ustawić styl farby używany przez kontrolkę, na przykład płaski lub 3W.|
|[put_AutoSize](#put_autosize)|Wywołaj tę metodę, aby ustawić wartość flagi wskazującej, czy kontrolka nie może być żadnym innym rozmiarem.|
|[put_BackColor](#put_backcolor)|Wywołaj tę metodę, aby ustawić kolor tła kontrolki.|
|[put_BackStyle](#put_backstyle)|Wywołaj tę metodę, aby ustawić styl tła kontrolki.|
|[put_BorderColor](#put_bordercolor)|Wywołaj tę metodę, aby ustawić kolor obramowania kontrolki.|
|[put_BorderStyle](#put_borderstyle)|Wywołaj tę metodę, aby ustawić styl obramowania kontrolki.|
|[put_BorderVisible](#put_bordervisible)|Wywołaj tę metodę, aby ustawić wartość flagi wskazującej, czy obramowanie kontrolki jest widoczne, czy nie.|
|[put_BorderWidth](#put_borderwidth)|Wywołaj tę metodę, aby ustawić szerokość obramowania kontrolki.|
|[put_Caption](#put_caption)|Wywołaj tę metodę, aby ustawić tekst, który będzie wyświetlany z kontrolką.|
|[put_DrawMode](#put_drawmode)|Wywołaj tę metodę, aby ustawić tryb rysowania kontrolki, na przykład pióro XOR lub Odwróć kolory.|
|[put_DrawStyle](#put_drawstyle)|Wywołaj tę metodę, aby ustawić styl rysowania kontrolki, na przykład Solid, kreskowany lub kropkowany.|
|[put_DrawWidth](#put_drawwidth)|Wywołaj tę metodę, aby ustawić szerokość (w pikselach) używaną przez metody rysowania kontrolki.|
|[put_Enabled](#put_enabled)|Wywołaj tę metodę, aby ustawić flagę wskazującą, czy kontrolka jest włączona.|
|[put_FillColor](#put_fillcolor)|Wywołaj tę metodę, aby ustawić kolor wypełnienia formantu.|
|[put_FillStyle](#put_fillstyle)|Wywołaj tę metodę, aby ustawić styl wypełnienia kontrolki, na przykład pełny, przezroczysty lub wylęgowe krzyżowo.|
|[put_Font](#put_font)|Wywołaj tę metodę, aby ustawić właściwości czcionki kontrolki.|
|[put_ForeColor](#put_forecolor)|Wywołaj tę metodę, aby ustawić kolor pierwszego planu formantu.|
|[put_HWND](#put_hwnd)|Ta metoda zwraca E_FAIL.|
|[put_MouseIcon](#put_mouseicon)|Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), które mają być wyświetlane, gdy wskaźnik myszy znajduje się nad kontrolką.|
|[put_MousePointer](#put_mousepointer)|Wywołaj tę metodę, aby ustawić typ wskaźnika myszy wyświetlanego, gdy wskaźnik myszy znajduje się nad kontrolką, na przykład strzałką, krzyżykiem lub klepsydrą.|
|[put_Picture](#put_picture)|Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikony, mapy bitowej lub metapliku) do wyświetlenia.|
|[put_ReadyState](#put_readystate)|Wywołaj tę metodę, aby ustawić stan gotowości kontrolki, na przykład ładowania lub ładowania.|
|[put_TabStop](#put_tabstop)|Wywołaj tę metodę, aby ustawić wartość flagi wskazującej, czy kontrolka jest tabulatorem.|
|[put_Text](#put_text)|Wywołaj tę metodę, aby ustawić tekst wyświetlany z kontrolką.|
|[putvalid](#put_valid)|Wywołaj tę metodę, aby ustawić flagę wskazującą, czy formant jest prawidłowy, czy nie.|
|[put_Window](#put_window)|Ta metoda wywołuje [CStockPropImpl::p ut_HWND](#put_hwnd), która zwraca E_FAIL.|
|[putref_Font](#putref_font)|Wywołaj tę metodę, aby ustawić właściwości czcionki kontrolki z liczbą odwołań.|
|[putref_MouseIcon](#putref_mouseicon)|Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), które mają być wyświetlane, gdy wskaźnik myszy znajduje się nad kontrolką, z liczbą odwołań.|
|[putref_Picture](#putref_picture)|Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikony, mapy bitowej lub metapliku), która ma być wyświetlana z liczbą odwołań.|

## <a name="remarks"></a>Uwagi

`CStockPropImpl` zapewnia metody **Put** i **Get** dla każdej właściwości giełdowej. Te metody zapewniają kod niezbędny do ustawienia lub pobrania składowej danych skojarzonej z każdą właściwością oraz do powiadamiania i synchronizowania z kontenerem w przypadku zmiany właściwości.

Program Visual Studio zapewnia obsługę właściwości podstawowych za pomocą kreatorów. Aby uzyskać więcej informacji na temat dodawania właściwości podstawowych do kontrolki, zobacz [samouczek ATL](../../atl/active-template-library-atl-tutorial.md).

W celu zapewnienia zgodności z poprzednimi wersjami `CStockPropImpl` udostępnia również `get_Window` `put_Window` metody, które po prostu wywołują `get_HWND` i `put_HWND` , odpowiednio. Domyślna implementacja funkcji `put_HWND` returns E_FAIL, ponieważ właściwość HWND powinna być właściwością tylko do odczytu.

Następujące właściwości mają również implementację **PUTREF** :

- Czcionka

- MouseIcon

- Obraz

Te same trzy właściwości podstawowe wymagają odpowiedniego elementu członkowskiego danych jako typu `CComPtr` lub innej klasy, która zapewnia poprawne zliczanie odwołań do interfejsów za pomocą operatora przypisania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`T`

[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

## <a name="cstockpropimplget_appearance"></a><a name="get_appearance"></a> CStockPropImpl:: get_Appearance

Wywołaj tę metodę, aby uzyskać styl farby używany przez kontrolkę, na przykład płaski lub 3W.

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>Parametry

*pnAppearance*<br/>
Zmienna, która otrzymuje styl malowania kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_autosize"></a><a name="get_autosize"></a> CStockPropImpl:: get_AutoSize

Wywołaj tę metodę, aby uzyskać stan flagi wskazującej, czy kontrolka nie może być żadnym innym rozmiarem.

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>Parametry

*pbAutoSize*<br/>
Zmienna, która odbiera stan flagi. Wartość TRUE oznacza, że kontrolka nie może być żadnym innym rozmiarem.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_backcolor"></a><a name="get_backcolor"></a> CStockPropImpl:: get_BackColor

Wywołaj tę metodę, aby uzyskać kolor tła kontrolki.

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>Parametry

*pclrBackColor*<br/>
Zmienna, która otrzymuje kolor tła kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_backstyle"></a><a name="get_backstyle"></a> CStockPropImpl:: get_BackStyle

Wywołaj tę metodę, aby uzyskać styl tła kontrolki, jako przezroczysty lub nieprzezroczysty.

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>Parametry

*pnBackStyle*<br/>
Zmienna, która otrzymuje styl tła formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_bordercolor"></a><a name="get_bordercolor"></a> CStockPropImpl:: get_BorderColor

Wywołaj tę metodę, aby uzyskać kolor obramowania kontrolki.

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>Parametry

*pclrBorderColor*<br/>
Zmienna, która otrzymuje kolor obramowania kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_borderstyle"></a><a name="get_borderstyle"></a> CStockPropImpl:: get_BorderStyle

Wywołaj tę metodę, aby uzyskać styl obramowania kontrolki.

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>Parametry

*pnBorderStyle*<br/>
Zmienna, która otrzymuje styl obramowania kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_bordervisible"></a><a name="get_bordervisible"></a> CStockPropImpl:: get_BorderVisible

Wywołaj tę metodę, aby uzyskać stan flagi wskazującej, czy obramowanie kontrolki jest widoczne, czy nie.

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>Parametry

*pbBorderVisible*<br/>
Zmienna, która odbiera stan flagi. Wartość TRUE wskazuje, że obramowanie kontrolki jest widoczne.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_borderwidth"></a><a name="get_borderwidth"></a> CStockPropImpl:: get_BorderWidth

Wywołaj tę metodę, aby uzyskać szerokość obramowania kontrolki.

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>Parametry

*pnBorderWidth*<br/>
Zmienna, która otrzymuje szerokość obramowania kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_caption"></a><a name="get_caption"></a> CStockPropImpl:: get_Caption

Wywołaj tę metodę, aby uzyskać tekst określony w podpisie obiektu.

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>Parametry

*pbstrCaption*<br/>
Tekst, który będzie wyświetlany z kontrolką.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_drawmode"></a><a name="get_drawmode"></a> CStockPropImpl:: get_DrawMode

Wywołaj tę metodę, aby uzyskać tryb rysowania kontrolki, na przykład pióro XOR lub Odwróć kolory.

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>Parametry

*pnDrawMode*<br/>
Zmienna, która odbiera tryb rysowania kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_drawstyle"></a><a name="get_drawstyle"></a> CStockPropImpl:: get_DrawStyle

Wywołaj tę metodę, aby uzyskać styl rysowania kontrolki, na przykład Solid, kreskowany lub kropkowany.

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>Parametry

*pnDrawStyle*<br/>
Zmienna, która otrzymuje styl rysowania kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_drawwidth"></a><a name="get_drawwidth"></a> CStockPropImpl:: get_DrawWidth

Wywołaj tę metodę, aby uzyskać szerokość rysunku (w pikselach) używaną przez metody rysowania kontrolki.

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>Parametry

*pnDrawWidth*<br/>
Zmienna, która otrzymuje wartość szerokości kontrolki (w pikselach).

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_enabled"></a><a name="get_enabled"></a> CStockPropImpl:: get_Enabled

Wywołaj tę metodę, aby uzyskać stan flagi wskazującej, czy kontrolka jest włączona.

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>Parametry

*pbEnabled*<br/>
Zmienna, która odbiera stan flagi. Wartość TRUE oznacza, że kontrolka jest włączona.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_fillcolor"></a><a name="get_fillcolor"></a> CStockPropImpl:: get_FillColor

Wywołaj tę metodę, aby uzyskać kolor wypełnienia formantu.

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>Parametry

*pclrFillColor*<br/>
Zmienna, która otrzymuje kolor wypełnienia formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_fillstyle"></a><a name="get_fillstyle"></a> CStockPropImpl:: get_FillStyle

Wywołaj tę metodę, aby uzyskać styl wypełnienia kontrolki, na przykład Solid, transparent lub crosshatched.

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>Parametry

*pnFillStyle*<br/>
Zmienna, która odbiera styl wypełnienia kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_font"></a><a name="get_font"></a> CStockPropImpl:: get_Font

Wywołaj tę metodę, aby uzyskać wskaźnik do właściwości czcionki kontrolki.

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont*<br/>
Zmienna, która otrzymuje wskaźnik do właściwości czcionki kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_forecolor"></a><a name="get_forecolor"></a> CStockPropImpl:: get_ForeColor

Wywołaj tę metodę, aby uzyskać kolor pierwszego planu formantu.

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>Parametry

*pclrForeColor*<br/>
Zmienna, która otrzymuje kolor pierwszego planu kontrolek.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_hwnd"></a><a name="get_hwnd"></a> CStockPropImpl:: get_HWND

Wywołaj tę metodę, aby uzyskać uchwyt okna skojarzonego z kontrolką.

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parametry

*phWnd*<br/>
Uchwyt okna skojarzony z kontrolką.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_mouseicon"></a><a name="get_mouseicon"></a> CStockPropImpl:: get_MouseIcon

Wywołaj tę metodę, aby uzyskać właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), które mają być wyświetlane, gdy wskaźnik myszy znajduje się nad kontrolką.

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parametry

*ppPicture*<br/>
Zmienna, która otrzymuje wskaźnik do właściwości obrazu grafiki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_mousepointer"></a><a name="get_mousepointer"></a> CStockPropImpl:: get_MousePointer

Wywołaj tę metodę, aby uzyskać typ wskaźnika myszy wyświetlanego, gdy wskaźnik myszy znajduje się nad kontrolką, na przykład strzałką, krzyżykiem lub klepsydrą.

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>Parametry

*pnMousePointer*<br/>
Zmienna, która odbiera typ wskaźnika myszy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_picture"></a><a name="get_picture"></a> CStockPropImpl:: get_Picture

Wywołaj tę metodę, aby uzyskać wskaźnik do właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), która ma zostać wyświetlona.

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parametry

*ppPicture*<br/>
Zmienna, która otrzymuje wskaźnik do właściwości obrazu. Aby uzyskać więcej informacji, zobacz [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) .

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_readystate"></a><a name="get_readystate"></a> CStockPropImpl:: get_ReadyState

Wywołaj tę metodę, aby uzyskać stan gotowości kontrolki, na przykład ładowania lub ładowania.

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>Parametry

*pnReadyState*<br/>
Zmienna, która odbiera stan gotowości formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_tabstop"></a><a name="get_tabstop"></a> CStockPropImpl:: get_TabStop

Wywołaj tę metodę, aby uzyskać stan flagi wskazującej, czy kontrolka jest tabulatorem.

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>Parametry

*pbTabStop*<br/>
Zmienna, która odbiera stan flagi. Wartość TRUE oznacza, że kontrolka jest tabulatorem.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_text"></a><a name="get_text"></a> CStockPropImpl:: get_Text

Wywołaj tę metodę, aby uzyskać tekst wyświetlany z kontrolką.

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>Parametry

*pbstrText*<br/>
Tekst wyświetlany z kontrolką.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplgetvalid"></a><a name="get_valid"></a> CStockPropImpl:: getważny

Wywołaj tę metodę, aby uzyskać stan flagi wskazującej, czy formant jest prawidłowy, czy nie.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>Parametry

*pbValid*<br/>
Zmienna, która odbiera stan flagi. Wartość TRUE wskazuje, że formant jest prawidłowy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplget_window"></a><a name="get_window"></a> CStockPropImpl:: get_Window

Wywołaj tę metodę, aby uzyskać uchwyt okna skojarzonego z kontrolką. Identyczny z [CStockPropImpl:: get_HWND](#get_hwnd).

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parametry

*phWnd*<br/>
Uchwyt okna skojarzony z kontrolką.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_appearance"></a><a name="put_appearance"></a> CStockPropImpl::p ut_Appearance

Wywołaj tę metodę, aby ustawić styl farby używany przez kontrolkę, na przykład płaski lub 3W.

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>Parametry

*nAppearance*<br/>
Nowy styl malowania, który ma być używany przez formant.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_autosize"></a><a name="put_autosize"></a> CStockPropImpl::p ut_AutoSize

Wywołaj tę metodę, aby ustawić wartość flagi wskazującej, czy kontrolka nie może być żadnym innym rozmiarem.

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>Parametry

*bAutoSize*<br/>
Ma wartość TRUE, Jeśli kontrolka nie może być żadnym innym rozmiarem.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_backcolor"></a><a name="put_backcolor"></a> CStockPropImpl::p ut_BackColor

Wywołaj tę metodę, aby ustawić kolor tła kontrolki.

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>Parametry

*clrBackColor*<br/>
Nowy kolor tła kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_backstyle"></a><a name="put_backstyle"></a> CStockPropImpl::p ut_BackStyle

Wywołaj tę metodę, aby ustawić styl tła kontrolki.

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>Parametry

*nBackStyle*<br/>
Nowy styl tła kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_bordercolor"></a><a name="put_bordercolor"></a> CStockPropImpl::p ut_BorderColor

Wywołaj tę metodę, aby ustawić kolor obramowania kontrolki.

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>Parametry

*clrBorderColor*<br/>
Nowy kolor obramowania. Typ danych OLE_COLOR jest reprezentowany wewnętrznie jako 32-bitowa Long Integer.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_borderstyle"></a><a name="put_borderstyle"></a> CStockPropImpl::p ut_BorderStyle

Wywołaj tę metodę, aby ustawić styl obramowania kontrolki.

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>Parametry

*nBorderStyle*<br/>
Nowy styl obramowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_bordervisible"></a><a name="put_bordervisible"></a> CStockPropImpl::p ut_BorderVisible

Wywołaj tę metodę, aby ustawić wartość flagi wskazującej, czy obramowanie kontrolki jest widoczne, czy nie.

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>Parametry

*bBorderVisible*<br/>
Ma wartość TRUE, jeśli obramowanie ma być widoczne.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_borderwidth"></a><a name="put_borderwidth"></a> CStockPropImpl::p ut_BorderWidth

Wywołaj tę metodę, aby ustawić szerokość obramowania kontrolki.

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>Parametry

*nBorderWidth*<br/>
Nowa szerokość obramowania kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_caption"></a><a name="put_caption"></a> CStockPropImpl::p ut_Caption

Wywołaj tę metodę, aby ustawić tekst, który będzie wyświetlany z kontrolką.

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>Parametry

*bstrCaption*<br/>
Tekst, który będzie wyświetlany z kontrolką.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_drawmode"></a><a name="put_drawmode"></a> CStockPropImpl::p ut_DrawMode

Wywołaj tę metodę, aby ustawić tryb rysowania kontrolki, na przykład pióro XOR lub Odwróć kolory.

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>Parametry

*nDrawMode*<br/>
Nowy tryb rysowania dla kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_drawstyle"></a><a name="put_drawstyle"></a> CStockPropImpl::p ut_DrawStyle

Wywołaj tę metodę, aby ustawić styl rysowania kontrolki, na przykład Solid, kreskowany lub kropkowany.

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>Parametry

*nDrawStyle*<br/>
Nowy styl rysowania dla kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_drawwidth"></a><a name="put_drawwidth"></a> CStockPropImpl::p ut_DrawWidth

Wywołaj tę metodę, aby ustawić szerokość (w pikselach) używaną przez metody rysowania kontrolki.

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>Parametry

*nDrawWidth*<br/>
Nowa szerokość, która będzie używana przez metody rysowania kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_enabled"></a><a name="put_enabled"></a> CStockPropImpl::p ut_Enabled

Wywołaj tę metodę, aby ustawić wartość flagi wskazującej, czy kontrolka jest włączona.

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*bEnabled*<br/>
Ma wartość TRUE, Jeśli kontrolka jest włączona.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_fillcolor"></a><a name="put_fillcolor"></a> CStockPropImpl::p ut_FillColor

Wywołaj tę metodę, aby ustawić kolor wypełnienia formantu.

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>Parametry

*clrFillColor*<br/>
Nowy kolor wypełnienia formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_fillstyle"></a><a name="put_fillstyle"></a> CStockPropImpl::p ut_FillStyle

Wywołaj tę metodę, aby ustawić styl wypełnienia kontrolki, na przykład pełny, przezroczysty lub wylęgowe krzyżowo.

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>Parametry

*nFillStyle*<br/>
Nowy styl wypełnienia dla kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_font"></a><a name="put_font"></a> CStockPropImpl::p ut_Font

Wywołaj tę metodę, aby ustawić właściwości czcionki kontrolki.

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Wskaźnik do właściwości czcionki kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_forecolor"></a><a name="put_forecolor"></a> CStockPropImpl::p ut_ForeColor

Wywołaj tę metodę, aby ustawić kolor pierwszego planu formantu.

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>Parametry

*clrForeColor*<br/>
Nowy kolor pierwszego planu formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_hwnd"></a><a name="put_hwnd"></a> CStockPropImpl::p ut_HWND

Ta metoda zwraca E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
Zarezerwowany.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_FAIL.

### <a name="remarks"></a>Uwagi

Uchwyt okna to wartość tylko do odczytu.

## <a name="cstockpropimplput_mouseicon"></a><a name="put_mouseicon"></a> CStockPropImpl::p ut_MouseIcon

Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), które mają być wyświetlane, gdy wskaźnik myszy znajduje się nad kontrolką.

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Wskaźnik do właściwości obrazu grafiki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_mousepointer"></a><a name="put_mousepointer"></a> CStockPropImpl::p ut_MousePointer

Wywołaj tę metodę, aby ustawić typ wskaźnika myszy wyświetlanego, gdy wskaźnik myszy znajduje się nad kontrolką, na przykład strzałką, krzyżykiem lub klepsydrą.

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>Parametry

*nMousePointer*<br/>
Typ wskaźnika myszy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_picture"></a><a name="put_picture"></a> CStockPropImpl::p ut_Picture

Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikony, mapy bitowej lub metapliku) do wyświetlenia.

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Wskaźnik do właściwości obrazu. Aby uzyskać więcej informacji, zobacz [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) .

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_readystate"></a><a name="put_readystate"></a> CStockPropImpl::p ut_ReadyState

Wywołaj tę metodę, aby ustawić stan gotowości kontrolki, na przykład ładowania lub ładowania.

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>Parametry

*nReadyState*<br/>
Stan gotowości formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_tabstop"></a><a name="put_tabstop"></a> CStockPropImpl::p ut_TabStop

Wywołaj tę metodę, aby ustawić flagę, która wskazuje, czy kontrolka jest tabulatorem.

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>Parametry

*bTabStop*<br/>
TRUE, Jeśli kontrolka jest tabulatorem.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_text"></a><a name="put_text"></a> CStockPropImpl::p ut_Text

Wywołaj tę metodę, aby ustawić tekst wyświetlany z kontrolką.

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>Parametry

*bstrText*<br/>
Tekst wyświetlany z kontrolką.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplputvalid"></a><a name="put_valid"></a> CStockPropImpl::p utvalid

Wywołaj tę metodę, aby ustawić flagę wskazującą, czy formant jest prawidłowy, czy nie.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>Parametry

*bValid*<br/>
Ma wartość TRUE, jeśli formant jest prawidłowy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="cstockpropimplput_window"></a><a name="put_window"></a> CStockPropImpl::p ut_Window

Ta metoda wywołuje [CStockPropImpl::p ut_HWND](#put_hwnd), która zwraca E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
Uchwyt okna.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_FAIL.

### <a name="remarks"></a>Uwagi

Uchwyt okna to wartość tylko do odczytu.

## <a name="cstockpropimplputref_font"></a><a name="putref_font"></a> CStockPropImpl::p utref_Font

Wywołaj tę metodę, aby ustawić właściwości czcionki kontrolki z liczbą odwołań.

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Wskaźnik do właściwości czcionki kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Taka sama jak [CStockPropImpl::p ut_Font](#put_font), ale z liczbą odwołań.

## <a name="cstockpropimplputref_mouseicon"></a><a name="putref_mouseicon"></a> CStockPropImpl::p utref_MouseIcon

Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), które mają być wyświetlane, gdy wskaźnik myszy znajduje się nad kontrolką, z liczbą odwołań.

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Wskaźnik do właściwości obrazu grafiki.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Taka sama jak [CStockPropImpl::p ut_MouseIcon](#put_mouseicon), ale z liczbą odwołań.

## <a name="cstockpropimplputref_picture"></a><a name="putref_picture"></a> CStockPropImpl::p utref_Picture

Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikony, mapy bitowej lub metapliku), która ma być wyświetlana z liczbą odwołań.

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Wskaźnik do właściwości obrazu. Aby uzyskać więcej informacji, zobacz [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) .

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Taka sama jak [CStockPropImpl::p ut_Picture](#put_picture), ale z liczbą odwołań.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa IDispatchImpl](../../atl/reference/idispatchimpl-class.md)
