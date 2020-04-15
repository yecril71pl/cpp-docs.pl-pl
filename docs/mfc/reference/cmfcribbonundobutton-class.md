---
title: Klasa CMFCRibbonUndoButton
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
ms.openlocfilehash: f30e6f78b0988b791617ee0926cf649377972ce2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368814"
---
# <a name="cmfcribbonundobutton-class"></a>Klasa CMFCRibbonUndoButton

Klasa `CMFCRibbonUndoButton` implementuje przycisk listy rozwijanej, który zawiera najnowsze polecenia użytkownika. Użytkownicy mogą wybrać jedno lub więcej najnowszych poleceń z listy rozwijanej, aby ponażyć lub cofnąć.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Konstruuje `CMFCRibbonUndoButton` nowy obiekt przy użyciu określanego identyfikatora polecenia, etykiety tekstowej i obrazów z listy obrazów obiektu nadrzędnego.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Dodaje nową akcję do listy akcji.|
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Czyści listę akcji, która jest listą rozwijaną.|
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Określa liczbę elementów wybranych przez użytkownika z listy rozwijanej.|
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Wskazuje, czy obiekt zawiera menu.|

## <a name="remarks"></a>Uwagi

Klasa `CMFCRibbonUndoButton` używa stosu do reprezentowania listy rozwijanej.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCRibbonUndoButton` skonstruować obiekt klasy i dodać nową akcję do listy akcji. Ten fragment kodu jest częścią [przykładu Gadżety wstążki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGaleria](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribbonundobutton.h

## <a name="cmfcribbonundobuttonaddundoaction"></a><a name="addundoaction"></a>CMFCRibbonUndoButton::AddUndoAction

Dodaje nową akcję do listy akcji.

```
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Etykieta akcji, która będzie wyświetlana na liście rozwijanej.

## <a name="cmfcribbonundobuttoncleanupundolist"></a><a name="cleanupundolist"></a>CMFCRibbonUndoButton::CleanUpUndoList

Czyści listę akcji, która jest listą rozwijaną.

```
void CleanUpUndoList();
```

## <a name="cmfcribbonundobuttoncmfcribbonundobutton"></a><a name="cmfcribbonundobutton"></a>CMFCRibbonUndoButton::CMFCRibbonUndoButton

Konstruuje `CMFCRibbonUndoButton` nowy obiekt przy użyciu określanego identyfikatora polecenia, etykiety tekstowej i obrazów z listy obrazów obiektu nadrzędnego.

```
CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex=-1,
    int nLargeImageIndex=-1);

CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    HICON hIcon);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[w] Określa identyfikator polecenia.

*lpszText (tekst)*<br/>
[w] Określa etykietę tekstową przycisku.

*nSmallImageIndex*<br/>
[w] Indeks oparty na wartości zerowej na liście obrazów obiektu nadrzędnego dla małego obrazu przycisku.

*nLargeImageIndex*<br/>
[w] Indeks oparty na wartości zerowej na liście obrazów obiektu nadrzędnego dla dużego obrazu przycisku.

*hIcon (własówce)*<br/>
[w] Uchwyt do ikony, której można użyć jako obrazu przycisku.

## <a name="cmfcribbonundobuttongetactionnumber"></a><a name="getactionnumber"></a>CMFCRibbonUndoButton::GetActionNumber

Określa liczbę elementów wybranych przez użytkownika z listy rozwijanej.

```
int GetActionNumber() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów wybranych przez użytkownika.

## <a name="cmfcribbonundobuttonhasmenu"></a><a name="hasmenu"></a>CMFCRibbonUndoButton::HasMenu

Wskazuje, czy obiekt zawiera menu.

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)
