---
title: Klasa CMFCImageEditorDialog
ms.date: 11/19/2018
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
ms.openlocfilehash: 97f16fa00b2e90fd9c43bf9b6792b4eafe7d7b88
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58780448"
---
# <a name="cmfcimageeditordialog-class"></a>Klasa CMFCImageEditorDialog

`CMFCImageEditorDialog` Klasa obsługuje okno dialogowe edytora obrazu.

## <a name="syntax"></a>Składnia

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|Konstruuje `CMFCImageEditorDialog` obiektu.|

## <a name="remarks"></a>Uwagi

`CMFCImageEditorDialog` Klasa udostępnia okno dialogowe, która obejmuje:

- Obszar obrazu, którego używasz do modyfikowania poszczególnych pikseli w obrazie.

- Narzędzia do modyfikowania pikseli w obszarze obrazu do rysowania.

- Palety kolorów, aby określić kolor, który jest używany przez narzędzia do rysowania.

- Obszar (wersja zapoznawcza), który wyświetla efekt edycji.

Poniższa ilustracja przedstawia edytora obrazów, okno dialogowe.

![Okno dialogowe CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "CMFCImageEditorDialog, okno dialogowe")

Jednym ze sposobów, aby użyć `CMFCImageEditorDialog` obiekt jest przekazywany `CBitmap` obrazu do edycji. Nie należy tworzyć duży obraz, ponieważ obraz obszar edytowania ma ograniczony rozmiar, a rozmiar w pikselach logicznej zostanie dopasowana do obszaru. Wywołaj `DoModal` metodę, aby uruchomić okno modalne okno dialogowe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afximageeditordialog.h

##  <a name="cmfcimageeditordialog"></a>  CMFCImageEditorDialog::CMFCImageEditorDialog

Konstruuje `CMFCImageEditorDialog` obiektu.

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>Parametry

*pBitmap*<br/>
Wskaźnik do obrazu.

*pParent*<br/>
Wskaźnik do okna nadrzędnego bieżące okno dialogowe edytora obrazu.

*nBitsPixel*<br/>
Liczba bitów używanych do reprezentowania koloru piksela, który jest również określany jako głębi kolorów.  Jeśli *nBitsPixel* parametru wynosi -1, głębi kolorów jest tworzony na podstawie obrazu, określony przez *pBitmap* parametru. Wartość domyślna to -1.

### <a name="return-value"></a>Wartość zwracana

Aby zmodyfikować obraz, przekazać wskaźnik obrazu do `CMFCImageEditorDialog` konstruktora. Następnie wywołaj `DoModal` metodę, aby otworzyć okno modalne okno dialogowe. Gdy `DoModal` metoda zwróci wartość, mapy bitowej zawiera nowy obraz.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCImageEditorDialog` klasy. W tym przykładzie jest częścią [przykładowe nowych formantów](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>Zobacz także

[Diagram hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
