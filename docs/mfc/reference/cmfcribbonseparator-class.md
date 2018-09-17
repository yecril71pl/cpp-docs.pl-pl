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
ms.openlocfilehash: e9112a6790175709a2575319c6f71a55d1303a83
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705318"
---
# <a name="cmfcribbonseparator-class"></a>Klasa CMFCRibbonSeparator
Implementuje separator wstążki.  
  
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
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Separator, który dodaje **polecenia** listy w **Dostosuj** okno dialogowe. (Przesłania [CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|  
|`CMFCRibbonSeparator::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CMFCRibbonSeparator::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|Metoda kopiowania, który określa zmienne Członkowskie separator z innego obiektu.|  
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|Zwraca rozmiar separatora.|  
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|Wskazuje, czy jest separatorem.|  
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Wskazuje, czy jest tabulatora.|  
|[CMFCRibbonSeparator::OnDraw](#ondraw)|Metoda wywoływana przez system do rysowania separatora Wstążki lub paska narzędzi Szybki dostęp.|  
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Wywoływane przez system, aby narysować separatora na **polecenia** listy.|  
  
## <a name="remarks"></a>Uwagi  
 Separator wstążki jest linii pionowych lub poziomych, logicznie dzieli elementy wstążki. Separator mogą być wystawiane na formantu wstążki, w menu aplikacji głównej, paska stanu Wstążki i paska narzędzi Szybki dostęp.  
  
 Aby użyć separatora w aplikacji, utworzenia nowego obiektu i dodać go do menu głównego aplikacji, jak pokazano poniżej:  
  
```  
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...  
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```  
Wywołaj [CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) Dodawanie separatorów do paneli wstążki. Separatory są przydzielane i dodać wewnętrznie przez `AddSeparator` metody.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxbaseribbonelement.h  
  
##  <a name="addtolistbox"></a>  CMFCRibbonSeparator::AddToListBox  
 Separator, który dodaje **polecenia** listy w **Dostosuj** okno dialogowe.  
  
```  
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,  
    BOOL bDeep);
```  
  
### <a name="parameters"></a>Parametry  
*pWndListBox*<br/>
[in] Wskaźnik do **polecenia** listy, w której zostanie dodany separatora.  
  
*bDeep*<br/>
[in] Ignorowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks na ciąg w polu listy, określony przez *pWndListBox*.  
  
##  <a name="cmfcribbonseparator"></a>  CMFCRibbonSeparator::CMFCRibbonSeparator  
 Konstruuje `CMFCRibbonSeparator` obiektu.  
  
```  
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
*bIsHoriz*<br/>
[in] W przypadku opcji TRUE separatora jest poziomy; w przypadku wartości FAŁSZ separatora jest pionowy.  
  
### <a name="remarks"></a>Uwagi  
 W menu aplikacji używane są separatory poziomej. Rozwiń na paskach narzędzi używane są separatory pionowy.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCRibbonSeparator` klasy.  
  
 [!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]  
  
##  <a name="copyfrom"></a>  CMFCRibbonSeparator::CopyFrom  
 Metoda kopiowania, który określa zmienne Członkowskie separator z innego obiektu.  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Parametry  
*src*<br/>
[in] Element wstążki źródła do skopiowania.  
  
##  <a name="getregularsize"></a>  CMFCRibbonSeparator::GetRegularSize  
 Zwraca rozmiar separatora.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do zawartości urządzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar separatora w kontekście danego urządzenia.  
  
##  <a name="isseparator"></a>  CMFCRibbonSeparator::IsSeparator  
 Wskazuje, czy jest separatorem.  
  
```  
virtual BOOL IsSeparator() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze ma wartość TRUE dla tej klasy.  
  
##  <a name="istabstop"></a>  CMFCRibbonSeparator::IsTabStop  
 Wskazuje, czy jest tabulatora.  
  
```  
virtual BOOL IsTabStop() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze wartość FALSE dla tej klasy.  
  
### <a name="remarks"></a>Uwagi  
 Separator wstążki jest tabulatora.  
  
##  <a name="ondraw"></a>  CMFCRibbonSeparator::OnDraw  
 Metoda wywoływana przez system do rysowania separatora Wstążki lub paska narzędzi Szybki dostęp.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.  
  
##  <a name="ondrawonlist"></a>  CMFCRibbonSeparator::OnDrawOnList  
 Wywoływane przez system, aby narysować separatora na **polecenia** listy.  
  
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
|*podstawowego kontrolera domeny*|[in] Wskaźnik do kontekstu urządzenia.|  
|*strText*|[in] Tekst wyświetlany na liście.|  
|*nTextOffset*|[in] Odstęp między tekstem a po lewej stronie prostokąt otaczający.|  
|*Rect*|[in] Określa prostokąt otaczający.|  
|*bIsSelected*|[in] Ignorowane.|  
|*bHighlighted*|[in] Ignorowane.|  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
