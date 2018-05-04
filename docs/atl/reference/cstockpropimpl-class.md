---
title: Klasa CStockPropImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CStockPropImpl class
- controls [ATL], stock properties
- stock properties, ATL controls
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f12cff287b9a9c74b548a08d9a03f73869671fc1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cstockpropimpl-class"></a>Klasa CStockPropImpl
Ta klasa dostarcza metody do obsługi wartości właściwości standardowych.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T, class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CcomTypeInfoHolder>  
class ATL_NO_VTABLE CStockPropImpl : public IDispatchImpl<InterfaceName, piid,
 plibid,
    wMajor,
 wMinor,
    tihclass>
```   
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasa implementacja formantu i wynikające z `CStockPropImpl`.  
  
 `InterfaceName`  
 Interfejs podwójny udostępnianie właściwości standardowych.  
  
 `piid`  
 Wskaźnik na celu uzyskanie identyfikatora IID `InterfaceName`.  
  
 `plibid`  
 Wskaźnik do identyfikatora LIBID biblioteki typów zawierający definicję `InterfaceName`.  
  
 `wMajor`  
 Wersja główna biblioteki typów. Wartość domyślna to 1.  
  
 `wMinor`  
 Wersja pomocnicza biblioteki typów. Wartość domyślna to 0.  
  
 `tihclass`  
 Klasa używana do zarządzania informacji o typie `T`. Wartość domyślna to `CComTypeInfoHolder`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|[get_Appearance](#get_appearance)|Wywołaj tę metodę, aby uzyskać paint styl używany przez formant, na przykład, płaskim lub 3W.|  
|[get_AutoSize](#get_autosize)|Wywołaj tę metodę w celu pobrania stanu flagę wskazującą, czy formant nie może być dowolnym rozmiarze.|  
|[get_BackColor](#get_backcolor)|Wywołaj tę metodę, aby pobrać kolor tła formantu.|  
|[get_BackStyle](#get_backstyle)|Wywołaj tę metodę, aby pobrać styl tła formantu, przezroczystego lub nieprzezroczystego.|  
|[get_BorderColor](#get_bordercolor)|Wywołaj tę metodę, aby pobrać kolor obramowania formantu.|  
|[get_BorderStyle](#get_borderstyle)|Wywołaj tę metodę, aby pobrać styl obramowania formantu.|  
|[get_BorderVisible](#get_bordervisible)|Wywołaj tę metodę w celu pobrania stanu flagę wskazującą, czy obramowania formantu jest widoczne.|  
|[get_BorderWidth](#get_borderwidth)|Wywołaj tę metodę, aby pobrać szerokość obramowania formantu (w pikselach).|  
|[get_Caption](#get_caption)|Wywołaj tę metodę, aby uzyskać tekst określony w nagłówku obiektu.|  
|[get_DrawMode](#get_drawmode)|Wywołaj tę metodę, aby pobrać tryb rysowania formantu, na przykład XOR pióro lub Odwróć kolory.|  
|[get_DrawStyle](#get_drawstyle)|Na przykład wywołać tę metodę, aby pobrać styl rysowania formantu, stały, przerywana lub kropkami.|  
|[get_DrawWidth](#get_drawwidth)|Wywołanie tej metody można pobrać metody rysowania formantu rysowania szerokość (w pikselach).|  
|[get_Enabled](#get_enabled)|Wywołaj tę metodę w celu pobrania stanu flagę wskazującą, czy formant jest włączony.|  
|[get_FillColor](#get_fillcolor)|Wywołaj tę metodę, aby pobrać kolor wypełnienia formantu.|  
|[get_FillStyle](#get_fillstyle)|Na przykład wywołać tę metodę, aby pobrać styl wypełnienia kontrolki, stały, przezroczysty lub zakreskowany.|  
|[get_Font](#get_font)|Wywołaj tę metodę, aby otrzymywać wskaźnik do właściwości czcionki formantu.|  
|[get_ForeColor](#get_forecolor)|Wywołaj tę metodę, aby pobrać kolor pierwszego planu formantu.|  
|[get_HWND](#get_hwnd)|Wywołanie tej metody można pobrać uchwytu okna skojarzony z formantem.|  
|[get_MouseIcon](#get_mouseicon)|Wywołanie tej metody można pobrać właściwości obrazu graficznego (ikony, mapa bitowa lub metaplik) do wyświetlenia, gdy wskaźnik myszy znajduje się nad formantem.|  
|[get_MousePointer](#get_mousepointer)|Wywołanie tej metody można pobrać typu wskaźnika myszy wyświetlane, gdy wskaźnik myszy znajduje się nad formantem, na przykład, strzałki, między lub Klepsydra.|  
|[get_Picture](#get_picture)|Wywołaj tę metodę, aby uzyskać wskaźnika graficznego (ikony, mapy bitowej lub metaplik), które mają być wyświetlane właściwości obrazu.|  
|[get_ReadyState](#get_readystate)|Wywołanie tej metody można pobrać stanu gotowości formantu, na przykład, ładowania lub załadować.|  
|[get_TabStop](#get_tabstop)|Wywołaj tę metodę, aby pobrać flagę wskazującą, czy formant jest tabulatora.|  
|[get_Text](#get_text)|Wywołanie tej metody, aby uzyskać tekst, który jest wyświetlany za pomocą formantu.|  
|[getvalid](#get_valid)|Wywołaj tę metodę w celu pobrania stanu flagę wskazującą, czy formant jest prawidłowy.|  
|[get_Window](#get_window)|Wywołanie tej metody można pobrać uchwytu okna skojarzony z formantem. Taki sam jak [CStockPropImpl::get_HWND](#get_hwnd).|  
|[put_Appearance](#put_appearance)|Wywołaj tę metodę, aby ustawić paint styl używany przez formant, na przykład, płaskim lub 3W.|  
|[put_AutoSize](#put_autosize)|Wywołanie tej metody można ustawić wartości flagę wskazującą, czy formant nie może być dowolnym rozmiarze.|  
|[put_BackColor](#put_backcolor)|Wywołaj tę metodę, aby ustawić kolor tła formantu.|  
|[put_BackStyle](#put_backstyle)|Wywołaj tę metodę, aby ustawić styl tła formantu.|  
|[put_BorderColor](#put_bordercolor)|Wywołaj tę metodę w celu ustawienia koloru obramowania formantu.|  
|[put_BorderStyle](#put_borderstyle)|Wywołaj tę metodę, aby ustawić styl obramowania formantu.|  
|[put_BorderVisible](#put_bordervisible)|Wywołanie tej metody można ustawić wartości flagę wskazującą, czy obramowania formantu jest widoczne.|  
|[put_BorderWidth](#put_borderwidth)|Wywołaj tę metodę, aby ustawić szerokość obramowania formantu.|  
|[put_Caption](#put_caption)|Wywołaj tę metodę, aby ustawić tekst, który ma być wyświetlane z formantem.|  
|[put_DrawMode](#put_drawmode)|Wywołaj tę metodę, aby ustawić tryb rysowania formantu, na przykład XOR pióro lub Odwróć kolory.|  
|[put_DrawStyle](#put_drawstyle)|Na przykład wywołać tę metodę, aby ustawić styl rysowania formantu, stały, przerywana lub kropkami.|  
|[put_DrawWidth](#put_drawwidth)|Wywołanie tej metody można ustawić szerokość (w pikselach) metody rysowania formantu.|  
|[put_Enabled](#put_enabled)|Wywołaj tę metodę, aby ustawić flagę wskazującą, czy formant jest włączony.|  
|[put_FillColor](#put_fillcolor)|Wywołaj tę metodę, aby ustawić kolor wypełnienia formantu.|  
|[put_FillStyle](#put_fillstyle)|Na przykład wywołać tę metodę, aby ustawić styl wypełnienia kontrolki, stały, przezroczysty lub zakreskowany.|  
|[put_Font](#put_font)|Wywołanie tej metody można ustawić właściwości czcionki formantu.|  
|[put_ForeColor](#put_forecolor)|Wywołaj tę metodę, aby ustawić kolor pierwszego planu formantu.|  
|[put_HWND](#put_hwnd)|Ta metoda zwraca E_FAIL.|  
|[put_MouseIcon](#put_mouseicon)|Wywołanie tej metody można ustawić właściwości obrazu graficznego (ikony, mapa bitowa lub metaplik) do wyświetlenia, gdy wskaźnik myszy znajduje się nad formantem.|  
|[put_MousePointer](#put_mousepointer)|Wywołanie tej metody, aby ustawić typ wskaźnika myszy wyświetlane, gdy wskaźnik myszy znajduje się nad formantem, na przykład, strzałki, między lub Klepsydra.|  
|[put_Picture](#put_picture)|Wywołanie tej metody można ustawić właściwości obrazu grafiki (ikony, mapy bitowej lub metaplik), które mają być wyświetlane.|  
|[put_ReadyState](#put_readystate)|Wywołanie tej metody można ustawić stanu gotowości formantu, na przykład, ładowania lub załadować.|  
|[put_TabStop](#put_tabstop)|Wywołanie tej metody można ustawić wartości flagę wskazującą, czy formant jest tabulatora.|  
|[put_Text](#put_text)|Wywołaj tę metodę, aby ustawić tekst, który jest wyświetlany za pomocą formantu.|  
|[putvalid](#put_valid)|Wywołaj tę metodę, aby ustawić flagę wskazującą, czy formant jest prawidłowy.|  
|[put_Window](#put_window)|Ta metoda wywołuje [CStockPropImpl::put_HWND](#put_hwnd), która zwraca E_FAIL.|  
|[putref_Font](#putref_font)|Wywołanie tej metody można ustawić właściwości czcionki formantu, wraz z liczbą odwołania.|  
|[putref_MouseIcon](#putref_mouseicon)|Wywołanie tej metody można ustawić właściwości obrazu graficznego (ikony, mapa bitowa lub metaplik) do wyświetlenia, gdy wskaźnik myszy znajduje się nad formantem, wraz z liczbą odwołania.|  
|[putref_Picture](#putref_picture)|Wywołanie tej metody można ustawić właściwości obrazu grafiki (ikony, mapy bitowej lub metaplik), które mają być wyświetlane, wraz z liczbą odwołania.|  
  
## <a name="remarks"></a>Uwagi  
 `CStockPropImpl` udostępnia **put** i **uzyskać** metod dla każdej właściwości standardowych. Te metody Podaj kod konieczne ustawić lub pobrać element członkowski danych skojarzony z każdą właściwość i powiadamia i synchronizowanie z kontenerem podczas zmiany żadnych właściwości.  
  
 Visual C++ obsługuje właściwości standardowych za pośrednictwem jego kreatorów. Aby uzyskać więcej informacji na temat Dodawanie właściwości standardowych do formantu, zobacz [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md).  
  
 W celu zapewnienia zgodności z poprzednimi wersjami `CStockPropImpl` udostępnia również `get_Window` i `put_Window` metod, które po prostu Wywołaj `get_HWND` i `put_HWND`odpowiednio. Domyślna implementacja `put_HWND` zwraca **E_FAIL** ponieważ `HWND` powinno być właściwością tylko do odczytu.  
  
 Następujące właściwości również mają **putref** implementacji:  
  
-   Czcionki  
  
-   MouseIcon  
  
-   Obraz  
  
 Te same właściwości standardowych trzy wymagają ich odpowiedniego elementu członkowskiego danych typu `CComPtr` lub inną klasę, która udostępnia odwołania poprawnego interfejsu inwentaryzacji za pomocą operatora przypisania.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `T`  
  
 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md)  
  
 `CStockPropImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="get_appearance"></a>  CStockPropImpl::get_Appearance  
 Wywołaj tę metodę, aby uzyskać paint styl używany przez formant, na przykład, płaskim lub 3W.  
  
