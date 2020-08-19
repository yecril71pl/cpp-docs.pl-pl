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
ms.openlocfilehash: 3d8bfc40c3c9e937ad5acd7228e49877af65204a
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562158"
---
# <a name="cmfcimagepaintarea-class"></a>Klasa CMFCImagePaintArea

Udostępnia obszar obrazu, który służy do modyfikowania obrazu w oknie dialogowym Edytor obrazu.

## <a name="syntax"></a>Składnia

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCImagePaintArea:: CMFCImagePaintArea](#cmfcimagepaintarea)|Konstruuje `CMFCImagePaintArea` obiekt.|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCImagePaintArea:: GetMode](#getmode)|Pobiera bieżący tryb rysowania.|
|[CMFCImagePaintArea:: setmap](#setbitmap)|Ustawia obraz mapy bitowej dla obszaru obrazu.|
|[CMFCImagePaintArea:: SetColor](#setcolor)|Ustawia bieżący kolor rysowania.|
|[CMFCImagePaintArea:: setMode](#setmode)|Ustawia bieżący tryb rysowania.|

### <a name="remarks"></a>Uwagi

Ta klasa nie jest przeznaczona do użycia bezpośrednio w kodzie.

Struktura używa tej klasy do wyświetlania obszaru obrazu w oknie dialogowym Edytor obrazu. Aby uzyskać więcej informacji na temat okna dialogowego Edytor obrazu, zobacz [Klasa CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania obiektu `CMFCImagePaintArea` klasy, ustawiania bieżącego koloru rysowania, ustawiania bieżącego trybu rysowania i ustawiania obrazu mapy bitowej dla obszaru obrazu.

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afximagepaintarea. h

## <a name="cmfcimagepaintareacmfcimagepaintarea"></a><a name="cmfcimagepaintarea"></a> CMFCImagePaintArea:: CMFCImagePaintArea

Konstruuje `CMFCImagePaintArea` obiekt.

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>Parametry

*pParentDlg*\
podczas Wskaźnik do okna dialogowego, które jest elementem nadrzędnym edytora obrazu.

## <a name="cmfcimagepaintareagetmode"></a><a name="getmode"></a> CMFCImagePaintArea:: GetMode

Pobiera bieżący tryb rysowania.

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) , która określa bieżący tryb rysowania.

## <a name="cmfcimagepaintareasetbitmap"></a><a name="setbitmap"></a> CMFCImagePaintArea:: setmap

Ustawia obraz mapy bitowej dla obszaru obrazu.

```cpp
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*pBitmap*\
podczas Nowy obraz mapy bitowej do wyświetlenia.

### <a name="remarks"></a>Uwagi

Jeśli *pBitmap* ma wartość null, ta metoda ustawia rozmiar obszaru farby modyfikowanej na zero. W przeciwnym razie ustawia rozmiar obszaru farby modyfikowanej na rozmiar podanego obrazu mapy bitowej.

## <a name="cmfcimagepaintareasetcolor"></a><a name="setcolor"></a> CMFCImagePaintArea:: SetColor

Ustawia bieżący kolor rysowania.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*Kolor*\
podczas Nowy kolor rysowania.

### <a name="remarks"></a>Uwagi

Po wybraniu koloru z paska palety edytora obrazu lub selektora kolorów, struktura wywołuje tę metodę, aby zaktualizować bieżący kolor rysowania. Początkowy kolor rysowania jest czarny (wartość COLORREF równa 0).

Kolor rysowania jest używany przez okno dialogowe Edytor obrazów dla wszystkich trybów rysowania, z wyjątkiem IMAGE_EDIT_MODE_COLOR. Aby uzyskać więcej informacji na temat trybów rysowania, zobacz [CMFCImagePaintArea:: IMAGE_EDIT_MODE Enumeration](cmfcimagepaintarea-image-edit-mode-enumeration.md).

## <a name="cmfcimagepaintareasetmode"></a><a name="setmode"></a> CMFCImagePaintArea:: setMode

Ustawia bieżący tryb rysowania.

```cpp
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>Parametry

*wyst*\
podczas Wartość [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) , która określa bieżący tryb rysowania.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)
