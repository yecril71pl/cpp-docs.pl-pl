---
title: Interfejs IAxWinAmbientDispatch | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d082faf4c25f76fd7a98cc897760adc424ffb49e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366331"
---
# <a name="iaxwinambientdispatch-interface"></a>Interfejs IAxWinAmbientDispatch
Ten interfejs udostępnia metody do określania właściwości formantu hostowanej lub kontenera.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
interface IAxWinAmbientDispatch : IDispatch
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[get_AllowContextMenu](#get_allowcontextmenu)|**AllowContextMenu** właściwość określa, czy obsługiwanego formantu może wyświetlić menu kontekstowe.|  
|[get_AllowShowUI](#get_allowshowui)|**AllowShowUI** właściwość określa, czy formant hostowanej może wyświetlić interfejs użytkownika.|  
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|**AllowWindowlessActivation** właściwość określa, czy kontener będzie zezwolenia na aktywację bez okien.|  
|[get_BackColor](#get_backcolor)|`BackColor` Właściwość określa kolor tła otoczenia kontenera.|  
|[get_DisplayAsDefault](#get_displayasdefault)|**Displayasdefault środowiska** jest właściwością otoczenia umożliwiający sterowania sprawdzić, czy jest domyślnym.|  
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|**DocHostDoubleClickFlags** właściwość określa działanie powinno odbywać się w odpowiedzi na dwukrotne.|  
|[get_DocHostFlags](#get_dochostflags)|**DocHostFlags** właściwość określa możliwości interfejsu użytkownika obiektu hosta.|  
|[get_Font](#get_font)|**Czcionki** właściwość określa czcionkę otoczenia kontenera.|  
|[get_ForeColor](#get_forecolor)|`ForeColor` Właściwość określa kolor otoczenia kontenera.|  
|[get_LocaleID](#get_localeid)|**LocaleID** właściwość określa identyfikator ustawień regionalnych otoczenia kontenera.|  
|[get_MessageReflect](#get_messagereflect)|**MessageReflect** otoczenia właściwość określa, czy kontener będzie odzwierciedlać wiadomości do obsługiwanego formantu.|  
|[get_OptionKeyPath](#get_optionkeypath)|**OptionKeyPath** właściwość określa ścieżkę klucza rejestru w celu ustawienia użytkownika.|  
|[get_ShowGrabHandles](#get_showgrabhandles)|**ShowGrabHandles** zmieniono właściwość zapewnia kontrolę dowiedzieć się, jeśli jego powinien być rysowany sam z uchwytów.|  
|[get_ShowHatching](#get_showhatching)|**ShowHatching** sterowania dowiedzieć się, jeśli jego powinien być rysowany sam wyklutych umożliwia — właściwość otoczenia.|  
|[get_UserMode](#get_usermode)|**Przekierowanie** właściwość określa tryb użytkownika otoczenia kontenera.|  
|[put_AllowContextMenu](#put_allowcontextmenu)|**AllowContextMenu** właściwość określa, czy obsługiwanego formantu może wyświetlić menu kontekstowe.|  
|[put_AllowShowUI](#put_allowshowui)|**AllowShowUI** właściwość określa, czy formant hostowanej może wyświetlić interfejs użytkownika.|  
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|**AllowWindowlessActivation** właściwość określa, czy kontener będzie zezwolenia na aktywację bez okien.|  
|[put_BackColor](#put_backcolor)|`BackColor` Właściwość określa kolor tła otoczenia kontenera.|  
|[put_DisplayAsDefault](#put_displayasdefault)|**Displayasdefault środowiska** jest właściwością otoczenia umożliwiający sterowania sprawdzić, czy jest domyślnym.|  
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|**DocHostDoubleClickFlags** właściwość określa działanie powinno odbywać się w odpowiedzi na dwukrotne.|  
|[put_DocHostFlags](#put_dochostflags)|**DocHostFlags** właściwość określa możliwości interfejsu użytkownika obiektu hosta.|  
|[put_Font](#put_font)|**Czcionki** właściwość określa czcionkę otoczenia kontenera.|  
|[put_ForeColor](#put_forecolor)|`ForeColor` Właściwość określa kolor otoczenia kontenera.|  
|[put_LocaleID](#put_localeid)|**LocaleID** właściwość określa identyfikator ustawień regionalnych otoczenia kontenera.|  
|[put_MessageReflect](#put_messagereflect)|**MessageReflect** otoczenia właściwość określa, czy kontener będzie odzwierciedlać wiadomości do obsługiwanego formantu.|  
|[put_OptionKeyPath](#put_optionkeypath)|**OptionKeyPath** właściwość określa ścieżkę klucza rejestru w celu ustawienia użytkownika.|  
|[put_UserMode](#put_usermode)|**Przekierowanie** właściwość określa tryb użytkownika otoczenia kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest udostępniany przez formant ActiveX w ATL hosting obiektów. Wywołanie metody w tym interfejsie można ustawić właściwości otaczających dostępne do formantu hostowanej lub, aby określić inne aspekty zachowania kontenera. Uzupełnienie właściwości udostępniane przez `IAxWinAmbientDispatch`, użyj [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).  
  
 [AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) próbuje załadować informacji o typie o `IAxWinAmbientDispatch` i `IAxWinAmbientDispatchEx` z biblioteki typów, który zawiera kod.  
  
 Jeśli łączysz się ATL90.dll, **AXHost** załaduje informacji o typie z biblioteki typów w bibliotece DLL.  
  
 Zobacz [Hosting AXHost za pomocą biblioteki ATL programu ActiveX formanty](../../atl/hosting-activex-controls-using-atl-axhost.md) więcej szczegółów.  
  
## <a name="requirements"></a>Wymagania  
 Definicja tego interfejsu jest dostępne w wielu formularzach, jak pokazano w poniższej tabeli.  
  
|Typ definicji|Plik|  
|---------------------|----------|  
|IDL|atliface.IDL|  
|Biblioteki typów|ATL.dll|  
|C++|atliface.h (również zawarte w ATLBase.h)|  
  
##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu  
 **AllowContextMenu** właściwość określa, czy obsługiwanego formantu może wyświetlić menu kontekstowe.  
  
```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```  
  
### <a name="parameters"></a>Parametry  
 *pbAllowContextMenu*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa `VARIANT_TRUE` jako wartość domyślna tej właściwości.  
  
##  <a name="get_allowshowui"></a>  IAxWinAmbientDispatch::get_AllowShowUI  
 **AllowShowUI** właściwość określa, czy formant hostowanej może wyświetlić interfejs użytkownika.  
  
```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```  
  
### <a name="parameters"></a>Parametry  
 *pbAllowShowUI*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa **wartość VARIANT_FALSE** jako wartość domyślna tej właściwości.  
  
##  <a name="get_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::get_AllowWindowlessActivation  
 **AllowWindowlessActivation** właściwość określa, czy kontener będzie zezwolenia na aktywację bez okien.  
  
```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```  
  
### <a name="parameters"></a>Parametry  
 *pbAllowWindowless*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa `VARIANT_TRUE` jako wartość domyślna tej właściwości.  
  
##  <a name="get_backcolor"></a>  IAxWinAmbientDispatch::get_BackColor  
 `BackColor` Właściwość określa kolor tła otoczenia kontenera.  
  
```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```  
  
### <a name="parameters"></a>Parametry  
 *pclrBackground*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa **COLOR_BTNFACE** lub **COLOR_WINDOW** jako wartość domyślna tej właściwości (w zależności od tego, czy element nadrzędny okno hosta jest okno dialogowe, lub nie).  
  
##  <a name="get_displayasdefault"></a>  IAxWinAmbientDispatch::get_DisplayAsDefault  
 **Displayasdefault środowiska** jest właściwością otoczenia umożliwiający sterowania sprawdzić, czy jest domyślnym.  
  
```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```  
  
### <a name="parameters"></a>Parametry  
 *pbDisplayAsDefault*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa **wartość VARIANT_FALSE** jako wartość domyślna tej właściwości.  
  
##  <a name="get_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::get_DocHostDoubleClickFlags  
 **DocHostDoubleClickFlags** właściwość określa działanie powinno odbywać się w odpowiedzi na dwukrotne.  
  
```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *pdwDocHostDoubleClickFlags*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa **DOCHOSTUIDBLCLK_DEFAULT** jako wartość domyślna tej właściwości.  
  
##  <a name="get_dochostflags"></a>  IAxWinAmbientDispatch::get_DocHostFlags  
 **DocHostFlags** właściwość określa możliwości interfejsu użytkownika obiektu hosta.  
  
```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *pdwDocHostFlags*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa **DOCHOSTUIFLAG_NO3DBORDER** jako wartość domyślna tej właściwości.  
  
##  <a name="get_font"></a>  IAxWinAmbientDispatch::get_Font  
 **Czcionki** właściwość określa czcionkę otoczenia kontenera.  
  
```
STDMETHOD(get_Font)(IFontDisp** pFont);
```  
  
### <a name="parameters"></a>Parametry  
 `pFont`  
 [out] Adres **IFontDisp** wskaźnika interfejsu używany do odbierania bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa domyślnej czcionki graficznego interfejsu użytkownika lub systemu jako wartość domyślna tej właściwości.  
  
##  <a name="get_forecolor"></a>  IAxWinAmbientDispatch::get_ForeColor  
 `ForeColor` Właściwość określa kolor otoczenia kontenera.  
  
```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```  
  
### <a name="parameters"></a>Parametry  
 *pclrForeground*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa kolor tekstu okna systemu jako wartość domyślna tej właściwości.  
  
##  <a name="get_localeid"></a>  IAxWinAmbientDispatch::get_LocaleID  
 **LocaleID** właściwość określa identyfikator ustawień regionalnych otoczenia kontenera.  
  
```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```  
  
### <a name="parameters"></a>Parametry  
 *plcidLocaleID*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa użytkownika domyślne ustawienia regionalne jako wartość domyślna tej właściwości.  
  
 Ta metoda może odnajdywać otoczenia identyfikator lokalny, oznacza to, że identyfikator ustawień regionalnych programu formantu jest używana w. Jeśli znasz identyfikator ustawień regionalnych kod, aby załadować podpisów specyficzne dla ustawień regionalnych, tekst komunikatu o błędzie, można wywołać itd z pliku zasobów lub satelitarnej biblioteki DLL.  
  
##  <a name="get_messagereflect"></a>  IAxWinAmbientDispatch::get_MessageReflect  
 **MessageReflect** otoczenia właściwość określa, czy kontener będzie odzwierciedlać wiadomości do obsługiwanego formantu.  
  
```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```  
  
### <a name="parameters"></a>Parametry  
 *pbMessageReflect*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa `VARIANT_TRUE` jako wartość domyślna tej właściwości.  
  
##  <a name="get_optionkeypath"></a>  IAxWinAmbientDispatch::get_OptionKeyPath  
 **OptionKeyPath** właściwość określa ścieżkę klucza rejestru w celu ustawienia użytkownika.  
  
```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```  
  
### <a name="parameters"></a>Parametry  
 *pbstrOptionKeyPath*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles  
 **ShowGrabHandles** zmieniono właściwość zapewnia kontrolę dowiedzieć się, jeśli jego powinien być rysowany sam z uchwytów.  
  
```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```  
  
### <a name="parameters"></a>Parametry  
 *pbShowGrabHandles*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL zawsze zwraca **wartość VARIANT_FALSE** jako wartość tej właściwości.  
  
##  <a name="get_showhatching"></a>  IAxWinAmbientDispatch::get_ShowHatching  
 **ShowHatching** sterowania dowiedzieć się, jeśli jego powinien być rysowany sam wyklutych umożliwia — właściwość otoczenia.  
  
```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```  
  
### <a name="parameters"></a>Parametry  
 *pbShowHatching*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL zawsze zwraca **wartość VARIANT_FALSE** jako wartość tej właściwości.  
  
##  <a name="get_usermode"></a>  IAxWinAmbientDispatch::get_UserMode  
 **Przekierowanie** właściwość określa tryb użytkownika otoczenia kontenera.  
  
```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```  
  
### <a name="parameters"></a>Parametry  
 *pbUserMode*  
 [out] Adres zmiennej bieżąca wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa `VARIANT_TRUE` jako wartość domyślna tej właściwości.  
  
##  <a name="put_allowcontextmenu"></a>  IAxWinAmbientDispatch::put_AllowContextMenu  
 **AllowContextMenu** właściwość określa, czy obsługiwanego formantu może wyświetlić menu kontekstowe.  
  
```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```  
  
### <a name="parameters"></a>Parametry  
 *bAllowContextMenu*  
 [in] Nowa wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa `VARIANT_TRUE` jako wartość domyślna tej właściwości.  
  
##  <a name="put_allowshowui"></a>  IAxWinAmbientDispatch::put_AllowShowUI  
 **AllowShowUI** właściwość określa, czy formant hostowanej może wyświetlić interfejs użytkownika.  
  
```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```  
  
### <a name="parameters"></a>Parametry  
 *bAllowShowUI*  
 [in] Nowa wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa **wartość VARIANT_FALSE** jako wartość domyślna tej właściwości.  
  
##  <a name="put_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::put_AllowWindowlessActivation  
 **AllowWindowlessActivation** właściwość określa, czy kontener będzie zezwolenia na aktywację bez okien.  
  
```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```  
  
### <a name="parameters"></a>Parametry  
 *bAllowWindowless*  
 [in] Nowa wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa `VARIANT_TRUE` jako wartość domyślna tej właściwości.  
  
##  <a name="put_backcolor"></a>  IAxWinAmbientDispatch::put_BackColor  
 `BackColor` Właściwość określa kolor tła otoczenia kontenera.  
  
```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```  
  
### <a name="parameters"></a>Parametry  
 *clrBackground*  
 [in] Nowa wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa **COLOR_BTNFACE** lub **COLOR_WINDOW** jako wartość domyślna tej właściwości (w zależności od tego, czy element nadrzędny okno hosta jest okno dialogowe, lub nie).  
  
##  <a name="put_displayasdefault"></a>  IAxWinAmbientDispatch::put_DisplayAsDefault  
 **Displayasdefault środowiska** jest właściwością otoczenia umożliwiający sterowania sprawdzić, czy jest domyślnym.  
  
```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```  
  
### <a name="parameters"></a>Parametry  
 `bDisplayAsDefault`  
 [in] Nowa wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa **wartość VARIANT_FALSE** jako wartość domyślna tej właściwości.  
  
##  <a name="put_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::put_DocHostDoubleClickFlags  
 **DocHostDoubleClickFlags** właściwość określa działanie powinno odbywać się w odpowiedzi na dwukrotne.  
  
```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDocHostDoubleClickFlags*  
 [in] Nowa wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa **DOCHOSTUIDBLCLK_DEFAULT** jako wartość domyślna tej właściwości.  
  
##  <a name="put_dochostflags"></a>  IAxWinAmbientDispatch::put_DocHostFlags  
 **DocHostFlags** właściwość określa możliwości interfejsu użytkownika obiektu hosta.  
  
```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDocHostFlags*  
 [in] Nowa wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa **DOCHOSTUIFLAG_NO3DBORDER** jako wartość domyślna tej właściwości.  
  
##  <a name="put_font"></a>  IAxWinAmbientDispatch::put_Font  
 **Czcionki** właściwość określa czcionkę otoczenia kontenera.  
  
```
STDMETHOD(put_Font)(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>Parametry  
 `pFont`  
 [in] Nowa wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa domyślnej czcionki graficznego interfejsu użytkownika lub systemu jako wartość domyślna tej właściwości.  
  
##  <a name="put_forecolor"></a>  IAxWinAmbientDispatch::put_ForeColor  
 `ForeColor` Właściwość określa kolor otoczenia kontenera.  
  
```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```  
  
### <a name="parameters"></a>Parametry  
 *clrForeground*  
 [in] Nowa wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa kolor tekstu okna systemu jako wartość domyślna tej właściwości.  
  
##  <a name="put_localeid"></a>  IAxWinAmbientDispatch::put_LocaleID  
 **LocaleID** właściwość określa identyfikator ustawień regionalnych otoczenia kontenera.  
  
```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```  
  
### <a name="parameters"></a>Parametry  
 *lcidLocaleID*  
 [in] Nowa wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa użytkownika domyślne ustawienia regionalne jako wartość domyślna tej właściwości.  
  
##  <a name="put_messagereflect"></a>  IAxWinAmbientDispatch::put_MessageReflect  
 **MessageReflect** otoczenia właściwość określa, czy kontener będzie odzwierciedlać wiadomości do obsługiwanego formantu.  
  
```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```  
  
### <a name="parameters"></a>Parametry  
 `bMessageReflect`  
 [in] Nowa wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa `VARIANT_TRUE` jako wartość domyślna tej właściwości.  
  
##  <a name="put_optionkeypath"></a>  IAxWinAmbientDispatch::put_OptionKeyPath  
 **OptionKeyPath** właściwość określa ścieżkę klucza rejestru w celu ustawienia użytkownika.  
  
```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```  
  
### <a name="parameters"></a>Parametry  
 *bstrOptionKeyPath*  
 [in] Nowa wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode  
 **Przekierowanie** właściwość określa tryb użytkownika otoczenia kontenera.  
  
```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```  
  
### <a name="parameters"></a>Parametry  
 `bUserMode`  
 [in] Nowa wartość tej właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Implementacja obiektu hosta ATL używa `VARIANT_TRUE` jako wartość domyślna tej właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)   
 [Interfejs IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)   
 [CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)