```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```  
  
### <a name="parameters"></a>Parametry  
 *pnAppearance*  
 Zmienna, która odbiera styl malowanie formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_autosize"></a>  CStockPropImpl::get_AutoSize  
 Wywołaj tę metodę w celu pobrania stanu flagę wskazującą, czy formant nie może być dowolnym rozmiarze.  
  
```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```  
  
### <a name="parameters"></a>Parametry  
 *pbAutoSize*  
 Zmienna, która otrzymuje stan flagi. Wartość TRUE wskazuje, że formant nie może być dowolnym rozmiarze.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_backcolor"></a>  CStockPropImpl::get_BackColor  
 Wywołaj tę metodę, aby pobrać kolor tła formantu.  
  
```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```  
  
### <a name="parameters"></a>Parametry  
 *pclrBackColor*  
 Zmienna, która odbiera kolor tła formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_backstyle"></a>  CStockPropImpl::get_BackStyle  
 Wywołaj tę metodę, aby pobrać styl tła formantu, przezroczystego lub nieprzezroczystego.  
  
```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *pnBackStyle*  
 Zmienna, która odbiera styl tła formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_bordercolor"></a>  CStockPropImpl::get_BorderColor  
 Wywołaj tę metodę, aby pobrać kolor obramowania formantu.  
  
```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```  
  
### <a name="parameters"></a>Parametry  
 *pclrBorderColor*  
 Zmienna, która odbiera kolor obramowania formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_borderstyle"></a>  CStockPropImpl::get_BorderStyle  
 Wywołaj tę metodę, aby pobrać styl obramowania formantu.  
  
```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *pnBorderStyle*  
 Zmienna, która odbiera styl obramowania formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_bordervisible"></a>  CStockPropImpl::get_BorderVisible  
 Wywołaj tę metodę w celu pobrania stanu flagę wskazującą, czy obramowania formantu jest widoczne.  
  
