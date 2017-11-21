---
title: Klasa CAtlPreviewCtrlImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Create
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Destroy
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Focus
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::OnPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Redraw
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetHost
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetPreviewVisuals
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetRect
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::DoPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_plf
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrBack
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrText
dev_langs: C++
helpviewer_keywords: CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 281bc00e46cf28f7cc7d5f1e072fd41ad4cce61a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="catlpreviewctrlimpl-class"></a>Klasa CAtlPreviewCtrlImpl
Ta klasa jest implementacją ATL okna, który znajduje się w oknie hostów udostępnianych przez powłokę dla podglądu rozbudowanego.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl](#dtor)|Destructs obiektu podglądu formantu.|  
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Tworzy obiekt kontroli wersji zapoznawczej.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::Create](#create)|Metoda wywoływana przez program obsługi podglądu rozbudowanego można utworzyć okna systemu Windows.|  
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|Wywoływane przez program obsługi podglądu rozbudowanego, kiedy zachodzi potrzeba zniszczyć tego formantu.|  
|[CAtlPreviewCtrlImpl::Focus](#focus)|Zestawy danych wejściowych fokus do tego formantu.|  
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|Obsługuje komunikat WM_PAINT.|  
|[CAtlPreviewCtrlImpl::Redraw](#redraw)|Określa, że tego formantu, aby odświeżyć.|  
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Ustawia nowy element nadrzędny tego formantu.|  
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Metoda wywoływana przez program obsługi podglądu rozbudowanego kiedy zachodzi potrzeba Ustaw obraz podglądu zawartości.|  
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|Ustawia nowy prostokąt ograniczający dla tego formantu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|Wywoływane przez platformę, by renderować w wersji zapoznawczej.|  
  
### <a name="protected-constants"></a>Stałe chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|Czcionka używana do wyświetlania tekstu w okienku podglądu.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|Kolor tła okna podglądu.|  
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|Kolor tekstu okna podglądu.|  

  
## <a name="remarks"></a>Uwagi  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `TBase`  
  
 `ATL::CMessageMap`  
  
 `ATL::CWindowImplRoot<TBase>`  
  
 `ATL::CWindowImplBaseT<TBase,TWinTraits>`  
  
 [ATL::CWindowImpl\<CAtlPreviewCtrlImpl >](../../atl/reference/cwindowimpl-class.md)  
  
 `IPreviewCtrl`  
  
 `ATL::CAtlPreviewCtrlImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlpreviewctrlimpl.h  
  
##  <a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl  
 Tworzy obiekt kontroli wersji zapoznawczej.  
  
```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="dtor"></a>CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl  
 Destructs obiektu podglądu formantu.  
  
```
virtual ~CAtlPreviewCtrlImpl(void);
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="create"></a>CAtlPreviewCtrlImpl::Create  
 Metoda wywoływana przez program obsługi podglądu rozbudowanego można utworzyć okna systemu Windows.  
  
```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 Dojście do okna hosta dostarczone przez powłokę dla podglądu rozbudowanego.  
  
 `prc`  
 Określa początkowy rozmiar i położenie okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`w przypadku powodzenia; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="destroy"></a>CAtlPreviewCtrlImpl::Destroy  
 Wywoływane przez program obsługi podglądu rozbudowanego, kiedy zachodzi potrzeba zniszczyć tego formantu.  
  
```
virtual void Destroy();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="dopaint"></a>CAtlPreviewCtrlImpl::DoPaint  
 Wywoływane przez platformę, by renderować w wersji zapoznawczej.  
  
```
virtual void DoPaint(HDC hdc);
```  
  
### <a name="parameters"></a>Parametry  
 `hdc`  
 Dojście do kontekstu urządzenia dla malowania.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="focus"></a>CAtlPreviewCtrlImpl::Focus  
 Zestawy danych wejściowych fokus do tego formantu.  
  
```
virtual void Focus();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_clrback"></a>CAtlPreviewCtrlImpl::m_clrBack  
 Kolor tła okna podglądu.  
  
```
COLORREF m_clrBack;
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_clrtext"></a>CAtlPreviewCtrlImpl::m_clrText  
 Kolor tekstu okna podglądu.  
  
```
COLORREF m_clrText;
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_plf"></a>CAtlPreviewCtrlImpl::m_plf  
 Czcionka używana do wyświetlania tekstu w okienku podglądu.  
  
```
const LOGFONTW* m_plf;
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onpaint"></a>CAtlPreviewCtrlImpl::OnPaint  
 Obsługuje komunikat WM_PAINT.  
  
```
LRESULT OnPaint(  
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Parametry  
 `nMsg`  
 Ustaw WM_PAINT.  
  
 `wParam`  
 Ten parametr nie jest używany.  
  
 `lParam`  
 Ten parametr nie jest używany.  
  
 `bHandled`  
 Po powrocie z tej funkcji zawiera `TRUE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość 0.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="redraw"></a>CAtlPreviewCtrlImpl::Redraw  
 Określa, że tego formantu, aby odświeżyć.  
  
```
virtual void Redraw();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost  
 Ustawia nowy element nadrzędny tego formantu.  
  
```
virtual void SetHost(HWND hWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 Dojście do nowego okna nadrzędnego.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals  
 Metoda wywoływana przez program obsługi podglądu rozbudowanego kiedy zachodzi potrzeba Ustaw obraz podglądu zawartości.  
  
```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```  
  
### <a name="parameters"></a>Parametry  
 `clrBack`  
 Kolor tła okna podglądu.  
  
 `clrText`  
 Kolor tekstu okna podglądu.  
  
 `plf`  
 Czcionka używana do wyświetlania tekstu w okienku podglądu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setrect"></a>CAtlPreviewCtrlImpl::SetRect  
 Ustawia nowy prostokąt ograniczający dla tego formantu.  
  
```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```  
  
### <a name="parameters"></a>Parametry  
 `prc`  
 Określa nowy rozmiar i położenie formant podglądu.  
  
 `bRedraw`  
 Określa, czy formant powinien być narysowany ponownie.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki COM pulpitu ATL](../../atl/atl-com-desktop-components.md)
