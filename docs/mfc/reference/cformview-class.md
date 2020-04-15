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
ms.openlocfilehash: a9b897c661731878f0bf78c9d04ae7c4ba28cd42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373798"
---
# <a name="cformview-class"></a>Klasa CFormView

Klasa podstawowa używana dla widoków formularzy.

## <a name="syntax"></a>Składnia

```
class CFormView : public CScrollView
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CFormView::CFormView](#cformview)|Konstruuje `CFormView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFormView::IsInitDlgKokomatne](#isinitdlgcompleted)|Służy do synchronizacji podczas inicjowania.|

## <a name="remarks"></a>Uwagi

Widok formularza jest zasadniczo widok, który zawiera formanty. Te formanty są określone na podstawie zasobu szablonu okna dialogowego. Użyj, `CFormView` jeśli chcesz formularzy w aplikacji. Te widoki obsługują przewijanie, w razie potrzeby, przy użyciu funkcji [CScrollView.](../../mfc/reference/cscrollview-class.md)

Podczas [tworzenia aplikacji opartej](../../mfc/reference/creating-a-forms-based-mfc-application.md)na formularzach można oprzeć `CFormView`jej klasę widoku na , dzięki czemu jest to aplikacja oparta na formularzach.

Można również wstawić nowe [tematy formularzy](../../mfc/form-views-mfc.md) do aplikacji opartych na widoku dokumentu. Nawet jeśli aplikacja początkowo nie obsługuje formularzy, Visual C++ doda tę obsługę po wstawieniu nowego formularza.

Kreator aplikacji MFC i polecenie Dodaj klasę są preferowanymi metodami tworzenia aplikacji opartych na formularzach. Jeśli chcesz utworzyć aplikację opartą na formularzach bez użycia tych metod, zobacz [Tworzenie aplikacji opartej na formularzach](../../mfc/reference/creating-a-forms-based-mfc-application.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[Cscrollview](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="cformviewcformview"></a><a name="cformview"></a>CFormView::CFormView

Konstruuje `CFormView` obiekt.

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Zawiera ciąg zakończony zerem, który jest nazwą zasobu szablonu okna dialogowego.

*nIDTemplate*<br/>
Zawiera numer identyfikatora zasobu szablonu okna dialogowego.

### <a name="remarks"></a>Uwagi

Podczas tworzenia obiektu typu pochodnego `CFormView`z , wywołać jeden z konstruktorów, aby utworzyć obiekt widoku i zidentyfikować zasób okna dialogowego, na którym opiera się widok. Zasób można zidentyfikować według nazwy (przekazać ciąg jako argument do konstruktora) lub jego identyfikator (przekazać niepodpisaną kreślęń całkowitych jako argument).

Okno widoku formularza i formanty `CWnd::Create` podrzędne nie są tworzone, dopóki nie zostanie wywołane. `CWnd::Create`jest wywoływana przez platformę jako część procesu tworzenia dokumentu i widoku, który jest napędzany przez szablon dokumentu.

> [!NOTE]
> Klasa pochodna *musi* dostarczyć własny konstruktor. W konstruktorze wywołać konstruktora, `CFormView::CFormView`z nazwą zasobu lub identyfikator jako argument, jak pokazano w poprzednim omówieniu klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

## <a name="cformviewisinitdlgcompleted"></a><a name="isinitdlgcompleted"></a>CFormView::IsInitDlgKokomatne

Używane przez MFC, aby upewnić się, że inicjowanie jest zakończone przed wykonaniem innych operacji.

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli funkcja inicjowania dla tego okna dialogowego została ukończona.

## <a name="see-also"></a>Zobacz też

[Próbka MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Przykładowy viewex MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CScrollView](../../mfc/reference/cscrollview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Klasa CScrollView](../../mfc/reference/cscrollview-class.md)