```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```  
  
### <a name="parameters"></a>Parametry  
 *pbBorderVisible*  
 Zmienna, która otrzymuje stan flagi. Wartość TRUE wskazuje, że obramowania formantu jest widoczny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_borderwidth"></a>  CStockPropImpl::get_BorderWidth  
 Wywołaj tę metodę, aby pobrać szerokość obramowania formantu.  
  
```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *pnBorderWidth*  
 Zmienna, która odbiera szerokość obramowania formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_caption"></a>  CStockPropImpl::get_Caption  
 Wywołaj tę metodę, aby uzyskać tekst określony w nagłówku obiektu.  
  
```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```  
  
### <a name="parameters"></a>Parametry  
 *pbstrCaption*  
 Tekst, który ma być wyświetlane z formantem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_drawmode"></a>  CStockPropImpl::get_DrawMode  
 Wywołaj tę metodę, aby pobrać tryb rysowania formantu, na przykład XOR pióro lub Odwróć kolory.  
  
```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```  
  
### <a name="parameters"></a>Parametry  
 *pnDrawMode*  
 Zmienna, która odbiera tryb rysowania formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_drawstyle"></a>  CStockPropImpl::get_DrawStyle  
 Na przykład wywołać tę metodę, aby pobrać styl rysowania formantu, stały, przerywana lub kropkami.  
  
```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *pnDrawStyle*  
 Zmienna, która odbiera styl rysowania formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_drawwidth"></a>  CStockPropImpl::get_DrawWidth  
 Wywołanie tej metody można pobrać metody rysowania formantu rysowania szerokość (w pikselach).  
  
