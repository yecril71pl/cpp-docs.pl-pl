---
title: Klasa CMFCSpinButtonCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
dev_langs:
- C++
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 756cdffc8f9f726e63b129f5f87a19eec01cd429
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440020"
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

*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

Struktura wywołuje `CMFCSpinButtonCtrl::OnPaint` metody, aby obsłużyć [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) komunikat i że metoda z kolei wywołuje to `CMFCSpinButtonCtrl::OnDraw` metody. Zastępuje tę metodę, aby dostosować sposób, w ramach rysuje kontrolka przycisku pokrętła.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)
