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
ms.openlocfilehash: 5386240114550826e4bf557b63310a91590afb55
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284219"
---
# <a name="cpictureholder-class"></a>Klasa CPictureHolder

Implementuje właściwość obrazu, który umożliwia użytkownikowi wyświetlanie obrazu w kontrolce.

## <a name="syntax"></a>Składnia

```
class CPictureHolder
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPictureHolder::CPictureHolder](#cpictureholder)|Konstruuje `CPictureHolder` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPictureHolder::CreateEmpty](#createempty)|Tworzy pustą `CPictureHolder` obiektu.|
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|Tworzy `CPictureHolder` obiektu z mapy bitowej.|
|[CPictureHolder::CreateFromIcon](#createfromicon)|Tworzy `CPictureHolder` obiektu z ikony.|
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|Tworzy `CPictureHolder` obiekt z metaplik.|
|[CPictureHolder::GetDisplayString](#getdisplaystring)|Pobiera ciąg wyświetlany w przeglądarce właściwości kontenera kontrolki.|
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|Zwraca `CPictureHolder` obiektu `IDispatch` interfejsu.|
|[CPictureHolder::GetType](#gettype)|Informuje, czy `CPictureHolder` obiekt jest mapy bitowej, metaplik lub ikony.|
|[CPictureHolder::Render](#render)|Renderuje obraz.|
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|Zestawy `CPictureHolder` obiektu `IDispatch` interfejsu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPictureHolder::m_pPict](#m_ppict)|Wskaźnik do obiektu obrazu.|

## <a name="remarks"></a>Uwagi

`CPictureHolder` nie ma klasy bazowej.

Za pomocą właściwości podstawowych obrazu Deweloper można określić mapy bitowej, ikona lub metaplik do wyświetlenia.

Informacje na temat tworzenia właściwości niestandardowego obrazu, zobacz artykuł [kontrolki ActiveX MFC: Używanie obrazów w kontrolce ActiveX](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CPictureHolder`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

##  <a name="cpictureholder"></a>  CPictureHolder::CPictureHolder

Konstruuje `CPictureHolder` obiektu.

```
CPictureHolder();
```

##  <a name="createempty"></a>  CPictureHolder::CreateEmpty

Tworzy pustą `CPictureHolder` obiektu i łączy ją do `IPicture` interfejsu.

```
BOOL CreateEmpty();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obiekt jest pomyślnie utworzony; w przeciwnym razie 0.

##  <a name="createfrombitmap"></a>  CPictureHolder::CreateFromBitmap

Używa mapę bitową do inicjalizacji obiektu obrazu w `CPictureHolder`.

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

*idResource*<br/>
Identyfikator zasobu, zasób mapy bitowej.

*pBitmap*<br/>
Wskaźnik do [CBitmap](../../mfc/reference/cbitmap-class.md) obiektu.

*pPal*<br/>
Wskaźnik do [CPalette](../../mfc/reference/cpalette-class.md) obiektu.

*bTransferOwnership*<br/>
Wskazuje, czy obiektu obrazu będzie przejęcie na własność obiektów mapy bitowej i palety.

*hbm*<br/>
Dojście do mapy bitowej, z którego `CPictureHolder` obiekt zostanie utworzony.

*hpal*<br/>
Dojście do palety, używany do renderowania mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obiekt jest pomyślnie utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *bTransferOwnership* ma wartość TRUE, obiekt wywołujący nie należy używać mapy bitowej lub zwraca obiekt palety w jakikolwiek sposób po tym wywołaniu. Jeśli *bTransferOwnership* ma wartość FAŁSZ, obiekt wywołujący jest odpowiedzialny za zapewnienie, że obiekty mapy bitowej i palety pozostają w mocy okresu istnienia obiektu obrazu.

##  <a name="createfromicon"></a>  CPictureHolder::CreateFromIcon

Używa ikony można zainicjować obiektu obrazu w `CPictureHolder`.

```
BOOL CreateFromIcon(
    UINT idResource);

