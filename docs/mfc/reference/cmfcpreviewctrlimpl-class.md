---
title: Klasa CMFCPreviewCtrlImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::Create
- AFXWIN/CMFCPreviewCtrlImpl::Destroy
- AFXWIN/CMFCPreviewCtrlImpl::Focus
- AFXWIN/CMFCPreviewCtrlImpl::GetDocument
- AFXWIN/CMFCPreviewCtrlImpl::Redraw
- AFXWIN/CMFCPreviewCtrlImpl::SetDocument
- AFXWIN/CMFCPreviewCtrlImpl::SetHost
- AFXWIN/CMFCPreviewCtrlImpl::SetPreviewVisuals
- AFXWIN/CMFCPreviewCtrlImpl::SetRect
- AFXWIN/CMFCPreviewCtrlImpl::DoPaint
- AFXWIN/CMFCPreviewCtrlImpl::m_clrBackColor
- AFXWIN/CMFCPreviewCtrlImpl::m_clrTextColor
- AFXWIN/CMFCPreviewCtrlImpl::m_font
- AFXWIN/CMFCPreviewCtrlImpl::m_pDocument
dev_langs:
- C++
helpviewer_keywords:
- CMFCPreviewCtrlImpl [MFC], CMFCPreviewCtrlImpl
- CMFCPreviewCtrlImpl [MFC], Create
- CMFCPreviewCtrlImpl [MFC], Destroy
- CMFCPreviewCtrlImpl [MFC], Focus
- CMFCPreviewCtrlImpl [MFC], GetDocument
- CMFCPreviewCtrlImpl [MFC], Redraw
- CMFCPreviewCtrlImpl [MFC], SetDocument
- CMFCPreviewCtrlImpl [MFC], SetHost
- CMFCPreviewCtrlImpl [MFC], SetPreviewVisuals
- CMFCPreviewCtrlImpl [MFC], SetRect
- CMFCPreviewCtrlImpl [MFC], DoPaint
- CMFCPreviewCtrlImpl [MFC], m_clrBackColor
- CMFCPreviewCtrlImpl [MFC], m_clrTextColor
- CMFCPreviewCtrlImpl [MFC], m_font
- CMFCPreviewCtrlImpl [MFC], m_pDocument
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a94ad813ff72eaed2642e9c78a098b999bf128fa
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040080"
---
# <a name="cmfcpreviewctrlimpl-class"></a>Klasa CMFCPreviewCtrlImpl
Ta klasa implementuje okno, w którym znajduje się w oknie hostów udostępnianych przez powłokę dla podglądu rozbudowanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCPreviewCtrlImpl : public CWnd;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl](#dtor)|Destructs obiektu podglądu formantu.|  
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|Tworzy obiekt kontroli wersji zapoznawczej.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::Create](#create)|Przeciążone. Metoda wywoływana przez program obsługi podglądu rozbudowanego można utworzyć okna systemu Windows.|  
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|Wywoływane przez program obsługi podglądu rozbudowanego, kiedy zachodzi potrzeba zniszczyć tego formantu.|  
|[CMFCPreviewCtrlImpl::Focus](#focus)|Zestawy danych wejściowych fokus do tego formantu.|  
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|Zwraca połączony ten formant podglądu dokumentu.|  
|[CMFCPreviewCtrlImpl::Redraw](#redraw)|Określa, że tego formantu, aby odświeżyć.|  
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|Metoda wywoływana przez Obsługa podglądu, można utworzyć relacji między implementacji dokumentu i Podgląd formantu.|  
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|Ustawia nowy element nadrzędny tego formantu.|  
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Metoda wywoływana przez program obsługi podglądu rozbudowanego kiedy zachodzi potrzeba Ustaw obraz podglądu zawartości.|  
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|Ustawia nowy prostokąt ograniczający dla tego formantu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|Wywoływane przez platformę, by renderować w wersji zapoznawczej.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|Kolor tła okna podglądu.|  
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|Kolor tekstu okna podglądu.|  
|[CMFCPreviewCtrlImpl::m_font](#m_font)|Czcionka używana do wyświetlania tekstu w okienku podglądu.|  
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|Wskaźnik do dokumentu, których zawartość jest przeglądany w formancie.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h    
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimpl"></a> CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
Tworzy obiekt kontroli wersji zapoznawczej.

### <a name="syntax"></a>Składnia
CMFCPreviewCtrlImpl();  

## <a name="create"></a> CMFCPreviewCtrlImpl::Create
Przeciążone. Metoda wywoływana przez program obsługi podglądu rozbudowanego można utworzyć okna systemu Windows.  
  
### <a name="syntax"></a>Składnia  
  
```  
virtual BOOL Create(  
   HWND hWndParent,  
   const RECT* prc  
);  
virtual BOOL Create(  
   HWND hWndParent,  
   const RECT* prc,  
   CCreateContext* pContext  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *hWndParent*  
 Dojście do okna hosta dostarczone przez powłokę dla podglądu rozbudowanego.  
  
 *ChRL*  
 Określa początkowy rozmiar i położenie okna.  
  
 *pContext*  
 Wskaźnik do tworzenia kontekstu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli tworzenie zakończyło się pomyślnie; w przeciwnym razie `FALSE`.  
  
## <a name="destroy"></a> CMFCPreviewCtrlImpl::Destroy
Wywoływane przez program obsługi podglądu rozbudowanego, kiedy zachodzi potrzeba zniszczyć tego formantu.  
  
### <a name="syntax"></a>Składnia  
  
```  
virtual void Destroy();  
```  
  
## <a name="dopaint"></a> CMFCPreviewCtrlImpl::DoPaint  
Wywoływane przez platformę, by renderować w wersji zapoznawczej.  
  
### <a name="syntax"></a>Składnia  
  
```  
virtual void DoPaint(  
   CPaintDC* pDC  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia dla malowania.  


## <a name="focus"></a> CMFCPreviewCtrlImpl::Focus  
Zestawy danych wejściowych fokus do tego formantu.  
  
### <a name="syntax"></a>Składnia  
  
```  
virtual void Focus();  
```  
## <a name="getdocument"></a> CMFCPreviewCtrlImpl::GetDocument
Zwraca połączony ten formant podglądu dokumentu.  
  
### <a name="syntax"></a>Składnia  
  
```  
ATL::IDocument* GetDocument();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do dokumentu, których zawartość jest przeglądany w formancie.

## <a name="m_clrbackcolor"></a> CMFCPreviewCtrlImpl::m_clrBackColor  
Kolor tła okna podglądu.  
  
### <a name="syntax"></a>Składnia  
  
```  
COLORREF m_clrBackColor;  
```  

## <a name="m_clrtextcolor"></a> CMFCPreviewCtrlImpl::m_clrTextColor
Kolor tekstu okna podglądu.  
  
### <a name="syntax"></a>Składnia  
  
```  
COLORREF m_clrTextColor;  
```  
## <a name="m_font"></a> Czcionka CMFCPreviewCtrlImpl::m_font używany do wyświetlania tekstu w okienku podglądu.  
  
### <a name="syntax"></a>Składnia  
  
```  
CFont m_font;  
```  
## <a name="m_pdocument"></a> CMFCPreviewCtrlImpl::m_pDocument  
Wskaźnik do dokumentu, których zawartość jest przeglądany w formancie.  
  
### <a name="syntax"></a>Składnia  
  
```  
ATL::IDocument* m_pDocument;  
```  

## <a name="redraw"></a> CMFCPreviewCtrlImpl::Redraw  
Określa, że tego formantu, aby odświeżyć.  
  
### <a name="syntax"></a>Składnia  
  
```  
virtual void Redraw();  
```  
## <a name="setdocument"></a> CMFCPreviewCtrlImpl::SetDocument 
Metoda wywoływana przez Obsługa podglądu, można utworzyć relacji między implementacji dokumentu i Podgląd formantu.  
  
### <a name="syntax"></a>Składnia  
  
```  
void SetDocument(  
   IDocument* pDocument  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDocument*  
 Wskaźnik do implementacji dokumentu.  

## <a name="sethost"></a> CMFCPreviewCtrlImpl::SetHost  
Ustawia nowy element nadrzędny tego formantu.  
  
### <a name="syntax"></a>Składnia  
  
```  
virtual void SetHost(  
   HWND hWndParent  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *hWndParent*  
 Dojście do nowego okna nadrzędnego.  

## <a name="setpreviewvisuals"></a> CMFCPreviewCtrlImpl::SetPreviewVisuals  
Metoda wywoływana przez program obsługi podglądu rozbudowanego kiedy zachodzi potrzeba Ustaw obraz podglądu zawartości.  
  
### <a name="syntax"></a>Składnia  
  
```  
virtual void SetPreviewVisuals(  
   COLORREF clrBack,  
   COLORREF clrText,  
   const LOGFONTW *plf  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *clrBack*  
 Kolor tła okna podglądu.  
  
 *clrText*  
 Kolor tekstu okna podglądu.  
  
 *PLF*  
 Czcionka używana do wyświetlania tekstu w okienku podglądu. 

##  <a name="setrect"></a> CMFCPreviewCtrlImpl::SetRect  
Ustawia nowy prostokąt ograniczający dla tego formantu.  
  
### <a name="syntax"></a>Składnia  
  
```  
virtual void SetRect(  
   const RECT* prc,  
   BOOL bRedraw  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *ChRL*  
 Określa nowy rozmiar i położenie formant podglądu.  
  
 *bRedraw*  
 Określa, czy formant powinien być narysowany ponownie.  
  
### <a name="remarks"></a>Uwagi  
 Zazwyczaj nowy prostokąt ograniczający jest ustawiona, gdy zmieni się rozmiar kontrolki hosta.  

## <a name="dtor"></a> CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl  
Destructs obiektu podglądu formantu.  
  
### <a name="syntax"></a>Składnia  
  
```  
virtual ~CMFCPreviewCtrlImpl();  
```  
  