```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *pnDrawWidth*  
 Zmienna, która odbiera wartość szerokości formantu w pikselach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_enabled"></a>  CStockPropImpl::get_Enabled  
 Wywołaj tę metodę w celu pobrania stanu flagę wskazującą, czy formant jest włączony.  
  
```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```  
  
### <a name="parameters"></a>Parametry  
 `pbEnabled`  
 Zmienna, która otrzymuje stan flagi. Wartość TRUE wskazuje, czy formant jest włączony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_fillcolor"></a>  CStockPropImpl::get_FillColor  
 Wywołaj tę metodę, aby pobrać kolor wypełnienia formantu.  
  
```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```  
  
### <a name="parameters"></a>Parametry  
 *pclrFillColor*  
 Zmienna, która odbiera kolor wypełnienia formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_fillstyle"></a>  CStockPropImpl::get_FillStyle  
 Na przykład wywołać tę metodę, aby pobrać styl wypełnienia kontrolki, stały, przezroczysty lub crosshatched.  
  
```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *pnFillStyle*  
 Zmienna, która odbiera styl wypełnienia formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_font"></a>  CStockPropImpl::get_Font  
 Wywołaj tę metodę, aby otrzymywać wskaźnik do właściwości czcionki formantu.  
  
```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```  
  
### <a name="parameters"></a>Parametry  
 `ppFont`  
 Zmienna, która otrzymuje wskaźnik właściwości czcionki formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_forecolor"></a>  CStockPropImpl::get_ForeColor  
 Wywołaj tę metodę, aby pobrać kolor pierwszego planu formantu.  
  
```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```  
  