BOOL CreateFromIcon(
    HICON hIcon,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parametry

*idResource*<br/>
Identyfikator zasobu, zasób mapy bitowej.

*hIcon*<br/>
Dojście do ikony, z którego `CPictureHolder` obiekt zostanie utworzony.

*bTransferOwnership*<br/>
Wskazuje, czy obiektu obrazu będzie przejęcie na własność obiektu ikony.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obiekt jest pomyślnie utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *bTransferOwnership* ma wartość TRUE, obiekt wywołujący nie należy używać obiekt ikony w jakikolwiek sposób po powrocie tego wywołania. Jeśli *bTransferOwnership* ma wartość FAŁSZ, obiekt wywołujący jest odpowiedzialny za zapewnienie obiekt ikony pozostaje ważny przez okres istnienia obiektu obrazu.

##  <a name="createfrommetafile"></a>  CPictureHolder::CreateFromMetafile

Używa metaplik można zainicjować obiektu obrazu w `CPictureHolder`.

```
BOOL CreateFromMetafile(
    HMETAFILE hmf,
    int xExt,
    int yExt,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parametry

*hmf*<br/>
Dojście do metaplik użyty do utworzenia `CPictureHolder` obiektu.

*xExt*<br/>
X zakres obrazu.

*yExt*<br/>
Zakres Y obrazu.

*bTransferOwnership*<br/>
Wskazuje, czy obiekt obraz będzie przejęcie na własność obiektu metaplik.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obiekt jest pomyślnie utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *bTransferOwnership* ma wartość TRUE, obiekt wywołujący nie należy używać obiektu metaplik w jakikolwiek sposób po powrocie tego wywołania. Jeśli *bTransferOwnership* ma wartość FAŁSZ, obiekt wywołujący jest odpowiedzialny za zapewnienie obiektu metaplik pozostaje ważny przez okres istnienia obiektu obrazu.

##  <a name="getdisplaystring"></a>  CPictureHolder::GetDisplayString

Pobiera ciąg, który jest wyświetlany w przeglądarce właściwości kontenera.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parametry

*strValue*<br/>
Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) jest do przechowywania ciągu wyświetlanego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli ciąg jest pomyślnie pobrane; w przeciwnym razie 0.

##  <a name="getpicturedispatch"></a>  CPictureHolder::GetPictureDispatch

Ta funkcja zwraca wskaźnik do `CPictureHolder` obiektu `IPictureDisp` interfejsu.

```
LPPICTUREDISP GetPictureDispatch();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CPictureHolder` obiektu `IPictureDisp` interfejsu.

### <a name="remarks"></a>Uwagi

Obiekt wywołujący musi wywołać `Release` na ten wskaźnik, po zakończeniu pracy z nim.

##  <a name="gettype"></a>  CPictureHolder::GetType

Wskazuje, czy obraz jest mapa bitowa, metaplik lub ikonę.

```
short GetType();
```

### <a name="return-value"></a>Wartość zwracana

Wartość wskazująca, typ obrazu. Możliwe wartości i ich znaczenie są następujące:

|Wartość|Znaczenie|
|-----------|-------------|
|PICTYPE_UNINITIALIZED|`CPictureHolder` obiekt jest unititialized.|
|PICTYPE_NONE|`CPictureHolder` obiekt jest pusty.|
|PICTYPE_BITMAP|Obraz jest mapą bitową.|
|PICTYPE_METAFILE|Obraz jest metaplik.|
|PICTYPE_ICON|Obraz jest wyświetlana jako ikona.|

##  <a name="m_ppict"></a>  CPictureHolder::m_pPict

Wskaźnik do `CPictureHolder` obiektu `IPicture` interfejsu.

```
LPPICTURE m_pPict;
```

##  <a name="render"></a>  CPictureHolder::Render

Renderuje obraz w prostokącie odwołuje się *rcRender*.

```
void Render(
    CDC* pDC,
    const CRect& rcRender,
    const CRect& rcWBounds);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do kontekstu wyświetlania, w którym obraz ma być renderowany.

*rcRender*<br/>
Prostokąt, w którym obraz ma być renderowany.

*rcWBounds*<br/>
Prostokąt reprezentujący prostokąt otaczający obiektu renderowania obrazu. Kontrolki, jest to prostokąt *rcBounds* parametr przekazany do zastępowania metody [COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw).

##  <a name="setpicturedispatch"></a>  CPictureHolder::SetPictureDispatch

Łączy `CPictureHolder` obiekt `IPictureDisp` interfejsu.

```
void SetPictureDispatch(LPPICTUREDISP pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Wskaźnik do nowego `IPictureDisp` interfejsu.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFontHolder](../../mfc/reference/cfontholder-class.md)
