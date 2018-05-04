---
title: Klasa IAtlMemMgr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35cc685c06eaa3992ec8444cfc5d99f2191145a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
|[Przydziel](#allocate)|Wywołanie tej metody można przydzielić bloku pamięci.|  
|[W warstwie bezpłatna](#free)|Wywołanie tej metody, aby zwolnić bloku pamięci.|  
|[GetSize](#getsize)|Wywołaj tę metodę, aby pobrać rozmiar bloku alokacji pamięci.|  
|[Ponowne przydzielenie](#reallocate)|Wywołaj tę metodę, aby ponownie przydzielić bloku pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest implementowany przez [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md), lub [CWin32Heap](../../atl/reference/cwin32heap-class.md).  
  
> [!NOTE]
>  Funkcje sterty lokalne i globalne wolniej niż inne funkcje zarządzania pamięcią, a nie udostępniają tylu funkcji. W związku z tym nowe aplikacje powinny używać [stercie funkcji](http://msdn.microsoft.com/library/windows/desktop/aa366711). Są one dostępne w [CWin32Heap](../../atl/reference/cwin32heap-class.md) klasy.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlmem.h  
  
##  <a name="allocate"></a>  IAtlMemMgr::Allocate  
 Wywołanie tej metody można przydzielić bloku pamięci.  
  
```
void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Żądana liczba bajtów w nowego bloku pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do rozpoczęcia bloku nowo alokacji pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie [IAtlMemMgr::Free](#free) lub [IAtlMemMgr::Reallocate](#reallocate) zwolnienia pamięci przydzielonej przez tę metodę.  
  
### <a name="example"></a>Przykład  
 Na przykład zobacz [omówienie IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
##  <a name="free"></a>  IAtlMemMgr::Free  
 Wywołanie tej metody, aby zwolnić bloku pamięci.  
  
```
void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do pamięci przydzielonej wcześniej przez tego menedżera pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia zwolnić pamięć uzyskany przez [IAtlMemMgr::Allocate](#allocate) lub [IAtlMemMgr::Reallocate](#reallocate).  
  
### <a name="example"></a>Przykład  
 Na przykład zobacz [omówienie IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
##  <a name="getsize"></a>  IAtlMemMgr::GetSize  
 Wywołaj tę metodę, aby pobrać rozmiar bloku alokacji pamięci.  
  
```
size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do pamięci przydzielonej wcześniej przez tego menedżera pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca rozmiar bloku pamięci w bajtach.  
  
### <a name="example"></a>Przykład  
 Na przykład zobacz [omówienie IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
##  <a name="reallocate"></a>  IAtlMemMgr::Reallocate  
 Wywołaj tę metodę, aby ponownie przydzielić pamięci przydzielonej przez ten Menedżer pamięci.  
  
```
void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do pamięci przydzielonej wcześniej przez tego menedżera pamięci.  
  
 `nBytes`  
 Żądana liczba bajtów w nowego bloku pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do rozpoczęcia bloku nowo alokacji pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie [IAtlMemMgr::Free](#free) lub [IAtlMemMgr::Reallocate](#reallocate) zwolnienia pamięci przydzielonej przez tę metodę.  
  
 Koncepcyjnie ta metoda zwalnia pamięć istniejących i przydziela nowego bloku pamięci. W rzeczywistości istniejącej pamięci może być rozszerzony lub w przeciwnym razie ponownie.  
  
### <a name="example"></a>Przykład  
 Na przykład zobacz [omówienie IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
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
  
##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch  
 Ta metoda jest wywoływana, aby uzupełnić domyślnego interfejsu — właściwość otoczenia z interfejsem użytkownika.  
  
```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 *pDispatch*  
 Wskaźnik do nowego interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `SetAmbientDispatch` jest wywoływana za pomocą wskaźnika do nowego interfejsu nowy interfejs będzie służyć do wywołania żadnych właściwości ani metod wyświetlony monit o podanie przez formant hostowanej — Jeśli te właściwości nie są już dostarczane przez [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).  
  
##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl  
 Dołącza kontrolkę istniejących (i wcześniej zainicjowana) do obiektu hosta, za pomocą okna identyfikowane przez `hWnd`.  
  
```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkControl*  
 [in] Wskaźnik do **IUnknown** interfejsu formantu jest dołączony do obiektu hosta.  
  
 `hWnd`  
 [in] Dojście do okna używanego do hostowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl  
 Tworzy kontrolkę, inicjowane i znajduje się w oknie identyfikowane przez `hWnd`.  
  
```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```  
  
### <a name="parameters"></a>Parametry  
 `lpTricsData`  
 [in] Ciąg identyfikujący formantu do utworzenia. Może to być identyfikator CLSID (należy uwzględnić nawiasy), identyfikator ProgID, adres URL lub kod HTML (poprzedzony **MSHTML:**).  
  
 `hWnd`  
 [in] Dojście do okna używanego do hostowania.  
  
 `pStream`  
 [in] Wskaźnik interfejsu dla strumienia zawierające dane inicjowania dla formantu. Może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 To okno zostanie podklasy przez obiekt hosta Udostępnianie ten interfejs, dzięki czemu komunikaty mogą pojawiają się do formantu i inne funkcje kontenera będą działać.  
  
 Wywołanie tej metody jest odpowiednikiem wywołania [IAxWinHostWindow::CreateControlEx](#createcontrolex).  
  
 Aby utworzyć licencjonowanego formantu ActiveX, zobacz [IAxWinHostWindowLic::CreateControlLic](#createcontrollicex).  
  
##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx  
 Tworzy formantu ActiveX, inicjowane i znajduje się w określonym okna, podobnie jak [IAxWinHostWindow::CreateControl](#createcontrol).  
  
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
 `lpTricsData`  
 [in] Ciąg identyfikujący formantu do utworzenia. Może to być identyfikator CLSID (należy uwzględnić nawiasy), identyfikator ProgID, adres URL lub kod HTML (prefiksem **MSHTML:**).  
  
 `hWnd`  
 [in] Dojście do okna używanego do hostowania.  
  
 `pStream`  
 [in] Wskaźnik interfejsu dla strumienia zawierające dane inicjowania dla formantu. Może być **NULL**.  
  
 `ppUnk`  
 [out] Adres wskaźnika, który będzie otrzymywał **IUnknown** interfejsu utworzony formantu. Może być **NULL**.  
  
 *riidAdvise*  
 [in] Identyfikator interfejsu interfejs wychodzących w zawartego w nim obiektu. Może być **ma wartości IID_NULL**.  
  
 *punkAdvise*  
 [in] Wskaźnik do **IUnknown** interfejsu połączenia z punktem połączenia zawartych w niej obiektu określonego przez obiekt sink `iidSink`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 W odróżnieniu od `CreateControl` metody `CreateControlEx` umożliwia również otrzymywać wskaźnik interfejsu do sterowania nowo utworzony i skonfigurowany obiekt sink zdarzenia do odbierania zdarzenia wywoływane przez formant.  
  
 Aby utworzyć licencjonowanego formantu ActiveX, zobacz [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex).  
  
##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl  
 Zwraca wskaźnik określonego interfejsu podał obsługiwanego formantu.  
  
```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `riid`  
 [in] Identyfikator formantu żądanego interfejsu.  
  
 `ppvObject`  
 [out] Adres wskaźnika odbioru określonego interfejsu utworzony formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch  
 Ustawia dispinterface zewnętrznego, który jest dostępny do zawartych w niej formantów za pomocą [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) metody.  
  
```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisp`  
 [in] Wskaźnik do `IDispatch` interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler  
 Wywołanie tej funkcji, aby ustawić zewnętrznej [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) interfejs na potrzeby `CAxWindow` obiektu.  
  
```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisp`  
 [in] Wskaźnik do **IDocHostUIHandlerDispatch** interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest używana przez formanty (na przykład formant przeglądarki sieci Web), które zapytania witryny hosta dla `IDocHostUIHandlerDispatch` interfejsu.  
  
##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic  
 Tworzy kontrolkę licencjonowane inicjowane i znajduje się w oknie identyfikowane przez `hWnd`.  
  
```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrLic`  
 [in] BSTR, który zawiera klucz licencji dla formantu.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IAxWinHostWindow::CreateControl](#createcontrol) opis pozostałych parametrów i zwracanych wartości.  
  
 Wywołanie tej metody jest odpowiednikiem wywołania [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>Przykład  
 Zobacz [Hosting AXHost za pomocą biblioteki ATL programu ActiveX formanty](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego z `IAxWinHostWindowLic::CreateControlLic`.  
  
##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx  
 Tworzy licencjonowanego formantu ActiveX, inicjowane i znajduje się w określonym okna, podobnie jak [IAxWinHostWindow::CreateControl](#createcontrol).  
  
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
 `bstrLic`  
 [in] BSTR, który zawiera klucz licencji dla formantu.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IAxWinHostWindow::CreateControlEx](#createcontrolex) opis pozostałych parametrów i zwracanych wartości.  
  
### <a name="example"></a>Przykład  
 Zobacz [Hosting AXHost za pomocą biblioteki ATL programu ActiveX formanty](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego z `IAxWinHostWindowLic::CreateControlLicEx`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