### <a name="parameters"></a>Parametry  
 *pclrForeColor*  
 Zmienna, która odbiera kolor pierwszego planu formantów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_hwnd"></a>  CStockPropImpl::get_HWND  
 Wywołanie tej metody można pobrać uchwytu okna skojarzony z formantem.  
  
```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `phWnd`  
 Uchwyt okna skojarzony z formantem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_mouseicon"></a>  CStockPropImpl::get_MouseIcon  
 Wywołanie tej metody można pobrać właściwości obrazu graficznego (ikony, mapa bitowa lub metaplik) do wyświetlenia, gdy wskaźnik myszy znajduje się nad formantem.  
  
```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```  
  
### <a name="parameters"></a>Parametry  
 `ppPicture`  
 Zmienna, która otrzymuje wskaźnik właściwości obrazu grafiki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_mousepointer"></a>  CStockPropImpl::get_MousePointer  
 Wywołanie tej metody można pobrać typu wskaźnika myszy wyświetlane, gdy wskaźnik myszy znajduje się nad formantem, na przykład, strzałki, między lub Klepsydra.  
  
```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```  
  
### <a name="parameters"></a>Parametry  
 *pnMousePointer*  
 Zmienna, która odbiera typ wskaźnika myszy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_picture"></a>  CStockPropImpl::get_Picture  
 Wywołaj tę metodę, aby uzyskać wskaźnika graficznego (ikony, mapy bitowej lub metaplik), które mają być wyświetlane właściwości obrazu.  
  
```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```  
  
### <a name="parameters"></a>Parametry  
 `ppPicture`  
 Zmienna, która otrzymuje wskaźnik właściwości obrazu. Zobacz [IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762) więcej szczegółów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_readystate"></a>  CStockPropImpl::get_ReadyState  
 Wywołanie tej metody można pobrać stanu gotowości formantu, na przykład, ładowania lub załadować.  
  
```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```  
  
### <a name="parameters"></a>Parametry  
 *pnReadyState*  
 Zmienna, która odbiera formantu stanie gotowe.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_tabstop"></a>  CStockPropImpl::get_TabStop  
 Wywołaj tę metodę w celu pobrania stanu flagę wskazującą, czy formant jest tabulatora.  
  
```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```  
  
### <a name="parameters"></a>Parametry  
 *pbTabStop*  
 Zmienna, która otrzymuje stan flagi. Wartość TRUE wskazuje, że formant jest tabulatora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_text"></a>  CStockPropImpl::get_Text  
 Wywołanie tej metody, aby uzyskać tekst, który jest wyświetlany za pomocą formantu.  
  
```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```  
  
### <a name="parameters"></a>Parametry  
 *pbstrText*  
 Tekst, który jest wyświetlany za pomocą formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_valid"></a>  CStockPropImpl::getvalid  
 Wywołaj tę metodę w celu pobrania stanu flagę wskazującą, czy formant jest prawidłowy.  
  
```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```  
  
### <a name="parameters"></a>Parametry  
 *pbValid*  
 Zmienna, która otrzymuje stan flagi. Wartość TRUE wskazuje, że formant jest nieprawidłowy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="get_window"></a>  CStockPropImpl::get_Window  
 Wywołanie tej metody można pobrać uchwytu okna skojarzony z formantem. Taki sam jak [CStockPropImpl::get_HWND](#get_hwnd).  
  
```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `phWnd`  
 Uchwyt okna skojarzony z formantem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_appearance"></a>  CStockPropImpl::put_Appearance  
 Wywołaj tę metodę, aby ustawić paint styl używany przez formant, na przykład, płaskim lub 3W.  
  
```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```  
  
### <a name="parameters"></a>Parametry  
 `nAppearance`  
 Nowy styl paint używanego przez formant.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_autosize"></a>  CStockPropImpl::put_AutoSize  
 Wywołanie tej metody można ustawić wartości flagę wskazującą, czy formant nie może być dowolnym rozmiarze.  
  
```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```  
  
### <a name="parameters"></a>Parametry  
 *bAutoSize*  
 Wartość TRUE, jeśli formant nie może być dowolnym rozmiarze.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_backcolor"></a>  CStockPropImpl::put_BackColor  
 Wywołaj tę metodę, aby ustawić kolor tła formantu.  
  
```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```  
  
### <a name="parameters"></a>Parametry  
 *clrBackColor*  
 Na nowy kolor tła formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_backstyle"></a>  CStockPropImpl::put_BackStyle  
 Wywołaj tę metodę, aby ustawić styl tła formantu.  
  
