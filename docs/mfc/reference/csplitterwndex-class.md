---
title: Klasa CSplitterWndEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
dev_langs:
- C++
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ae4a24424acc4385927e0f7c99735bd50a6d472
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121653"
---
# <a name="csplitterwndex-class"></a>Klasa CSplitterWndEx



Reprezentuje okna dzielącego dostosowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSplitterWndEx : public CSplitterWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CSplitterWndEx::CSplitterWndEx`|Domyślny konstruktor.|  
|`CSplitterWndEx::~CSplitterWndEx`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Wywoływane przez platformę, by narysować okno podziału. (Przesłania [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|  
  
## <a name="remarks"></a>Uwagi  
 Zastąpienie `OnDrawSplitter` metodę w celu dostosowania wyglądu graficznego składników okna podziału.  
  
 `CSplitterWndEx` Klasa jest używana razem z [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox), i [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) metody, które są implementowana przez Menedżera visual. Powoduje visual Menedżera do rysowania okna dzielącego w aplikacji, należy zastąpić deklaracje `CSplitterWnd` klasy z `CSplitterWndEx` klasy. W przypadku ramki okna aplikacji klasy okna podziału jest zadeklarowana w cmainframe — klasa, która znajduje się w mainfrm.h. Na przykład zobacz `OutlookDemo` przykładowa w katalogu przykładów.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 [CSplitterWnd](csplitterwnd-class.md)  
   
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxsplitterwndex.h  
  
##  <a name="ondrawsplitter"></a>  CSplitterWndEx::OnDrawSplitter  
 Wywoływane przez platformę, by narysować okno podziału.  
  
```  
virtual void OnDrawSplitter(  
   CDC* pDC,  
   ESplitType nType,  
   const CRect& rect   
);  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia. Jeśli ten parametr ma wartość NULL, w ramach ponownie rysuje aktywne okno.  
  
 [in] *Npowiadomienia*  
 Jeden z `CSplitterWnd::ESplitType` wartości wyliczenia, które określa element okna podziału do rysowania. Prawidłowe wartości to `splitBox`, `splitBar`, `splitIntersection`, i `splitBorder`.  
  
 [in] *rect*  
 Prostokąt ograniczający Określa wymiary i lokalizację do rysowania elementu okna podziału określony.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../hierarchy-chart.md)   
 [Klasy](mfc-classes.md)   
 [Klasa CSplitterWnd](csplitterwnd-class.md)   
 [Klasa CMFCVisualManager](cmfcvisualmanager-class.md)