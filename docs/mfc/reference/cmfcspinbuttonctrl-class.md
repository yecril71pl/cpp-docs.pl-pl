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
ms.openlocfilehash: 445b857400d8c82109ca7220b84bac692a2abf89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376173"
---
# <a name="cmfcspinbuttonctrl-class"></a>Klasa CMFCSpinButtonCtrl

Klasa `CMFCSpinButtonCtrl` obsługuje menedżera wizualnego, który rysuje formant przycisku pokrętła.

## <a name="syntax"></a>Składnia

```
class CMFCSpinButtonCtrl : public CSpinButtonCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|Domyślny konstruktor.|
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|Odświeża bieżącą kontrolę przycisku pokrętła.|

## <a name="remarks"></a>Uwagi

Aby użyć menedżera wizualnego, aby narysować formant przycisku `CSpinButtonCtrl` pokrętła `CMFCSpinButtonCtrl` w aplikacji, zastąp wszystkie wystąpienia klasy klasą.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCSpinButtonCtrl` utworzyć obiekt `Create` klasy i użyć jej metody.

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl (Polski)](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxspinbuttonctrl.h

## <a name="cmfcspinbuttonctrlondraw"></a><a name="ondraw"></a>CMFCSpinButtonCtrl::OnDraw

Odświeża bieżącą kontrolę przycisku pokrętła.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

Struktura wywołuje `CMFCSpinButtonCtrl::OnPaint` metodę do obsługi [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) wiadomości i tej `CMFCSpinButtonCtrl::OnDraw` metody z kolei wywołuje tę metodę. Zastąp tę metodę, aby dostosować sposób, w jaki struktura rysuje formant przycisku pokrętła.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)
