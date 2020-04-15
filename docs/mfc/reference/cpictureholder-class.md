---
title: Klasa CPictureHolder
ms.date: 11/04/2016
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
ms.openlocfilehash: 067ea7238c48f2698d7bfe469e9c4be10129c065
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364054"
---
# <a name="cpictureholder-class"></a>Klasa CPictureHolder

Implementuje Picture właściwości, która umożliwia użytkownikowi wyświetlanie obrazu w formancie.

## <a name="syntax"></a>Składnia

```
class CPictureHolder
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPictureHolder::CPictureHolder](#cpictureholder)|Konstruuje `CPictureHolder` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPictureHolder::CreateEmpty](#createempty)|Tworzy pusty `CPictureHolder` obiekt.|
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|Tworzy `CPictureHolder` obiekt z mapy bitowej.|
|[CPictureHolder::CreateFromIcon](#createfromicon)|Tworzy `CPictureHolder` obiekt na podstawie ikony.|
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|Tworzy `CPictureHolder` obiekt z metapliku.|
|[CPictureHolder::GetDisplayString](#getdisplaystring)|Pobiera ciąg wyświetlany w przeglądarce właściwości kontenera formantu.|
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|Zwraca `CPictureHolder` `IDispatch` interfejs obiektu.|
|[CPictureHolder::GetType](#gettype)|Określa, `CPictureHolder` czy obiekt jest bitmapą, metaplikem czy ikoną.|
|[CPictureHolder::Render](#render)|Renderuje obraz.|
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|Ustawia `CPictureHolder` `IDispatch` interfejs obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPictureHolder::m_pPict](#m_ppict)|Wskaźnik do obiektu obrazu.|

## <a name="remarks"></a>Uwagi

`CPictureHolder`nie ma klasy podstawowej.

Za pomocą właściwości Zdjęcie stock deweloper może określić mapę bitową, ikonę lub metaplik do wyświetlania.

Aby uzyskać informacje na temat tworzenia niestandardowych właściwości obrazu, zobacz artykuł [MFC ActiveX Controls: Using Pictures in an ActiveX Control](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CPictureHolder`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="cpictureholdercpictureholder"></a><a name="cpictureholder"></a>CPictureHolder::CPictureHolder

Konstruuje `CPictureHolder` obiekt.

```
CPictureHolder();
```

## <a name="cpictureholdercreateempty"></a><a name="createempty"></a>CPictureHolder::CreateEmpty

Tworzy pusty `CPictureHolder` obiekt i łączy `IPicture` go z interfejsem.

```
BOOL CreateEmpty();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie 0.

## <a name="cpictureholdercreatefrombitmap"></a><a name="createfrombitmap"></a>CPictureHolder::CreateFromBitmap

Używa mapy bitowej do zainicjowania obiektu `CPictureHolder`obrazu w pliku .

```
BOOL CreateFromBitmap(
    UINT idResource);

BOOL CreateFromBitmap(
    CBitmap* pBitmap,
    CPalette* pPal = NULL,
    BOOL bTransferOwnership = TRUE);

