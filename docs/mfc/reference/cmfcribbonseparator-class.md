---
title: Klasa CMFCRibbonSeparator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonSeparator [MFC], CMFCRibbonSeparator
- CMFCRibbonSeparator [MFC], AddToListBox
- CMFCRibbonSeparator [MFC], CopyFrom
- CMFCRibbonSeparator [MFC], GetRegularSize
- CMFCRibbonSeparator [MFC], IsSeparator
- CMFCRibbonSeparator [MFC], IsTabStop
- CMFCRibbonSeparator [MFC], OnDraw
- CMFCRibbonSeparator [MFC], OnDrawOnList
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1c4c3b286f020d8d409b344c5d8c05ebc200425
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370861"
---
# <a name="cmfcribbonseparator-class"></a>Klasa CMFCRibbonSeparator
Implementuje separatora wstążki.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonSeparator : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|Konstruuje `CMFCRibbonSeparator` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Separator, który dodaje **polecenia** na liście **Dostosuj** okno dialogowe. (Przesłania [CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|  
|`CMFCRibbonSeparator::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CMFCRibbonSeparator::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|Metoda kopiowania, która ustawia zmienne Członkowskie separatora z innego obiektu.|  
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|Zwraca rozmiar separatora.|  
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|Wskazuje, czy jest separatora.|  
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Wskazuje, czy jest tabulatora.|  
|[CMFCRibbonSeparator::OnDraw](#ondraw)|Metoda wywoływana przez system do rysowania separator na Wstążce lub paska narzędzi Szybki dostęp.|  
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Wywoływane przez system do rysowania separator **polecenia** listy.|  
  
## <a name="remarks"></a>Uwagi  
 Separator wstążki jest logicznie oddziela wstążki elementy linii pionowych lub poziomych. Separator mogą być wystawiane na formantu wstążki, w menu głównym aplikacji na pasku stanu Wstążki i paska narzędzi Szybki dostęp.  
  
 Aby użyć separator w aplikacji, utworzyć nowy obiekt i dodaj go do menu głównego aplikacji, jak pokazano poniżej:  
  
```  
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...  
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```  
Wywołanie [CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) można dodać do wstążki paneli separatorów. Separatory są przydzielane i dodać wewnętrznie przez `AddSeparator` metody.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxbaseribbonelement.h  
  
##  <a name="addtolistbox"></a>  CMFCRibbonSeparator::AddToListBox  
 Separator, który dodaje **polecenia** na liście **Dostosuj** okno dialogowe.  
  
```  
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,  
    BOOL bDeep);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pWndListBox`  
 Wskaźnik do **polecenia** gdzie jest dodana separatora listy.  
  
 [in] `bDeep`  
 Ignorowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks na ciąg w polu listy, określony przez `pWndListBox`.  
  
##  <a name="cmfcribbonseparator"></a>  CMFCRibbonSeparator::CMFCRibbonSeparator  
 Konstruuje `CMFCRibbonSeparator` obiektu.  
  
```  
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bIsHoriz`  
 Jeśli `TRUE`, separator jest poziomy; Jeśli `FALSE`, separator jest pionowy.  
  
### <a name="remarks"></a>Uwagi  
 Poziomy separatorów są używane w menu aplikacji. Pionowy separatorów są używane na paskach narzędzi.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCRibbonSeparator` klasy.  
  
 [!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]  
  
##  <a name="copyfrom"></a>  CMFCRibbonSeparator::CopyFrom  
 Metoda kopiowania, która ustawia zmienne Członkowskie separatora z innego obiektu.  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `Src`  
 Element wstążki źródła do skopiowania.  
  
##  <a name="getregularsize"></a>  CMFCRibbonSeparator::GetRegularSize  
 Zwraca rozmiar separatora.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDC`  
 Wskaźnik do zawartości urządzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar separatora w kontekście danego urządzenia.  
  
##  <a name="isseparator"></a>  CMFCRibbonSeparator::IsSeparator  
 Wskazuje, czy jest separatora.  
  
```  
virtual BOOL IsSeparator() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze `TRUE` dla tej klasy.  
  
##  <a name="istabstop"></a>  CMFCRibbonSeparator::IsTabStop  
 Wskazuje, czy jest tabulatora.  
  
```  
virtual BOOL IsTabStop() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze `FALSE` dla tej klasy.  
  
### <a name="remarks"></a>Uwagi  
 Separator wstążki nie jest tabulatora.  
  
##  <a name="ondraw"></a>  CMFCRibbonSeparator::OnDraw  
 Metoda wywoływana przez system do rysowania separator na Wstążce lub paska narzędzi Szybki dostęp.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
##  <a name="ondrawonlist"></a>  CMFCRibbonSeparator::OnDrawOnList  
 Wywoływane przez system do rysowania separator **polecenia** listy.  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in] `pDC`|Wskaźnik do kontekstu urządzenia.|  
|[in] `strText`|Tekst wyświetlany na liście.|  
|[in] `nTextOffset`|Odstęp między tekstem a prostokątem z lewej strony.|  
|[in] `rect`|Określa prostokątem.|  
|[in] `bIsSelected`|Ignorowane.|  
|[in] `bHighlighted`|Ignorowane.|  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
