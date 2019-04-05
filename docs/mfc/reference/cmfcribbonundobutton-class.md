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
ms.openlocfilehash: cd657ac035c004e7aa9bfcd2f6dbd2f3c90da80c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776469"
---
# <a name="cmfcribbonundobutton-class"></a>Klasa CMFCRibbonUndoButton

`CMFCRibbonUndoButton` Klasa implementuje przycisk listy rozwijanej, który zawiera najnowsze polecenia użytkownika. Użytkownicy mogą wybrać co najmniej jednym z najbardziej aktualną poleceń, z listy rozwijanej, aby cofnąć lub ponowić.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Tworzy nowy `CMFCRibbonUndoButton` obiektu za pomocą Identyfikatora polecenia, który określisz, etykiety tekstu i obrazów z listy obrazów obiektu nadrzędnego.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Dodaje nową akcję do listy akcji.|
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Czyści listę akcji, która jest listy rozwijanej.|
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Określa liczbę elementów, które użytkownik wybrane z listy rozwijanej.|
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Wskazuje, czy obiekt zawiera menu.|

## <a name="remarks"></a>Uwagi

`CMFCRibbonUndoButton` Klasa używa stosu, który reprezentuje listy rozwijanej.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCRibbonUndoButton` klasy, a następnie dodaj nową akcję do listy akcji. Ten fragment kodu jest częścią [przykładowe gadżetów wstążki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribbonundobutton.h

##  <a name="addundoaction"></a>  CMFCRibbonUndoButton::AddUndoAction

Dodaje nową akcję do listy akcji.

```
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Etykieta akcji, która będzie wyświetlana na liście rozwijanej.

##  <a name="cleanupundolist"></a>  CMFCRibbonUndoButton::CleanUpUndoList

Czyści listę akcji, która jest listy rozwijanej.

```
void CleanUpUndoList();
```

##  <a name="cmfcribbonundobutton"></a>  CMFCRibbonUndoButton::CMFCRibbonUndoButton

Tworzy nowy `CMFCRibbonUndoButton` obiektu za pomocą Identyfikatora polecenia, który określisz, etykiety tekstu i obrazów z listy obrazów obiektu nadrzędnego.

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

*nID*<br/>
[in] Określa identyfikator polecenia.

*lpszText*<br/>
[in] Określa tekst etykiety przycisku.

*nSmallImageIndex*<br/>
[in] Liczony od zera indeks z listy obrazów obiektu nadrzędnego, która ma być mały obraz przycisku.

*nLargeImageIndex*<br/>
[in] Liczony od zera indeks, z listy obrazów obiektu nadrzędnego dla dużych obrazu przycisku.

*hIcon*<br/>
[in] Dojście do ikonę która służy jako obrazu przycisku.

##  <a name="getactionnumber"></a>  CMFCRibbonUndoButton::GetActionNumber

Określa liczbę elementów, które użytkownik wybrane z listy rozwijanej.

```
int GetActionNumber() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które wybrane przez użytkownika.

##  <a name="hasmenu"></a>  CMFCRibbonUndoButton::HasMenu

Wskazuje, czy obiekt zawiera menu.

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Diagram hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)
