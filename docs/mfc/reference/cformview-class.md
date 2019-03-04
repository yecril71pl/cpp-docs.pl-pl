---
title: Klasa CFormView
ms.date: 11/04/2016
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
ms.openlocfilehash: 4d1f6a19e0fb2ddb88602600e02aec45936ce599
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305110"
---
# <a name="cformview-class"></a>Klasa CFormView

Klasa podstawowa używana w widokach formularza.

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
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|Używane na potrzeby synchronizacji podczas inicjowania.|

## <a name="remarks"></a>Uwagi

Widok formularza jest zasadniczo widok, który zawiera formanty. Te kontrolki są ułożone w zależności od zasobów szablonu okna dialogowego. Użyj `CFormView` chcącym formularzy w aplikacji. Widoki te obsługują przewijanie, stosownie do potrzeb, przy użyciu [CScrollView](../../mfc/reference/cscrollview-class.md) funkcji.

Po osiągnięciu [tworzenia aplikacji opartej na formularzach](../../mfc/reference/creating-a-forms-based-mfc-application.md), swojej klasie widoku można oprzeć na `CFormView`, dzięki czemu aplikacją opartą na formularzach.

Można także wstawić nowy [tematy formularza](../../mfc/form-views-mfc.md) do aplikacji na podstawie widoku dokumentu. Nawet jeśli aplikacja nie obsługuje początkowo formularzy, Visual C++ doda tej obsługi podczas wstawiania nowego formularza.

Kreator aplikacji MFC i polecenia Dodaj klasę są preferowanymi metodami do tworzenia aplikacji opartej na formularzach. Jeśli potrzebujesz do tworzenia aplikacji opartej na formularzach bez korzystania z tych metod, zobacz [tworzenia aplikacji opartej na formularzach](../../mfc/reference/creating-a-forms-based-mfc-application.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

##  <a name="cformview"></a>  CFormView::CFormView

Konstruuje `CFormView` obiektu.

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Zawiera ciąg zakończony zerem, która jest nazwą zasobu szablonu okna dialogowego.

*nIDTemplate*<br/>
Zawiera identyfikator zasobu szablonu okna dialogowego.

### <a name="remarks"></a>Uwagi

Po utworzeniu obiektu typu pochodną `CFormView`, wywołać za pomocą jednego z konstruktorów do utworzenia obiektu widoku i identyfikacji zasobu okna dialogowego, na którym bazuje widoku. Zasób można zidentyfikować przez nazwę (pass ciąg jako argument konstruktora) lub za pomocą jego Identyfikatora (pass liczbą całkowitą bez znaku jako argument).

Widok formularza formanty okna i podrzędne nie są tworzone do momentu `CWnd::Create` jest wywoływana. `CWnd::Create` jest wywoływana przez framework jako część procesu tworzenia dokument i widok, który jest wymuszany przez szablon dokumentu.

> [!NOTE]
>  Klasy pochodne *musi* podać swój własny konstruktora. W konstruktorze, należy wywołać konstruktora, `CFormView::CFormView`, przy użyciu nazwy zasobu lub identyfikator jako argument, jak pokazano na poprzednim klasa — Przegląd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

##  <a name="isinitdlgcompleted"></a>  CFormView::IsInitDlgCompleted

Używane przez MFC, aby upewnić się, że Inicjowanie zostało zakończone przed przystąpieniem do wykonywania innych operacji.

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli funkcja inicjowania dla tego okna dialogowego zostało ukończone.

## <a name="see-also"></a>Zobacz także

[Próbki MFC SNAPVW](../../visual-cpp-samples.md)<br/>
[Próbki MFC VIEWEX](../../visual-cpp-samples.md)<br/>
[Klasa CScrollView](../../mfc/reference/cscrollview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Klasa CScrollView](../../mfc/reference/cscrollview-class.md)
