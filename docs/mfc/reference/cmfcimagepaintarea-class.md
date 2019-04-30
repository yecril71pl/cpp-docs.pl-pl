---
title: CMFCImagePaintArea Class
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
ms.openlocfilehash: 37d975ace4d144cc6274b49a3406382f0fb300ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374184"
---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea Class

Zapewnia obszar obrazu, który umożliwia modyfikowanie obrazu w okno dialogowe edytora obrazu.

## <a name="syntax"></a>Składnia

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|Konstruuje `CMFCImagePaintArea` obiektu.|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCImagePaintArea::GetMode](#getmode)|Pobiera bieżący tryb rysowania.|
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|Ustawia obraz mapy bitowej dla obszaru obrazu.|
|[CMFCImagePaintArea::SetColor](#setcolor)|Ustawia bieżący kolor rysowania.|
|[CMFCImagePaintArea::SetMode](#setmode)|Ustawia bieżący tryb rysowania.|

### <a name="remarks"></a>Uwagi

Ta klasa nie jest przeznaczona do użycia bezpośrednio w kodzie.

Struktura używa tej klasy, aby wyświetlić obszar obrazu w okno dialogowe edytora obrazu. Aby uzyskać więcej informacji na temat okno dialogowe edytora obrazu, zobacz [klasa CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCImagePaintArea` klasy, należy ustawić bieżącą rysowania kolorów, Ustaw bieżący tryb rysowania i Ustaw obraz mapy bitowej dla obszaru obrazu.

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afximagepaintarea.h

##  <a name="cmfcimagepaintarea"></a>  CMFCImagePaintArea::CMFCImagePaintArea

Konstruuje `CMFCImagePaintArea` obiektu.

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pParentDlg*|[in] Wskaźnik do okna dialogowego, który jest elementem nadrzędnym edytora obrazów.|

##  <a name="getmode"></a>  CMFCImagePaintArea::GetMode

Pobiera bieżący tryb rysowania.

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>Wartość zwracana

[Image_edit_mode —](cmfcimagepaintarea-image-edit-mode-enumeration.md) wartość, która określa bieżący tryb rysowania.

##  <a name="setbitmap"></a>  CMFCImagePaintArea::SetBitmap

Ustawia obraz mapy bitowej dla obszaru obrazu.

```
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pBitmap*|[in] Nowy obraz mapy bitowej do wyświetlenia.|

### <a name="remarks"></a>Uwagi

Jeśli *pBitmap* ma wartość NULL, ta metoda ustawia rozmiar obszaru paint modyfikowane przez zero. W przeciwnym razie ustawia rozmiar obszaru można modyfikować paint, rozmiar obrazu mapy bitowej podana.

##  <a name="setcolor"></a>  CMFCImagePaintArea::SetColor

Ustawia bieżący kolor rysowania.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Kolor*|[in] Nowy kolor rysowania.|

### <a name="remarks"></a>Uwagi

Kiedy wybrać kolor z palety paska edytora obrazu lub selektora kolorów, struktura wywołuje tę metodę w celu aktualizacji bieżący kolor rysowania. Początkowy kolor rysunku jest czarny (COLORREF wartość 0).

Rysowanie kolor jest używany przez okno dialogowe edytora obrazu we wszystkich trybach rysowania, z wyjątkiem IMAGE_EDIT_MODE_COLOR. Aby uzyskać więcej informacji na temat trybów rysowania, zobacz [wyliczenie CMFCImagePaintArea::IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md).

##  <a name="setmode"></a>  CMFCImagePaintArea::SetMode

Ustawia bieżący tryb rysowania.

```
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Tryb*|[in] [Image_edit_mode —](cmfcimagepaintarea-image-edit-mode-enumeration.md) wartość, która określa bieżący tryb rysowania.|

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)
