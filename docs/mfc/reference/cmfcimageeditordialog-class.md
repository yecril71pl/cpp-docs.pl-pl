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
ms.openlocfilehash: 23c2a919428689fe107b82041bd87b758ede2bc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367466"
---
# <a name="cmfcimageeditordialog-class"></a>Klasa CMFCImageEditorDialog

Klasa `CMFCImageEditorDialog` obsługuje okno dialogowe edytora obrazów.

## <a name="syntax"></a>Składnia

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|Konstruuje `CMFCImageEditorDialog` obiekt.|

## <a name="remarks"></a>Uwagi

Klasa `CMFCImageEditorDialog` zawiera okno dialogowe, które zawiera:

- Obszar obrazu używany do modyfikowania pojedynczych pikseli obrazu.

- Narzędzia do rysowania w celu zmodyfikowania pikseli w obszarze obrazu.

- Paleta kolorów określająca kolor używany przez narzędzia do rysowania.

- Obszar podglądu, który wyświetla efekt edycji.

Na poniższej ilustracji przedstawiono okno dialogowe edytora obrazów.

![OKNO dialogowe CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "OKNO dialogowe CMFCImageEditorDialog")

Jednym ze sposobów `CMFCImageEditorDialog` użycia obiektu jest `CBitmap` przekazanie go obrazowi do edycji. Nie należy tworzyć dużego obrazu, ponieważ obszar edycji obrazu ma ograniczony rozmiar, a rozmiar piksela logicznego jest dostosowany do obszaru. Wywołanie `DoModal` metody, aby rozpocząć modalne okno dialogowe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[Cdialogex](../../mfc/reference/cdialogex-class.md)

[Cmfcimageeditordialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afximageeditordialog.h

## <a name="cmfcimageeditordialogcmfcimageeditordialog"></a><a name="cmfcimageeditordialog"></a>CMFCImageEditorDialog::CMFCImageEditorDialog

Konstruuje `CMFCImageEditorDialog` obiekt.

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>Parametry

*pBitmapa*<br/>
Wskaźnik do obrazu.

*pRoczysz*<br/>
Wskaźnik do okna nadrzędnego bieżącego okna dialogowego edytora obrazów.

*nBitsPixel (100)*<br/>
Liczba bitów używanych do reprezentowania koloru pojedynczego piksela, który jest również określany jako głębia kolorów.  Jeśli parametr *nBitsPixel* wynosi -1, głębia kolorów jest wyprowadzana z obrazu określonego przez parametr *pBitmap.* Wartość domyślna to -1.

### <a name="return-value"></a>Wartość zwracana

Aby zmodyfikować obraz, przekaż wskaźnik `CMFCImageEditorDialog` obrazu do konstruktora. Następnie wywołaj metodę, `DoModal` aby otworzyć modalne okno dialogowe. Gdy `DoModal` metoda zwraca, mapa bitowa zawiera nowy obraz.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCImageEditorDialog` skonstruować obiekt klasy. W tym przykładzie jest częścią [new controls próbki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
