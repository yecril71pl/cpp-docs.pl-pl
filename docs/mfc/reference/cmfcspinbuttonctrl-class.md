---
title: Klasa CMFCSpinButtonCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
ms.openlocfilehash: 60808359c11604368493031e1b6f4573b3b2026f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410103"
---
# <a name="cmfcspinbuttonctrl-class"></a>Klasa CMFCSpinButtonCtrl

`CMFCSpinButtonCtrl` Klasa obsługuje Menedżer wizualnego, który rysuje kontrolkę przycisku pokrętła.

## <a name="syntax"></a>Składnia

```
class CMFCSpinButtonCtrl : public CSpinButtonCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|Domyślny konstruktor.|
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|Odświeża bieżący kontrolka przycisku pokrętła.|

## <a name="remarks"></a>Uwagi

Aby za pomocą Menedżer wizualnego narysuj kontrolkę przycisku pokrętła w aplikacji, należy zastąpić wszystkie wystąpienia elementu `CSpinButtonCtrl` klasy `CMFCSpinButtonCtrl` klasy.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób tworzenia obiektu `CMFCSpinButtonCtrl` klasy i użyć jej `Create` metody.

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxspinbuttonctrl.h

##  <a name="ondraw"></a>  CMFCSpinButtonCtrl::OnDraw

Odświeża bieżący kontrolka przycisku pokrętła.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

Struktura wywołuje `CMFCSpinButtonCtrl::OnPaint` metody, aby obsłużyć [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) komunikat i że metoda z kolei wywołuje to `CMFCSpinButtonCtrl::OnDraw` metody. Zastępuje tę metodę, aby dostosować sposób, w ramach rysuje kontrolka przycisku pokrętła.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)
