---
title: Klasa CFormView | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
dev_langs:
- C++
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 386e28631d20721f22eb2b778ffbe2e1d4b1824d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cformview-class"></a>Klasa CFormView
Klasa podstawowa używana dla widoków formularza.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CFormView : public CScrollView  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFormView::CFormView](#cformview)|Konstruuje `CFormView` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|Używane do synchronizacji podczas inicjowania.|  
  
## <a name="remarks"></a>Uwagi  
 Widok formularza jest zasadniczo widoku, który zawiera formanty. Te ułożenia formantów na podstawie zasobu szablonu okna dialogowego. Użyj `CFormView` Chcąc formularzy w aplikacji. Widoki te obsługuje przewijania, zgodnie z potrzebami, za pomocą [CScrollView](../../mfc/reference/cscrollview-class.md) funkcji.  
  
 Po osiągnięciu [tworzenia aplikacji opartych na formularzach](../../mfc/reference/creating-a-forms-based-mfc-application.md), można utworzyć klasy jego widoku na `CFormView`, dzięki czemu aplikacja formularzy.  
  
 Można także wstawić nowy [tematy formularza](../../mfc/form-views-mfc.md) do aplikacji opartych na widok dokumentu. Nawet wtedy, gdy aplikacja nie obsługuje początkowo formularzy, Visual C++ zostanie dodana obsługa tego, po wstawieniu nowego formularza.  
  
 Kreator aplikacji MFC i polecenia Dodaj klasę są preferowanymi metodami do tworzenia aplikacji opartych na formularzach. Jeśli potrzebujesz do tworzenia aplikacji opartych na formularzach bez użycia tych metod, zobacz [tworzenia aplikacji opartych na formularzach](../../mfc/reference/creating-a-forms-based-mfc-application.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cview —](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 `CFormView`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
##  <a name="cformview"></a>CFormView::CFormView  
 Konstruuje `CFormView` obiektu.  
  
```  
CFormView(LPCTSTR lpszTemplateName);  
CFormView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTemplateName`  
 Zawiera ciąg zerem, który jest nazwa zasobu szablonu okna dialogowego.  
  
 `nIDTemplate`  
 Zawiera identyfikator zasobu szablonu okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Podczas tworzenia obiektu typu pochodną `CFormView`, wywołać za pomocą jednego z konstruktorów do utworzenia obiektu widoku i identyfikacji zasobu okna dialogowego, na której oparto widoku. Zasób można zidentyfikować przez nazwę (pass ciąg jako argument do konstruktora) lub za pomocą jego Identyfikatora (pass całkowitą bez znaku jako argument).  
  
 Kontrolki widoku formularza okna i podrzędne nie są tworzone do `CWnd::Create` jest wywoływana. `CWnd::Create`jest wywoływana przez platformę w ramach procesu tworzenia widoku i dokumentów, które wynikają z szablonu dokumentu.  
  
> [!NOTE]
>  Klasy pochodne *musi* podać własne konstruktora. W konstruktorze, należy wywołać konstruktora, `CFormView::CFormView`, o nazwy zasobu lub identyfikatorze jako argument opisane w poprzednim Przegląd klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]  
  
 [!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]  
  
##  <a name="isinitdlgcompleted"></a>CFormView::IsInitDlgCompleted  
 Używane przez MFC, aby upewnić się, że ten Inicjowanie zostało zakończone przed wykonaniem innych operacji.  
  
```  
BOOL IsInitDlgCompleted() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość true, jeśli funkcja inicjowania dla tego okna dialogowego zostało ukończone.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC SNAPVW](../../visual-cpp-samples.md)   
 [Przykładowe MFC VIEWEX](../../visual-cpp-samples.md)   
 [Klasa CScrollView](../../mfc/reference/cscrollview-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cdialog — klasa](../../mfc/reference/cdialog-class.md)   
 [Klasa CScrollView](../../mfc/reference/cscrollview-class.md)
