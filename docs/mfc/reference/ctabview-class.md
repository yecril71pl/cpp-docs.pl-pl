---
title: Klasa CTabView | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
dev_langs:
- C++
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce47dc5fc0a1d05d2f7200539718fb11c60d810e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718864"
---
# <a name="ctabview-class"></a>Klasa CTabView
`CTabView` Klasa upraszcza korzystanie z klasy formantu karty ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) w aplikacjach korzystających z architektury dokumentu/widoku MFC.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CTabbedView : public CView  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTabView::AddView](#addview)|Dodaje nowy widok do formantu karty.|  
|[CTabView::FindTab](#findtab)|Zwraca indeks określonej widoku w kontrolce karty.|  
|[CTabView::GetActiveView](#getactiveview)|Zwraca wskaźnik do aktualnie aktywnego widoku|  
|[CTabView::GetTabControl](#gettabcontrol)|Zwraca odwołanie do formantu karty skojarzone z tym widokiem.|  
|[CTabView::RemoveView](#removeview)|Usuwa widok z kontrolki karty.|  
|[CTabView::SetActiveView](#setactiveview)|Uaktywnia widoku.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTabView::IsScrollBar](#isscrollbar)|Wywoływane przez platformę, podczas tworzenia karty widoku w celu ustalenia, czy karty widoku ma udostępnionego poziomy pasek przewijania.|  
|[CTabView::OnActivateView](#onactivateview)|Wywoływane przez platformę, gdy karty widoku aktywne lub nieaktywne.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa sprawia, że łatwo umieścić widok z kartami w aplikacji dokument/widok. `CTabView` jest `CView`-pochodne klasy, która zawiera osadzony `CMFCTabCtrl` obiektu. `CTabView` obsługuje wszystkie komunikaty wymagane do obsługi `CMFCTabCtrl` obiektu. Po prostu wyprowadzić klasę z `CTabView` i podłącz go do aplikacji, a następnie dodaj `CView`-klasy pochodne przy użyciu `AddView` metody. Kontrolka karty będą wyświetlane te widoki jako karty.  
  
 Na przykład, Niewykluczone, że dokument, który może być reprezentowany na różne sposoby: jako arkusz kalkulacyjny, wykres edytowalnego formularza i tak dalej. Można utworzyć pojedyncze widoki rysowania danych zgodnie z potrzebami, umieść je w swojej `CTabView`— pochodzi z obiektu i je z zakładkami, bez dodatkowego kodowania.  
  
 [Przykład TabbedView: Aplikacja widok z kartami MFC](../../visual-cpp-samples.md) ilustruje użycie `CTabView`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób `CTabView` jest używana w przykładzie TabbedView.  
  
 [!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxTabView.h  
  
##  <a name="addview"></a>  CTabView::AddView  
 Dodaje widok do formantu karty.  
  
```  
int AddView(
    CRuntimeClass* pViewClass,  
    const CString& strViewLabel,  
    int iIndex=-1,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Parametry  
*pViewClass*<br/>
[in] Wskaźnik do klasy środowiska uruchomieniowego wstawiono widoku.  
  
*strViewLabel*<br/>
[in] Określa tekst karty.  
  
*iIndex*<br/>
[in] Określa położenie liczony od zera, w której mają zostać wstawione w widoku. Jeśli pozycja jest wartość -1 nowa karta zostanie wstawiony na końcu.  
  
*pContext*<br/>
[in] Wskaźnik do `CCreateContext` widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks widoku, jeśli metoda ta powiedzie się. W przeciwnym razie, wartość -1.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję, aby dodać widok do formantu karty, który jest osadzony w ramce.  
  
##  <a name="findtab"></a>  CTabView::FindTab  
 Zwraca indeks określonej widoku w kontrolce karty.  
  
```  
int FindTab(HWND hWndView) const;  
```  
  
### <a name="parameters"></a>Parametry  
*hWndView*<br/>
[in] Uchwyt widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks widoku, jeśli zostanie znaleziony; w przeciwnym razie, wartość -1.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję, aby pobrać indeksu w widoku, który ma określone dojście.  
  
##  <a name="getactiveview"></a>  CTabView::GetActiveView  
 Zwraca wskaźnik do aktualnie aktywnego widoku.  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nieprawidłowy wskaźnik do aktywnego widoku lub wartość NULL, jeśli istnieje aktywnego widoku.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gettabcontrol"></a>  CTabView::GetTabControl  
 Zwraca odwołanie do formantu karty skojarzone z tym widokiem.  
  
```  
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do formantu karty skojarzone z tym widokiem.  
  
##  <a name="isscrollbar"></a>  CTabView::IsScrollBar  
 Wywoływane przez platformę, podczas tworzenia karty widoku w celu ustalenia, czy karty widoku ma udostępnionego poziomy pasek przewijania.  
  
```  
virtual BOOL IsScrollBar() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli karty widoku powinien zostać utworzony wraz z paska przewijania udostępnionych. W przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę podczas *CTabView* obiekt jest tworzony.  
  
 Zastąp *IsScrollBar* method in Class metoda *CTabView*-klasę pochodną i zwraca wartość TRUE, jeśli chcesz utworzyć widok, który został udostępniony poziomy pasek przewijania.  
  
##  <a name="onactivateview"></a>  CTabView::OnActivateView  
 Wywoływane przez platformę, gdy karty widoku aktywne lub nieaktywne.  
  
```  
virtual void OnActivateView(CView* view);
```  
  
### <a name="parameters"></a>Parametry  
*Widok*<br/>
[in] Wskaźnik do widoku.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja nic nie robi. Należy przesłonić tę metodę w `CTabView`-klasy do przetworzenia tego powiadomienia.  
  
##  <a name="removeview"></a>  CTabView::RemoveView  
 Usuwa widok z kontrolki karty.  
  
```  
BOOL RemoveView(int iTabNum);
```  
  
### <a name="parameters"></a>Parametry  
*iTabNum*<br/>
[in] Indeks widok, aby usunąć.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks usunięty widok, jeśli metoda ta powiedzie się. W przeciwnym razie wartość-1.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setactiveview"></a>  CTabView::SetActiveView  
 Uaktywnia widoku.  
  
```  
BOOL SetActiveView(int iTabNum);
```  
  
### <a name="parameters"></a>Parametry  
*iTabNum*<br/>
[in] Liczony od zera indeks karty widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli określony widok zostało aktywowane, FALSE Jeśli indeks tego widoku jest nieprawidłowy.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)   
 [Klasa CView](../../mfc/reference/cview-class.md)
