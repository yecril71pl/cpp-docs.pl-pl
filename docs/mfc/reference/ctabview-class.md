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
ms.openlocfilehash: 08c0cff2f6586ab5e385808fb806ed435b00bfc9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ctabview-class"></a>Klasa CTabView
`CTabView` Klasa upraszcza korzystanie z klasy formantu karty ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) w aplikacjach korzystających z architektury dokument/widok MFC.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CTabbedView : public CView  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTabView::AddView](#addview)|Dodaje nowy widok do formantu karty.|  
|[CTabView::FindTab](#findtab)|Zwraca indeks określony widok formantu karty.|  
|[CTabView::GetActiveView](#getactiveview)|Zwraca wskaźnik do aktywnego widoku|  
|[CTabView::GetTabControl](#gettabcontrol)|Zwraca odwołanie do formantu karty skojarzone z tym widokiem.|  
|[CTabView::RemoveView](#removeview)|Usuwa widok z formantu karty.|  
|[CTabView::SetActiveView](#setactiveview)|Uaktywnia widoku.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTabView::IsScrollBar](#isscrollbar)|Wywoływane przez platformę, podczas tworzenia widoku kartę, aby określić, czy widok kartę udostępnionego poziomy pasek przewijania.|  
|[CTabView::OnActivateView](#onactivateview)|Wywoływane przez platformę, gdy widok kartę nawiązuje aktywne lub nieaktywne.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa ułatwia poddane z kartami widoku aplikacji dokument/widok. `CTabView` jest `CView`-klasy, która zawiera osadzony `CMFCTabCtrl` obiektu. `CTabView` obsługuje wszystkie komunikaty muszą obsługiwać `CMFCTabCtrl` obiektu. Po prostu wyprowadzenia klasy z `CTabView` i podłącz go do aplikacji, a następnie dodaj `CView`-klas pochodnych przy użyciu `AddView` metody. Formant karty wyświetli tych widoków jako karty.  
  
 Na przykład może być dokumentu, który może być reprezentowany na różne sposoby: jako arkusz kalkulacyjny, wykres można edytować formularza i tak dalej. Można tworzyć widoki poszczególnych pobieranie danych, zgodnie z potrzebami, wstawić je do Twojej `CTabView`-pochodnych obiektu i je z kartami bez żadnych dodatkowych kodowania.  
  
 [Przykład TabbedView: Aplikacji MFC w kartach widoku](../../visual-cpp-samples.md) przedstawiono użycie `CTabView`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób `CTabView` jest używany w przykładowym TabbedView.  
  
 [!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxTabView.h  
  
##  <a name="addview"></a>  CTabView::AddView  
 Dodaje widoku do formantu karty.  
  
```  
int AddView(
    CRuntimeClass* pViewClass,  
    const CString& strViewLabel,  
    int iIndex=-1,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pViewClass`  
 Wskaźnik do klasy środowiska uruchomieniowego wstawionego widoku.  
  
 [in] `strViewLabel`  
 Określa tekst zakładki.  
  
 [in] `iIndex`  
 Określa pozycję liczony od zera, w której mają zostać wstawione w widoku. Jeśli pozycja jest wartość -1 nową kartę są wstawiane na końcu.  
  
 [in] `pContext`  
 Wskaźnik do `CCreateContext` widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks widoku, jeśli ta metoda zakończy się powodzeniem. W przeciwnym razie wartość -1.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby dodać widok do formantu karty, który jest osadzony w ramce.  
  
##  <a name="findtab"></a>  CTabView::FindTab  
 Zwraca indeks określony widok formantu karty.  
  
```  
int FindTab(HWND hWndView) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] `hWndView`  
 Dojście widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks widoku, jeśli został znaleziony; w przeciwnym razie wartość -1.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można pobrać indeksu w widoku, który ma określony uchwyt.  
  
##  <a name="getactiveview"></a>  CTabView::GetActiveView  
 Zwraca wskaźnik do aktywnego widoku.  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nieprawidłowy wskaźnik do aktywnego widoku lub `NULL` przypadku aktywnego widoku.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gettabcontrol"></a>  CTabView::GetTabControl  
 Zwraca odwołanie do formantu karty skojarzone z tym widokiem.  
  
```  
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do formantu karty skojarzone z tym widokiem.  
  
##  <a name="isscrollbar"></a>  CTabView::IsScrollBar  
 Wywoływane przez platformę, podczas tworzenia widoku kartę, aby określić, czy widok kartę udostępnionego poziomy pasek przewijania.  
  
```  
virtual BOOL IsScrollBar() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli można utworzyć widoku kartę, wraz z udostępnionego przewijania na pasku przewijania. W przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę po `CTabView` utworzeniu obiektu.  
  
 Zastąpienie `IsScrollBar` metody w `CTabView`-pochodzi z klasy i przywracać `TRUE` Jeśli chcesz utworzyć widok, który został udostępniony poziomy pasek przewijania.  
  
##  <a name="onactivateview"></a>  CTabView::OnActivateView  
 Wywoływane przez platformę, gdy widok kartę nawiązuje aktywne lub nieaktywne.  
  
```  
virtual void OnActivateView(CView* view);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `view`  
 Wskaźnik do widoku.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja nie działa. Należy przesłonić tę metodę w `CTabView`-klasy do przetworzenia tego powiadomienia.  
  
##  <a name="removeview"></a>  CTabView::RemoveView  
 Usuwa widok z formantu karty.  
  
```  
BOOL RemoveView(int iTabNum);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `iTabNum`  
 Indeks widoku do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks widoku usunięte, jeśli ta metoda zakończy się powodzeniem. W przeciwnym razie wartość-1.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setactiveview"></a>  CTabView::SetActiveView  
 Uaktywnia widoku.  
  
```  
BOOL SetActiveView(int iTabNum);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `iTabNum`  
 Liczony od zera indeks w widoku kartę.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli określony widok została uaktywniona, `FALSE` Jeśli indeks widoku jest nieprawidłowy.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)   
 [Klasa CView](../../mfc/reference/cview-class.md)