BOOL CreateFromBitmap(
    HBITMAP hbm,
    HPALETTE hpal = NULL,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parametry

*idSerwród*<br/>
Identyfikator zasobu mapy bitowej.

*pBitmapa*<br/>
Wskaźnik do obiektu [CBitmap.](../../mfc/reference/cbitmap-class.md)

*pPal (pPal)*<br/>
Wskaźnik do obiektu [CPalette.](../../mfc/reference/cpalette-class.md)

*Btransferownership*<br/>
Wskazuje, czy obiekt obrazu przejmie na własność obiekty mapy bitowej i palety.

*Hbm*<br/>
Dojście do mapy `CPictureHolder` bitowej, z której tworzony jest obiekt.

*hpal*<br/>
Uchwyt do palety używanej do renderowania mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *bTransferOwnership* jest TRUE, obiekt wywołujący nie należy używać bitmapy lub obiektu palety w jakikolwiek sposób po tym wywołaniu zwraca. Jeśli *bTransferOwnership* jest FALSE, obiekt wywołujący jest odpowiedzialny za zapewnienie, że bitmapy i palety obiekty pozostają prawidłowe przez cały okres istnienia obiektu obrazu.

## <a name="cpictureholdercreatefromicon"></a><a name="createfromicon"></a>CPictureHolder::CreateFromIcon

Używa ikony do zainicjowania obiektu `CPictureHolder`obrazu w pliku .

```
BOOL CreateFromIcon(
    UINT idResource);

BOOL CreateFromIcon(
    HICON hIcon,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parametry

*idSerwród*<br/>
Identyfikator zasobu mapy bitowej.

*hIcon (własówce)*<br/>
Dojście do ikony, `CPictureHolder` z której tworzony jest obiekt.

*Btransferownership*<br/>
Wskazuje, czy obiekt obrazu przejmie na własność obiekt ikony.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *bTransferOwnership* jest TRUE, obiekt wywołujący nie należy używać obiektu ikony w jakikolwiek sposób po tym wywołaniu zwraca. Jeśli *bTransferOwnership* jest FALSE, obiekt wywołujący jest odpowiedzialny za zapewnienie, że obiekt ikony pozostaje prawidłowy przez cały okres istnienia obiektu obrazu.

## <a name="cpictureholdercreatefrommetafile"></a><a name="createfrommetafile"></a>CPictureHolder::CreateFromMetafile

Używa metapliku do zainicjowania obiektu `CPictureHolder`obrazu w pliku .

```
BOOL CreateFromMetafile(
    HMETAFILE hmf,
    int xExt,
    int yExt,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parametry

*Hmf*<br/>
Uchwyt do metapliku używanego `CPictureHolder` do tworzenia obiektu.

*xExt*<br/>
X zakres obrazu.

*yExt (yExt)*<br/>
Y zakres obrazu.

*Btransferownership*<br/>
Wskazuje, czy obiekt obrazu przejmie na własność obiekt metaplik.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *bTransferOwnership* jest TRUE, obiekt wywołujący nie należy używać metafile obiektu w jakikolwiek sposób po tym wywołaniu zwraca. Jeśli *bTransferOwnership* jest FALSE, obiekt wywołujący jest odpowiedzialny za zapewnienie, że obiekt metapliku pozostaje prawidłowy przez cały okres istnienia obiektu obrazu.

## <a name="cpictureholdergetdisplaystring"></a><a name="getdisplaystring"></a>CPictureHolder::GetDisplayString

Pobiera ciąg, który jest wyświetlany w przeglądarce właściwości kontenera.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parametry

*strValue (wartość)*<br/>
Odwołanie do [CString,](../../atl-mfc-shared/reference/cstringt-class.md) który ma pomieścić ciąg wyświetlania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli ciąg zostanie pomyślnie pobrany; w przeciwnym razie 0.

## <a name="cpictureholdergetpicturedispatch"></a><a name="getpicturedispatch"></a>CPictureHolder::GetPictureDispatch

Ta funkcja zwraca wskaźnik `CPictureHolder` do `IPictureDisp` interfejsu obiektu.

```
LPPICTUREDISP GetPictureDispatch();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CPictureHolder` `IPictureDisp` interfejsu obiektu.

### <a name="remarks"></a>Uwagi

Wywołujący musi `Release` wywołać ten wskaźnik po zakończeniu z nim.

## <a name="cpictureholdergettype"></a><a name="gettype"></a>CPictureHolder::GetType

Wskazuje, czy obraz jest bitmapą, metaplikiem czy ikoną.

```
short GetType();
```

### <a name="return-value"></a>Wartość zwracana

Wartość wskazująca typ obrazu. Możliwe wartości i ich znaczenie są następujące:

|Wartość|Znaczenie|
|-----------|-------------|
|PICTYPE_UNINITIALIZED|`CPictureHolder`obiekt jest unitiiisialized.|
|PICTYPE_NONE|`CPictureHolder`obiekt jest pusty.|
|PICTYPE_BITMAP|Obraz jest bitmapą.|
|PICTYPE_METAFILE|Obraz jest metaplik.|
|PICTYPE_ICON|Obraz jest ikoną.|

## <a name="cpictureholderm_ppict"></a><a name="m_ppict"></a>CPictureHolder::m_pPict

Wskaźnik do `CPictureHolder` `IPicture` interfejsu obiektu.

```
LPPICTURE m_pPict;
```

## <a name="cpictureholderrender"></a><a name="render"></a>CPictureHolder::Render

Renderuje obraz w prostokącie, do którego odwołuje się *rcRender*.

```
void Render(
    CDC* pDC,
    const CRect& rcRender,
    const CRect& rcWBounds);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu wyświetlania, w którym obraz ma być renderowany.

*rcRender ( rcRender )*<br/>
Prostokąt, w którym obraz ma być renderowany.

*połączenia z rcWBounds*<br/>
Prostokąt reprezentujący prostokąt ograniczający obiektu renderującego obraz. Dla formantu ten prostokąt jest *rcBounds* parametr przekazany do zastąpienia [COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw).

## <a name="cpictureholdersetpicturedispatch"></a><a name="setpicturedispatch"></a>CPictureHolder::SetPictureDispatch

Łączy obiekt `CPictureHolder` z `IPictureDisp` interfejsem.

```
void SetPictureDispatch(LPPICTUREDISP pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp (Niem.*<br/>
Wskaźnik do `IPictureDisp` nowego interfejsu.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFontHolder](../../mfc/reference/cfontholder-class.md)