```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *nBackStyle*  
 Nowy styl tła formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_bordercolor"></a>  CStockPropImpl::put_BorderColor  
 Wywołaj tę metodę w celu ustawienia koloru obramowania formantu.  
  
```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```  
  
### <a name="parameters"></a>Parametry  
 *clrBorderColor*  
 Na nowy kolor obramowania. Typ danych OLE_COLOR wewnętrznie jest reprezentowany jako długich 32-bitowych liczb całkowitych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_borderstyle"></a>  CStockPropImpl::put_BorderStyle  
 Wywołaj tę metodę, aby ustawić styl obramowania formantu.  
  
```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *nBorderStyle*  
 Nowy styl obramowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_bordervisible"></a>  CStockPropImpl::put_BorderVisible  
 Wywołanie tej metody można ustawić wartości flagę wskazującą, czy obramowania formantu jest widoczne.  
  
```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```  
  
### <a name="parameters"></a>Parametry  
 *bBorderVisible*  
 Wartość TRUE, jeśli ma być widoczne obramowanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_borderwidth"></a>  CStockPropImpl::put_BorderWidth  
 Wywołaj tę metodę, aby ustawić szerokość obramowania formantu.  
  
```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```  
  
### <a name="parameters"></a>Parametry  
 `nBorderWidth`  
 Nową szerokość obramowania formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_caption"></a>  CStockPropImpl::put_Caption  
 Wywołaj tę metodę, aby ustawić tekst, który ma być wyświetlane z formantem.  
  
```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```  
  
### <a name="parameters"></a>Parametry  
 *bstrCaption*  
 Tekst, który ma być wyświetlane z formantem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_drawmode"></a>  CStockPropImpl::put_DrawMode  
 Wywołaj tę metodę, aby ustawić tryb rysowania formantu, na przykład XOR pióro lub Odwróć kolory.  
  
```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```  
  
### <a name="parameters"></a>Parametry  
 `nDrawMode`  
 Tryb rysowania nowego formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_drawstyle"></a>  CStockPropImpl::put_DrawStyle  
 Na przykład wywołać tę metodę, aby ustawić styl rysowania formantu, stały, przerywana lub kropkami.  
  
```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *nDrawStyle*  
 Styl rysowania nowego formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_drawwidth"></a>  CStockPropImpl::put_DrawWidth  
 Wywołanie tej metody można ustawić szerokość (w pikselach) metody rysowania formantu.  
  
```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *nDrawWidth*  
 Nową szerokość używanego przez formant rysowania metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_enabled"></a>  CStockPropImpl::put_Enabled  
 Wywołanie tej metody można ustawić wartości flagę wskazującą, czy formant jest włączony.  
  
```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnabled`  
 Wartość TRUE, jeśli formant jest włączony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_fillcolor"></a>  CStockPropImpl::put_FillColor  
 Wywołaj tę metodę, aby ustawić kolor wypełnienia formantu.  
  
```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```  
  
### <a name="parameters"></a>Parametry  
 *clrFillColor*  
 Kolor wypełnienia nowego formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_fillstyle"></a>  CStockPropImpl::put_FillStyle  
 Na przykład wywołać tę metodę, aby ustawić styl wypełnienia kontrolki, stały, przezroczysty lub zakreskowany.  
  
```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *nFillStyle*  
 Styl wypełnienia nowego formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_font"></a>  CStockPropImpl::put_Font  
 Wywołanie tej metody można ustawić właściwości czcionki formantu.  
  
```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>Parametry  
 `pFont`  
 Wskaźnik do właściwości czcionki formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_forecolor"></a>  CStockPropImpl::put_ForeColor  
 Wywołaj tę metodę, aby ustawić kolor pierwszego planu formantu.  
  
```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```  
  
### <a name="parameters"></a>Parametry  
 *clrForeColor*  
 Na nowy kolor pierwszego planu formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_hwnd"></a>  CStockPropImpl::put_HWND  
 Ta metoda zwraca E_FAIL.  
  
```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```  
  
