---
title: Klasa CMFCImagePaintArea
ms.date: 11/04/2016
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
ms.openlocfilehash: 4e73bd7bc1a28317dbfc452df1f45541dfcbfd21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374435"
---
# <a name="cmfcimagepaintarea-class"></a>Klasa CMFCImagePaintArea

Udostępnia obszar obrazu używany do modyfikowania obrazu w oknie dialogowym edytora obrazów.

## <a name="syntax"></a>Składnia

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|Konstruuje `CMFCImagePaintArea` obiekt.|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCImagePaintArea::GetMode](#getmode)|Pobiera bieżący tryb rysowania.|
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|Ustawia obraz bitmapowy dla obszaru obrazu.|
|[CMFCImagePaintArea::SetColor](#setcolor)|Ustawia bieżący kolor rysunku.|
|[CMFCImagePaintArea::SetMode](#setmode)|Ustawia bieżący tryb rysowania.|

### <a name="remarks"></a>Uwagi

Ta klasa nie jest przeznaczona do użycia bezpośrednio z kodu.

Struktura używa tej klasy do wyświetlania obszaru obrazu w oknie dialogowym edytora obrazów. Aby uzyskać więcej informacji na temat okna dialogowego edytora obrazów, zobacz [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCImagePaintArea` skonstruować obiekt klasy, ustawić bieżący kolor rysunku, ustawić bieżący tryb rysowania i ustawić obraz bitmapowy dla obszaru obrazu.

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cbutton](../../mfc/reference/cbutton-class.md)

[CMFCImageObszar](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afximagepaintarea.h

## <a name="cmfcimagepaintareacmfcimagepaintarea"></a><a name="cmfcimagepaintarea"></a>CMFCImagePaintArea::CMFCImagePaintArea

Konstruuje `CMFCImagePaintArea` obiekt.

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pParentDlg*|[w] Wskaźnik do okna dialogowego, który jest elementem nadrzędnym edytora obrazów.|

## <a name="cmfcimagepaintareagetmode"></a><a name="getmode"></a>CMFCImagePaintArea::GetMode

Pobiera bieżący tryb rysowania.

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) określająca bieżący tryb rysowania.

## <a name="cmfcimagepaintareasetbitmap"></a><a name="setbitmap"></a>CMFCImagePaintArea::SetBitmap

Ustawia obraz bitmapowy dla obszaru obrazu.

```
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pBitmapa*|[w] Nowy obraz mapy bitowej do wyświetlenia.|

### <a name="remarks"></a>Uwagi

Jeśli *pBitmap* ma wartość NULL, ta metoda ustawia rozmiar modyfikowalnej powierzchni farby na zero. W przeciwnym razie ustawia rozmiar obszaru modyfikowalnej farby na rozmiar dostarczonego obrazu bitmapowego.

## <a name="cmfcimagepaintareasetcolor"></a><a name="setcolor"></a>CMFCImagePaintArea::SetColor

Ustawia bieżący kolor rysunku.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*color*|[w] Nowy kolor rysunku.|

### <a name="remarks"></a>Uwagi

Po wybraniu koloru z paska palety edytora obrazów lub selektora kolorów, struktura wywołuje tę metodę, aby zaktualizować bieżący kolor rysunku. Początkowy kolor rysunku jest czarny (wartość COLORREF 0).

Kolor rysunku jest używany w oknie dialogowym edytora obrazów dla wszystkich trybów rysowania z wyjątkiem IMAGE_EDIT_MODE_COLOR. Aby uzyskać więcej informacji na temat trybów rysowania, zobacz [CMFCImagePaintArea::IMAGE_EDIT_MODE Wyliczenie](cmfcimagepaintarea-image-edit-mode-enumeration.md).

## <a name="cmfcimagepaintareasetmode"></a><a name="setmode"></a>CMFCImagePaintArea::SetMode

Ustawia bieżący tryb rysowania.

```
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Tryb*|[w] Wartość [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) określająca bieżący tryb rysowania.|

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)
