---
title: Klasa CTabView
ms.date: 11/04/2016
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
ms.openlocfilehash: ad30cbbf5de195708d2d357a76c38b661d095c2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365921"
---
# <a name="ctabview-class"></a>Klasa CTabView

Klasa `CTabView` upraszcza użycie klasy kontroli tabulacji [(CMFCTabCtrl)](../../mfc/reference/ctabview-class.md)w aplikacjach korzystających z architektury dokumentu/widoku MFC.

## <a name="syntax"></a>Składnia

```
class CTabbedView : public CView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTabView::AddView](#addview)|Dodaje nowy widok do kontrolki karty.|
|[CTabView::ZnajdźTab](#findtab)|Zwraca indeks określonego widoku w formancie karty.|
|[CTabView::GetActiveView](#getactiveview)|Zwraca wskaźnik do aktualnie aktywnego widoku|
|[CTabView::GetTabControl](#gettabcontrol)|Zwraca odwołanie do formantu karty skojarzonego z widokiem.|
|[CTabView::Usuńview](#removeview)|Usuwa widok z kontrolki karty.|
|[CTabView::SetActiveView](#setactiveview)|Sprawia, że widok jest aktywny.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CTabView::IsscrollBar](#isscrollbar)|Wywoływane przez platformę podczas tworzenia widoku karty, aby ustalić, czy widok karty ma udostępniony poziomy pasek przewijania.|
|[CTabView::OnActivateView](#onactivateview)|Wywoływana przez platformę, gdy widok karty jest aktywny lub nieaktywny.|

## <a name="remarks"></a>Uwagi

Ta klasa ułatwia umieszczenie widoku z kartami w aplikacji dokumentu/widoku. `CTabView`jest `CView`klasą pochodną, która `CMFCTabCtrl` zawiera obiekt osadzony. `CTabView`obsługuje wszystkie komunikaty wymagane `CMFCTabCtrl` do obsługi obiektu. Po prostu wywodź klasę z `CTabView` i `CView`podłącz ją do aplikacji, a następnie dodaj klasy pochodne przy użyciu `AddView` metody. Kontrolka karty wyświetli te widoki jako karty.

Na przykład dokument, który może być reprezentowany na różne sposoby: jako arkusz kalkulacyjny, wykres, edytowalny formularz itd. W razie potrzeby można tworzyć pojedyncze widoki, `CTabView`które rysują dane, wstawiać je do obiektu pochodnego i umieszczać na kartach bez dodatkowego kodowania.

[Przykład widoku z kartami: aplikacja MFC z kartami](../../overview/visual-cpp-samples.md) ilustruje użycie `CTabView`programu .

## <a name="example"></a>Przykład

Poniższy przykład `CTabView` pokazuje, jak jest używany w przykładzie TabbedView.

[!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxTabView.h

## <a name="ctabviewaddview"></a><a name="addview"></a>CTabView::AddView

Dodaje widok do kontrolki karty.

```
int AddView(
    CRuntimeClass* pViewClass,
    const CString& strViewLabel,
    int iIndex=-1,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Parametry

*pViewClass (Klasa widoków)*<br/>
[w] Wskaźnik do klasy środowiska uruchomieniowego wstawionego widoku.

*strViewLabel (Luna StrView)*<br/>
[w] Określa tekst karty.

*Iindex*<br/>
[w] Określa położenie oparte na wartości zero, w którym ma być wstawiany widok. Jeśli pozycja wynosi -1, na końcu zostanie wstawiona nowa karta.

*Pcontext*<br/>
[w] Wskaźnik do `CCreateContext` widoku.

### <a name="return-value"></a>Wartość zwracana

Indeks widoku, jeśli ta metoda powiedzie się. W przeciwnym razie -1.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby dodać widok do kontrolki karty, która jest osadzona w ramce.

## <a name="ctabviewfindtab"></a><a name="findtab"></a>CTabView::ZnajdźTab

Zwraca indeks określonego widoku w formancie karty.

```
int FindTab(HWND hWndView) const;
```

### <a name="parameters"></a>Parametry

*hWndWidWiększ*<br/>
[w] Uchwyt widoku.

### <a name="return-value"></a>Wartość zwracana

Indeks widoku, jeśli zostanie znaleziony; w przeciwnym razie -1.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby pobrać indeks widoku, który ma określony dojście.

## <a name="ctabviewgetactiveview"></a><a name="getactiveview"></a>CTabView::GetActiveView

Zwraca wskaźnik do aktualnie aktywnego widoku.

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Wartość zwracana

Prawidłowy wskaźnik do aktywnego widoku lub NULL, jeśli nie ma aktywnego widoku.

### <a name="remarks"></a>Uwagi

## <a name="ctabviewgettabcontrol"></a><a name="gettabcontrol"></a>CTabView::GetTabControl

Zwraca odwołanie do formantu karty skojarzonego z widokiem.

```
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do formantu karty skojarzonego z widokiem.

## <a name="ctabviewisscrollbar"></a><a name="isscrollbar"></a>CTabView::IsscrollBar

Wywoływane przez platformę podczas tworzenia widoku karty, aby ustalić, czy widok karty ma udostępniony poziomy pasek przewijania.

```
virtual BOOL IsScrollBar() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli widok karty powinien zostać utworzony razem z udostępnionym paskiem przewijania. W przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy tworzony jest obiekt *CTabView.*

Zastąpokaj metodę *IsScrollBar* w klasie *CTabView*-derived i zwróć wartość TRUE, jeśli chcesz utworzyć widok, który ma udostępniony poziomy pasek przewijania.

## <a name="ctabviewonactivateview"></a><a name="onactivateview"></a>CTabView::OnActivateView

Wywoływana przez platformę, gdy widok karty jest aktywny lub nieaktywny.

```
virtual void OnActivateView(CView* view);
```

### <a name="parameters"></a>Parametry

*Widok*<br/>
[w] Wskaźnik do widoku.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nic nie robi. Zastąpić tę `CTabView`metodę w klasie pochodnej do przetwarzania tego powiadomienia.

## <a name="ctabviewremoveview"></a><a name="removeview"></a>CTabView::Usuńview

Usuwa widok z kontrolki karty.

```
BOOL RemoveView(int iTabNum);
```

### <a name="parameters"></a>Parametry

*iTabNum*<br/>
[w] Indeks widoku do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Indeks usuniętego widoku, jeśli ta metoda powiedzie się. W przeciwnym razie -1.

### <a name="remarks"></a>Uwagi

## <a name="ctabviewsetactiveview"></a><a name="setactiveview"></a>CTabView::SetActiveView

Sprawia, że widok jest aktywny.

```
BOOL SetActiveView(int iTabNum);
```

### <a name="parameters"></a>Parametry

*iTabNum*<br/>
[w] Indeks od zera w widoku karty.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli określony widok został aktywny, FALSE, jeśli indeks widoku jest nieprawidłowy.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Cmfctabctrl](../../mfc/reference/ctabview-class.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)