### <a name="parameters"></a>Parametry  
 */\* Właściwość hWnd \*/*  
 Zastrzeżone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca E_FAIL.  
  
### <a name="remarks"></a>Uwagi  
 Uchwyt okna jest wartością tylko do odczytu.  
  
##  <a name="put_mouseicon"></a>  CStockPropImpl::put_MouseIcon  
 Wywołanie tej metody można ustawić właściwości obrazu graficznego (ikony, mapa bitowa lub metaplik) do wyświetlenia, gdy wskaźnik myszy znajduje się nad formantem.  
  
```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>Parametry  
 `pPicture`  
 Wskaźnik do właściwości obrazu grafiki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_mousepointer"></a>  CStockPropImpl::put_MousePointer  
 Wywołanie tej metody, aby ustawić typ wskaźnika myszy wyświetlane, gdy wskaźnik myszy znajduje się nad formantem, na przykład, strzałki, między lub Klepsydra.  
  
```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```  
  
### <a name="parameters"></a>Parametry  
 *nMousePointer*  
 Typ wskaźnika myszy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_picture"></a>  CStockPropImpl::put_Picture  
 Wywołanie tej metody można ustawić właściwości obrazu grafiki (ikony, mapy bitowej lub metaplik), które mają być wyświetlane.  
  
```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>Parametry  
 `pPicture`  
 Wskaźnik do właściwości obrazu. Zobacz [IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762) więcej szczegółów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_readystate"></a>  CStockPropImpl::put_ReadyState  
 Wywołanie tej metody można ustawić stanu gotowości formantu, na przykład, ładowania lub załadować.  
  
```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```  
  
### <a name="parameters"></a>Parametry  
 *nReadyState*  
 Stan gotowości formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_tabstop"></a>  CStockPropImpl::put_TabStop  
 Wywołaj tę metodę, aby ustawić flagę wskazującą, czy formant jest tabulatora.  
  
```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```  
  
### <a name="parameters"></a>Parametry  
 *bTabStop*  
 Wartość TRUE, jeśli formant jest tabulatora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_text"></a>  CStockPropImpl::put_Text  
 Wywołaj tę metodę, aby ustawić tekst, który jest wyświetlany za pomocą formantu.  
  
```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrText`  
 Tekst, który jest wyświetlany za pomocą formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_valid"></a>  CStockPropImpl::putvalid  
 Wywołaj tę metodę, aby ustawić flagę wskazującą, czy formant jest prawidłowy.  
  
```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```  
  
### <a name="parameters"></a>Parametry  
 *bValid*  
 Wartość TRUE, jeśli formant jest nieprawidłowy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="put_window"></a>  CStockPropImpl::put_Window  
 Ta metoda wywołuje [CStockPropImpl::put_HWND](#put_hwnd), która zwraca E_FAIL.  
  
```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 Uchwyt okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca E_FAIL.  
  
### <a name="remarks"></a>Uwagi  
 Uchwyt okna jest wartością tylko do odczytu.  
  
##  <a name="putref_font"></a>  CStockPropImpl::putref_Font  
 Wywołanie tej metody można ustawić właściwości czcionki formantu, wraz z liczbą odwołania.  
  
```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>Parametry  
 `pFont`  
 Wskaźnik do właściwości czcionki formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Taki sam jak [CStockPropImpl::put_Font](#put_font), ale o liczbie odwołań.  
  
##  <a name="putref_mouseicon"></a>  CStockPropImpl::putref_MouseIcon  
 Wywołanie tej metody można ustawić właściwości obrazu graficznego (ikony, mapa bitowa lub metaplik) do wyświetlenia, gdy wskaźnik myszy znajduje się nad formantem, wraz z liczbą odwołania.  
  
```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>Parametry  
 `pPicture`  
 Wskaźnik do właściwości obrazu grafiki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Taki sam jak [CStockPropImpl::put_MouseIcon](#put_mouseicon), ale o liczbie odwołań.  
  
##  <a name="putref_picture"></a>  CStockPropImpl::putref_Picture  
 Wywołanie tej metody można ustawić właściwości obrazu grafiki (ikony, mapy bitowej lub metaplik), które mają być wyświetlane, wraz z liczbą odwołania.  
  
```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>Parametry  
 `pPicture`  
 Wskaźnik do właściwości obrazu. Zobacz [IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762) więcej szczegółów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Taki sam jak [CStockPropImpl::put_Picture](#put_picture), ale o liczbie odwołań.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa IDispatchImpl](../../atl/reference/idispatchimpl-class.md)
