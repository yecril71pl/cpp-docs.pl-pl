---
title: Klasa CMFCRibbonProgressBar
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
ms.openlocfilehash: 063f8ce560af84d350abc0114644f6a63f969f95
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368860"
---
# <a name="cmfcribbonprogressbar-class"></a>Klasa CMFCRibbonProgressBar

Implementuje formant, który wizualnie wskazuje postęp operacji długotrwałej.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|Konstruuje i inicjuje `CMFCRibbonProgressBar` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonProgressBar::GetPos](#getpos)|Zwraca bieżący postęp.|
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|Zwraca maksymalną wartość bieżącego zakresu.|
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|Zwraca minimalną wartość bieżącego zakresu.|
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|Zwraca regularny rozmiar elementu wstążki. (Zastępuje [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Określa, czy pasek postępu działa w trybie nieskończonym.|
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|Wywoływana przez strukturę do rysowania elementu wstążki. (Zastępuje [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Ustawia pasek postępu do pracy w trybie nieskończonym.|
|[CMFCRibbonProgressBar::SetPos](#setpos)|Ustawia bieżący postęp.|
|[CMFCRibbonProgressBar::SetRange](#setrange)|Ustawia wartości minimalne i maksymalne.|

## <a name="remarks"></a>Uwagi

A `CMFCRibbonProgressBar` może działać w dwóch trybach: zwykłym i nieskończonym. W trybie regularnym pasek postępu jest wypełniany od lewej do prawej i zatrzymuje się po osiągnięciu maksymalnej wartości. W trybie nieskończonym pasek postępu jest wielokrotnie wypełniany od wartości minimalnej do wartości maksymalnej. Tryb nieskończony można użyć, aby wskazać, że operacja jest w toku, ale czas ukończenia jest nieznany.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCRibbonProgressBar` używać różnych metod w klasie. W przykładzie pokazano, jak ustawić pasek postępu do pracy w trybie nieskończonym (gdzie czas zakończenia operacji jest nieznany), ustawić minimalne i maksymalne wartości dla paska postępu i ustawić bieżącą pozycję paska postępu. Ten fragment kodu jest częścią [przykładu demo pakietu MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonProgressBar.h

## <a name="cmfcribbonprogressbarcmfcribbonprogressbar"></a><a name="cmfcribbonprogressbar"></a>CMFCRibbonProgressBar::CMFCRibbonProgressBar

Konstruuje i inicjuje [OBIEKT CMFCRibbonProgressBar.](../../mfc/reference/cmfcribbonprogressbar-class.md)

```
CMFCRibbonProgressBar();

CMFCRibbonProgressBar(
    UINT nID,
    int nWidth = 90,
    int nHeight = 22);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[w] Określa identyfikator polecenia paska postępu wstążki.

*nWidth (ww.*<br/>
[w] Określa szerokość paska postępu wstążki w pikselach.

*nFeksja*<br/>
[w] Określa wysokość paska postępu wstążki w pikselach.

## <a name="cmfcribbonprogressbargetpos"></a><a name="getpos"></a>CMFCRibbonProgressBar::GetPos

Zwraca bieżącą pozycję paska postępu.

```
int GetPos () const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość reprezentująca bieżącą pozycję paska postępu.

### <a name="remarks"></a>Uwagi

Zakres, który jest ustawiony musi znajdować się w zakresie określonym przez [CMFCRibbonProgressBar::SetRange](#setrange) metody.

## <a name="cmfcribbonprogressbargetrangemax"></a><a name="getrangemax"></a>CMFCRibbonProgressBar::GetRangeMax

Zwraca bieżącą wartość maksymalną paska postępu.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna wartość bieżącego zakresu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonprogressbargetrangemin"></a><a name="getrangemin"></a>CMFCRibbonProgressBar::GetRangeMin

Zwraca bieżącą wartość minimalnego zakresu paska postępu.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Wartość zwracana

Minimalna wartość bieżącego zakresu.

## <a name="cmfcribbonprogressbargetregularsize"></a><a name="getregularsize"></a>CMFCRibbonProgressBar::GetRegularSize

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[w] *pDC*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonprogressbarisinfinitemode"></a><a name="isinfinitemode"></a>CMFCRibbonProgressBar::IsInfiniteMode

Określa, czy pasek postępu działa w trybie nieskończonym.

```
BOOL IsInfiniteMode() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli pasek postępu jest w trybie nieskończonym; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

W trybie nieskończonym pasek postępu wypełnia się wielokrotnie od wartości minimalnej do wartości maksymalnej. Tryb nieskończony można użyć, aby wskazać, że operacja jest w toku, ale czas ukończenia jest nieznany.

## <a name="cmfcribbonprogressbarondraw"></a><a name="ondraw"></a>CMFCRibbonProgressBar::OnDraw

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[w] *pDC*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonprogressbarsetinfinitemode"></a><a name="setinfinitemode"></a>CMFCRibbonProgressBar::SetInfiniteMode

Ustawia pasek postępu do pracy w trybie nieskończonym.

```
void SetInfiniteMode(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

*bStaw*<br/>
[w] PRAWDA, aby określić, że pasek postępu jest w trybie nieskończonym; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Zazwyczaj, jeśli pasek postępu jest w trybie nieskończonym, informuje użytkownika, że operacja jest w toku, ale czas ukończenia jest nieznany. W związku z tym pasek postępu wypełnia wielokrotnie od wartości minimalnej do wartości maksymalnej.

## <a name="cmfcribbonprogressbarsetpos"></a><a name="setpos"></a>CMFCRibbonProgressBar::SetPos

Ustawia bieżącą pozycję paska postępu.

```
void SetPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
[w] Określa położenie, na które ustawiony jest pasek postępu.

*bRedraw*<br/>
[w] Określa, czy pasek postępu ma zostać ponownie narysowany.

### <a name="remarks"></a>Uwagi

Zakres, który jest ustawiony musi znajdować się w zakresie określonym przez [CMFCRibbonProgressBar::SetRange](#setrange) metody.

## <a name="cmfcribbonprogressbarsetrange"></a><a name="setrange"></a>CMFCRibbonProgressBar::SetRange

Ustawia minimalne i maksymalne wartości dla paska postępu.

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin (min.*<br/>
[w] Określa minimalną wartość zakresu.

*Nmax*<br/>
[w] Określa maksymalną wartość zakresu.

### <a name="remarks"></a>Uwagi

Ta metoda służy do definiowania zakresu paska postępu przez ustawienie wartości minimalnych i maksymalnych.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
