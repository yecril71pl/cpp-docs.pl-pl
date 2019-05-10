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
ms.openlocfilehash: 246e2a26db6adde0fec06523c1b8db09c5f552f3
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221061"
---
# <a name="cstockpropimpl-class"></a>Klasa CStockPropImpl

Ta klasa dostarcza metody do obsługi wartości właściwości podstawowych.

> [!IMPORTANT]
> Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
Klasa Implementowanie formantu i wynikające z `CStockPropImpl`.

*InterfaceName*<br/>
Udostępnianie właściwości podstawowe podwójnego interfejsu.

*piid*<br/>
Wskaźnik do identyfikatora IID z `InterfaceName`.

*plibid*<br/>
Wskaźnik do identyfikatora LIBID biblioteki typów, zawierający definicję `InterfaceName`.

*wMajor*<br/>
Wersja główna biblioteki typów. Wartość domyślna to 1.

*wMinor*<br/>
Wersja pomocnicza biblioteki typów. Wartość domyślna to 0.

*tihclass*<br/>
Klasa używana do zarządzania informacji o typie *T*. Wartość domyślna to `CComTypeInfoHolder`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|[get_Appearance](#get_appearance)|Wywołaj tę metodę, aby uzyskać paint style używane przez kontrolkę, na przykład, płaskiego lub 3W.|
|[get_AutoSize](#get_autosize)|Wywołaj tę metodę, aby wyświetlić stan flagę wskazującą, jeśli formant nie może być dowolnym rozmiarze.|
|[get_BackColor](#get_backcolor)|Wywołaj tę metodę, aby pobrać kolor tła formantu.|
|[get_BackStyle](#get_backstyle)|Wywołaj tę metodę, aby uzyskać styl tła kontrolki, przezroczystego lub nieprzezroczystego.|
|[get_BorderColor](#get_bordercolor)|Wywołaj tę metodę, aby pobrać kolor obramowania formantu.|
|[get_BorderStyle](#get_borderstyle)|Wywołaj tę metodę, aby pobrać styl obramowania formantu.|
|[get_BorderVisible](#get_bordervisible)|Wywołaj tę metodę, aby wyświetlić stan flagę wskazującą, czy obramowanie formantu jest widoczne.|
|[get_BorderWidth](#get_borderwidth)|Wywołaj tę metodę, aby uzyskać szerokość obramowania formantu (w pikselach).|
|[get_Caption](#get_caption)|Wywołaj tę metodę można pobrać z tekstem określonym w podpis obiektu.|
|[get_DrawMode](#get_drawmode)|Wywołaj tę metodę, aby uzyskać tryb rysowania kontrolki, na przykład pióro XOR lub Odwróć kolory.|
|[get_DrawStyle](#get_drawstyle)|Wywołaj tę metodę, aby pobrać styl rysowania kontrolki, na przykład, stały, kreskowana lub kropkowana.|
|[get_DrawWidth](#get_drawwidth)|Wywołaj tę metodę, aby pobrać rysowania szerokość (w pikselach) używany przez metody rysowanie formantu.|
|[get_Enabled](#get_enabled)|Wywołaj tę metodę, aby wyświetlić stan flagi, która wskazuje, czy kontrolka jest włączona.|
|[get_FillColor](#get_fillcolor)|Wywołaj tę metodę, aby pobrać kolor wypełnienia kontrolki.|
|[get_FillStyle](#get_fillstyle)|Wywołaj tę metodę, aby pobrać styl wypełnienia kontrolki, na przykład, stały, przezroczyste lub zakreskowany.|
|[get_Font](#get_font)|Wywołaj tę metodę, aby uzyskać wskaźnik do właściwości czcionki formantu.|
|[get_ForeColor](#get_forecolor)|Wywołaj tę metodę, aby pobrać kolor pierwszego planu formantu.|
|[get_HWND](#get_hwnd)|Wywołaj tę metodę można pobrać uchwytu okna skojarzonego z kontrolką.|
|[get_MouseIcon](#get_mouseicon)|Wywołaj tę metodę można pobrać właściwości obrazu grafiki (ikony, mapy bitowej lub metaplik), które będzie wyświetlana, gdy wskaźnik myszy znajduje się nad formantem.|
|[get_MousePointer](#get_mousepointer)|Wywołaj tę metodę w celu uzyskania typu wskaźnika myszy wyświetlane, gdy wskaźnik myszy znajduje się nad formantem, na przykład, strzałki, między lub Klepsydra.|
|[get_Picture](#get_picture)|Wywołaj tę metodę, aby uzyskać wskaźnik do właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), które mają być wyświetlane.|
|[get_ReadyState](#get_readystate)|Wywołaj tę metodę można pobrać stanu gotowości kontrolki, na przykład, ładowanie lub załadować.|
|[get_TabStop](#get_tabstop)|Wywołaj tę metodę, aby pobrać flagę, która wskazuje, czy kontrolka jest tabulatora.|
|[get_Text](#get_text)|Wywołaj tę metodę, aby uzyskać tekst, który jest wyświetlany formantu.|
|[getvalid](#get_valid)|Wywołaj tę metodę można pobrać stanu flagę wskazującą, czy kontrolka jest prawidłowy.|
|[get_Window](#get_window)|Wywołaj tę metodę można pobrać uchwytu okna skojarzonego z kontrolką. Taka sama jak [CStockPropImpl::get_HWND](#get_hwnd).|
|[put_Appearance](#put_appearance)|Wywołaj tę metodę, aby ustawić paint style używane przez kontrolkę, na przykład, płaskiego lub 3W.|
|[put_AutoSize](#put_autosize)|Wywołaj tę metodę można ustawić wartości flagę wskazującą, jeśli formant nie może być dowolnym rozmiarze.|
|[put_BackColor](#put_backcolor)|Wywołaj tę metodę, aby ustawić kolor tła formantu.|
|[put_BackStyle](#put_backstyle)|Wywołaj tę metodę, aby ustawić styl tła formantu.|
|[put_BorderColor](#put_bordercolor)|Wywołaj tę metodę, aby ustawić kolor obramowania formantu.|
|[put_BorderStyle](#put_borderstyle)|Wywołaj tę metodę, aby ustawić styl obramowania formantu.|
|[put_BorderVisible](#put_bordervisible)|Wywołaj tę metodę można ustawić wartości flagę wskazującą, czy obramowanie formantu jest widoczne.|
|[put_BorderWidth](#put_borderwidth)|Wywołaj tę metodę, aby ustawić szerokość obramowania formantu.|
|[put_Caption](#put_caption)|Wywołaj tę metodę, aby ustawić tekst wyświetlany formantu.|
|[put_DrawMode](#put_drawmode)|Wywołaj tę metodę, aby ustawić tryb rysowania kontrolki, na przykład pióro XOR lub Odwróć kolory.|
|[put_DrawStyle](#put_drawstyle)|Wywołaj tę metodę, aby ustawić styl rysowania kontrolki, na przykład, stały, kreskowana lub kropkowana.|
|[put_DrawWidth](#put_drawwidth)|Wywołaj tę metodę, aby ustawić szerokość (w pikselach) używany przez metody rysowanie formantu.|
|[put_Enabled](#put_enabled)|Wywołaj tę metodę, aby ustawić flagę, która wskazuje, czy kontrolka jest włączona.|
|[put_FillColor](#put_fillcolor)|Wywołaj tę metodę, aby ustawić kolor wypełnienia kontrolki.|
|[put_FillStyle](#put_fillstyle)|Wywołaj tę metodę, aby ustawić styl wypełnienia kontrolki, na przykład, stały, przezroczyste lub zakreskowany.|
|[put_Font](#put_font)|Wywołaj tę metodę można ustawić właściwości czcionki formantu.|
|[put_ForeColor](#put_forecolor)|Wywołaj tę metodę, aby ustawić kolor pierwszego planu formantu.|
|[put_HWND](#put_hwnd)|Ta metoda zwraca E_FAIL.|
|[put_MouseIcon](#put_mouseicon)|Wywołaj tę metodę można ustawić właściwości obrazu grafiki (ikony, mapy bitowej lub metaplik), które będzie wyświetlana, gdy wskaźnik myszy znajduje się nad formantem.|
|[put_MousePointer](#put_mousepointer)|Wywołaj tę metodę, aby ustawić automatyczny typ wskaźnika myszy wyświetlane, gdy wskaźnik myszy znajduje się nad formantem, na przykład, strzałki, między lub Klepsydra.|
|[put_Picture](#put_picture)|Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), które mają być wyświetlane.|
|[put_ReadyState](#put_readystate)|Wywołanie tej metody do ustawiania stanu gotowości kontrolki, na przykład, ładowanie lub załadowane.|
|[put_TabStop](#put_tabstop)|Wywołaj tę metodę, aby ustawić wartość flagi, która wskazuje, czy kontrolka jest tabulatora.|
|[put_Text](#put_text)|Wywołaj tę metodę, aby ustawić tekst, który jest wyświetlany formantu.|
|[putvalid](#put_valid)|Wywołaj tę metodę, aby ustawić flagę wskazującą, czy kontrolka jest prawidłowy.|
|[put_Window](#put_window)|Ta metoda wywołuje [CStockPropImpl::put_HWND](#put_hwnd), która zwraca E_FAIL.|
|[putref_Font](#putref_font)|Wywołaj tę metodę można ustawić właściwości czcionki formantu, za pomocą licznika odwołań.|
|[putref_MouseIcon](#putref_mouseicon)|Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikony, mapy bitowej lub metaplik), które będzie wyświetlana, gdy wskaźnik myszy znajduje się nad kontrolki, za pomocą licznika odwołań.|
|[putref_Picture](#putref_picture)|Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), które mają być wyświetlane za pomocą licznika odwołań.|

## <a name="remarks"></a>Uwagi

`CStockPropImpl` udostępnia **umieścić** i **uzyskać** metody dla każdej właściwości podstawowych. Te metody Podaj kod ustawić lub pobrać element członkowski danych skojarzone z każdą właściwość i który będzie powiadamiany, a następnie zsynchronizować z kontenerem po zmianie dowolną właściwość.

Program Visual Studio zapewnia obsługę właściwości podstawowe za pośrednictwem jego kreatorów. Aby uzyskać więcej informacji na temat Dodawanie właściwości standardowych do kontrolki, zobacz [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md).

W celu zapewnienia zgodności z poprzednimi wersjami `CStockPropImpl` udostępnia również `get_Window` i `put_Window` metody odwołujące się po prostu `get_HWND` i `put_HWND`, odpowiednio. Domyślna implementacja klasy `put_HWND` zwraca E_FAIL, ponieważ HWND powinny być właściwością tylko do odczytu.

Następujące właściwości również mają **putref** implementacji:

- Czcionka

- MouseIcon

- Obraz

Te same trzy właściwości podstawowych wymagają ich odpowiedni element członkowski danych typu `CComPtr` lub innej klasy, który zawiera odwołanie interfejsu poprawne inwentaryzacji za pomocą operatora przypisania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`T`

[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="get_appearance"></a>  CStockPropImpl::get_Appearance

Wywołaj tę metodę, aby uzyskać paint style używane przez kontrolkę, na przykład, płaskiego lub 3W.

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>Parametry

*pnAppearance*<br/>
Zmienna, która odbiera stylu malowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_autosize"></a>  CStockPropImpl::get_AutoSize

Wywołaj tę metodę, aby wyświetlić stan flagę wskazującą, jeśli formant nie może być dowolnym rozmiarze.

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>Parametry

*pbAutoSize*<br/>
Zmienna, która otrzymuje stan flagi. Wartość TRUE wskazuje, że kontrolka nie może być dowolnym rozmiarze.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_backcolor"></a>  CStockPropImpl::get_BackColor

Wywołaj tę metodę, aby pobrać kolor tła formantu.

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>Parametry

*pclrBackColor*<br/>
Zmienna, która odbiera kolor tła formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_backstyle"></a>  CStockPropImpl::get_BackStyle

Wywołaj tę metodę, aby uzyskać styl tła kontrolki, przezroczystego lub nieprzezroczystego.

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>Parametry

*pnBackStyle*<br/>
Zmienna, która odbiera styl tła formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_bordercolor"></a>  CStockPropImpl::get_BorderColor

Wywołaj tę metodę, aby pobrać kolor obramowania formantu.

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>Parametry

*pclrBorderColor*<br/>
Zmienna, która odbiera kolor obramowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_borderstyle"></a>  CStockPropImpl::get_BorderStyle

Wywołaj tę metodę, aby pobrać styl obramowania formantu.

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>Parametry

*pnBorderStyle*<br/>
Zmienna, która odbiera styl obramowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_bordervisible"></a>  CStockPropImpl::get_BorderVisible

Wywołaj tę metodę, aby wyświetlić stan flagę wskazującą, czy obramowanie formantu jest widoczne.

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>Parametry

*pbBorderVisible*<br/>
Zmienna, która otrzymuje stan flagi. Wartość TRUE wskazuje, że obramowania kontrolki jest widoczna.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_borderwidth"></a>  CStockPropImpl::get_BorderWidth

Wywołaj tę metodę, aby uzyskać szerokość obramowania formantu.

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>Parametry

*pnBorderWidth*<br/>
Zmienna, która odbiera szerokość obramowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_caption"></a>  CStockPropImpl::get_Caption

Wywołaj tę metodę można pobrać z tekstem określonym w podpis obiektu.

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>Parametry

*pbstrCaption*<br/>
Tekst, który ma być wyświetlany formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_drawmode"></a>  CStockPropImpl::get_DrawMode

Wywołaj tę metodę, aby uzyskać tryb rysowania kontrolki, na przykład pióro XOR lub Odwróć kolory.

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>Parametry

*pnDrawMode*<br/>
Zmienna, która odbiera tryb rysowania kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_drawstyle"></a>  CStockPropImpl::get_DrawStyle

Wywołaj tę metodę, aby pobrać styl rysowania kontrolki, na przykład, stały, kreskowana lub kropkowana.

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>Parametry

*pnDrawStyle*<br/>
Zmienna, która odbiera styl rysowania kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_drawwidth"></a>  CStockPropImpl::get_DrawWidth

Wywołaj tę metodę, aby pobrać rysowania szerokość (w pikselach) używany przez metody rysowanie formantu.

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>Parametry

*pnDrawWidth*<br/>
Zmienna, która odbiera wartość szerokości kontrolki, w pikselach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_enabled"></a>  CStockPropImpl::get_Enabled

Wywołaj tę metodę, aby wyświetlić stan flagi, która wskazuje, czy kontrolka jest włączona.

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>Parametry

*pbEnabled*<br/>
Zmienna, która otrzymuje stan flagi. Wartość TRUE wskazuje, czy kontrolka jest włączona.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_fillcolor"></a>  CStockPropImpl::get_FillColor

Wywołaj tę metodę, aby pobrać kolor wypełnienia kontrolki.

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>Parametry

*pclrFillColor*<br/>
Zmienna, która odbiera kolor wypełnienia kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_fillstyle"></a>  CStockPropImpl::get_FillStyle

Wywołaj tę metodę, aby pobrać styl wypełnienia kontrolki, na przykład, stały, przezroczyste lub crosshatched.

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>Parametry

*pnFillStyle*<br/>
Zmienna, która odbiera styl wypełnienia kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_font"></a>  CStockPropImpl::get_Font

Wywołaj tę metodę, aby uzyskać wskaźnik do właściwości czcionki formantu.

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parametry

*ppFont*<br/>
Zmienna, która otrzymuje wskaźnik do właściwości czcionki formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_forecolor"></a>  CStockPropImpl::get_ForeColor

Wywołaj tę metodę, aby pobrać kolor pierwszego planu formantu.

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>Parametry

*pclrForeColor*<br/>
Zmienna, która odbiera kontrolek Kolor pierwszego planu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_hwnd"></a>  CStockPropImpl::get_HWND

Wywołaj tę metodę można pobrać uchwytu okna skojarzonego z kontrolką.

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parametry

*phWnd*<br/>
Uchwyt okna skojarzonego z kontrolką.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_mouseicon"></a>  CStockPropImpl::get_MouseIcon

Wywołaj tę metodę można pobrać właściwości obrazu grafiki (ikony, mapy bitowej lub metaplik), które będzie wyświetlana, gdy wskaźnik myszy znajduje się nad formantem.

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parametry

*ppPicture*<br/>
Zmienna, która otrzymuje wskaźnik do właściwości obrazu grafiki.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_mousepointer"></a>  CStockPropImpl::get_MousePointer

Wywołaj tę metodę w celu uzyskania typu wskaźnika myszy wyświetlane, gdy wskaźnik myszy znajduje się nad formantem, na przykład, strzałki, między lub Klepsydra.

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>Parametry

*pnMousePointer*<br/>
Zmienna, która otrzymuje typ wskaźnika myszy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_picture"></a>  CStockPropImpl::get_Picture

Wywołaj tę metodę, aby uzyskać wskaźnik do właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), które mają być wyświetlane.

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Parametry

*ppPicture*<br/>
Zmienna, która otrzymuje wskaźnik do właściwości obrazu. Zobacz [elementu IPictureDisp](/windows/desktop/api/ocidl/nn-ocidl-ipicturedisp) Aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_readystate"></a>  CStockPropImpl::get_ReadyState

Wywołaj tę metodę można pobrać stanu gotowości kontrolki, na przykład, ładowanie lub załadować.

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>Parametry

*pnReadyState*<br/>
Zmienna, która odbiera formantu stanu gotowości.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_tabstop"></a>  CStockPropImpl::get_TabStop

Wywołaj tę metodę, aby pobrać stan flagi, która wskazuje, czy kontrolka jest tabulatora.

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>Parametry

*pbTabStop*<br/>
Zmienna, która otrzymuje stan flagi. Wartość TRUE wskazuje, czy kontrolka jest tabulatora.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_text"></a>  CStockPropImpl::get_Text

Wywołaj tę metodę, aby uzyskać tekst, który jest wyświetlany formantu.

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>Parametry

*pbstrText*<br/>
Tekst, który jest wyświetlany formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_valid"></a>  CStockPropImpl::getvalid

Wywołaj tę metodę można pobrać stanu flagę wskazującą, czy kontrolka jest prawidłowy.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>Parametry

*pbValid*<br/>
Zmienna, która otrzymuje stan flagi. Wartość TRUE wskazuje, czy kontrolka jest nieprawidłowy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="get_window"></a>  CStockPropImpl::get_Window

Wywołaj tę metodę można pobrać uchwytu okna skojarzonego z kontrolką. Taka sama jak [CStockPropImpl::get_HWND](#get_hwnd).

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Parametry

*phWnd*<br/>
Uchwyt okna skojarzonego z kontrolką.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_appearance"></a>  CStockPropImpl::put_Appearance

Wywołaj tę metodę, aby ustawić paint style używane przez kontrolkę, na przykład, płaskiego lub 3W.

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>Parametry

*nAppearance*<br/>
Nowy styl paint używanego przez formant.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_autosize"></a>  CStockPropImpl::put_AutoSize

Wywołaj tę metodę, aby ustawić wartość flagi wskazującą, jeśli formant nie może być dowolnym rozmiarze.

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>Parametry

*bAutoSize*<br/>
Wartość TRUE, jeśli formant nie może być dowolnym rozmiarze.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_backcolor"></a>  CStockPropImpl::put_BackColor

Wywołaj tę metodę, aby ustawić kolor tła formantu.

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>Parametry

*clrBackColor*<br/>
Nowy kolor tła kontrolki.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_backstyle"></a>  CStockPropImpl::put_BackStyle

Wywołaj tę metodę, aby ustawić styl tła formantu.

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>Parametry

*nBackStyle*<br/>
Nowy styl tła formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_bordercolor"></a>  CStockPropImpl::put_BorderColor

Wywołaj tę metodę, aby ustawić kolor obramowania formantu.

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>Parametry

*clrBorderColor*<br/>
Nowy kolor obramowania. Typ danych OLE_COLOR wewnętrznie jest przedstawiana jako 32-bitowa liczba całkowita typu long.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_borderstyle"></a>  CStockPropImpl::put_BorderStyle

Wywołaj tę metodę, aby ustawić styl obramowania formantu.

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>Parametry

*nBorderStyle*<br/>
Nowy styl obramowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_bordervisible"></a>  CStockPropImpl::put_BorderVisible

Wywołaj tę metodę można ustawić wartości flagę wskazującą, czy obramowanie formantu jest widoczne.

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>Parametry

*bBorderVisible*<br/>
Wartość TRUE, jeśli ma być widoczne obramowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_borderwidth"></a>  CStockPropImpl::put_BorderWidth

Wywołaj tę metodę, aby ustawić szerokość obramowania formantu.

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>Parametry

*nBorderWidth*<br/>
Nową szerokość obramowania formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_caption"></a>  CStockPropImpl::put_Caption

Wywołaj tę metodę, aby ustawić tekst wyświetlany formantu.

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>Parametry

*bstrCaption*<br/>
Tekst, który ma być wyświetlany formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_drawmode"></a>  CStockPropImpl::put_DrawMode

Wywołaj tę metodę, aby ustawić tryb rysowania kontrolki, na przykład pióro XOR lub Odwróć kolory.

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>Parametry

*nDrawMode*<br/>
Tryb rysowania nowego formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_drawstyle"></a>  CStockPropImpl::put_DrawStyle

Wywołaj tę metodę, aby ustawić styl rysowania kontrolki, na przykład, stały, kreskowana lub kropkowana.

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>Parametry

*nDrawStyle*<br/>
Styl rysowania nowego formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_drawwidth"></a>  CStockPropImpl::put_DrawWidth

Wywołaj tę metodę, aby ustawić szerokość (w pikselach) używany przez metody rysowanie formantu.

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>Parametry

*nDrawWidth*<br/>
Nową szerokość ma być używany przez formant rysowania metody.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_enabled"></a>  CStockPropImpl::put_Enabled

Wywołaj tę metodę, aby ustawić wartość flagi, która wskazuje, czy kontrolka jest włączona.

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*bWłączony*<br/>
Wartość TRUE, jeśli kontrolka jest włączona.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_fillcolor"></a>  CStockPropImpl::put_FillColor

Wywołaj tę metodę, aby ustawić kolor wypełnienia kontrolki.

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>Parametry

*clrFillColor*<br/>
Nowy kolor wypełnienia dla formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_fillstyle"></a>  CStockPropImpl::put_FillStyle

Wywołaj tę metodę, aby ustawić styl wypełnienia kontrolki, na przykład, stały, przezroczyste lub zakreskowany.

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>Parametry

*nFillStyle*<br/>
Styl wypełnienia nowego formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_font"></a>  CStockPropImpl::put_Font

Wywołaj tę metodę można ustawić właściwości czcionki formantu.

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Wskaźnik do właściwości czcionki formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_forecolor"></a>  CStockPropImpl::put_ForeColor

Wywołaj tę metodę, aby ustawić kolor pierwszego planu formantu.

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>Parametry

*clrForeColor*<br/>
Nowy kolor pierwszego planu formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_hwnd"></a>  CStockPropImpl::put_HWND

Ta metoda zwraca E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Zastrzeżone.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_FAIL.

### <a name="remarks"></a>Uwagi

Uchwyt okna jest to wartość tylko do odczytu.

##  <a name="put_mouseicon"></a>  CStockPropImpl::put_MouseIcon

Wywołaj tę metodę można ustawić właściwości obrazu grafiki (ikony, mapy bitowej lub metaplik), które będzie wyświetlana, gdy wskaźnik myszy znajduje się nad formantem.

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Wskaźnik do właściwości obrazu grafiki.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_mousepointer"></a>  CStockPropImpl::put_MousePointer

Wywołaj tę metodę, aby ustawić automatyczny typ wskaźnika myszy wyświetlane, gdy wskaźnik myszy znajduje się nad formantem, na przykład, strzałki, między lub Klepsydra.

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>Parametry

*nMousePointer*<br/>
Typ wskaźnika myszy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_picture"></a>  CStockPropImpl::put_Picture

Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), które mają być wyświetlane.

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Wskaźnik do właściwości obrazu. Zobacz [elementu IPictureDisp](/windows/desktop/api/ocidl/nn-ocidl-ipicturedisp) Aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_readystate"></a>  CStockPropImpl::put_ReadyState

Wywołanie tej metody do ustawiania stanu gotowości kontrolki, na przykład, ładowanie lub załadowane.

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>Parametry

*nReadyState*<br/>
Kontrola stanu gotowości.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_tabstop"></a>  CStockPropImpl::put_TabStop

Wywołaj tę metodę, aby ustawić flagę, która wskazuje, czy kontrolka jest tabulatora.

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>Parametry

*bTabStop*<br/>
Wartość TRUE, jeśli kontrolka jest tabulatora.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_text"></a>  CStockPropImpl::put_Text

Wywołaj tę metodę, aby ustawić tekst, który jest wyświetlany formantu.

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>Parametry

*bstrText*<br/>
Tekst, który jest wyświetlany formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_valid"></a>  CStockPropImpl::putvalid

Wywołaj tę metodę, aby ustawić flagę wskazującą, czy kontrolka jest prawidłowy.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>Parametry

*bValid*<br/>
Wartość TRUE, jeśli kontrolka jest nieprawidłowy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="put_window"></a>  CStockPropImpl::put_Window

Ta metoda wywołuje [CStockPropImpl::put_HWND](#put_hwnd), która zwraca E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Uchwyt okna.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_FAIL.

### <a name="remarks"></a>Uwagi

Uchwyt okna jest to wartość tylko do odczytu.

##  <a name="putref_font"></a>  CStockPropImpl::putref_Font

Wywołaj tę metodę można ustawić właściwości czcionki formantu, za pomocą licznika odwołań.

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Wskaźnik do właściwości czcionki formantu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Taka sama jak [CStockPropImpl::put_Font](#put_font), ale liczby odwołań.

##  <a name="putref_mouseicon"></a>  CStockPropImpl::putref_MouseIcon

Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikony, mapy bitowej lub metaplik), które będzie wyświetlana, gdy wskaźnik myszy znajduje się nad kontrolki, za pomocą licznika odwołań.

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Wskaźnik do właściwości obrazu grafiki.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Taka sama jak [CStockPropImpl::put_MouseIcon](#put_mouseicon), ale liczby odwołań.

##  <a name="putref_picture"></a>  CStockPropImpl::putref_Picture

Wywołaj tę metodę, aby ustawić właściwości obrazu grafiki (ikona, mapa bitowa lub metaplik), które mają być wyświetlane za pomocą licznika odwołań.

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Parametry

*pPicture*<br/>
Wskaźnik do właściwości obrazu. Zobacz [elementu IPictureDisp](/windows/desktop/api/ocidl/nn-ocidl-ipicturedisp) Aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Taka sama jak [CStockPropImpl::put_Picture](#put_picture), ale liczby odwołań.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasa IDispatchImpl](../../atl/reference/idispatchimpl-class.md)
