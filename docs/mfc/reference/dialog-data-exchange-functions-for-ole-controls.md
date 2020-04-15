---
title: Funkcje wymiany danych w oknie dialogowym dla formantów OLE
ms.date: 11/04/2016
f1_keywords:
- AFXDISP/DDX_OCBool
- AFXDISP/DDX_OCBoolRO
- AFXDISP/DDX_OCColor
- AFXDISP/DDX_OCColorRO
- AFXDISP/DDX_OCFloat
- AFXDISP/DDX_OCFloatRO
- AFXDISP/DDX_OCInt
- AFXDISP/DDX_OCIntRO
- AFXDISP/DDX_OCShort
- AFXDISP/DDX_OCShortRO
- AFXDISP/DDX_OCText
- AFXDISP/DDX_OCTextRO
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
ms.openlocfilehash: 61a5983eec13902ed4b0e397e3befca4860977d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365767"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Funkcje wymiany danych w oknie dialogowym dla formantów OLE

W tym temacie wymieniono DDX_OC funkcji używanych do wymiany danych między właściwością formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem członkowskim danych w oknie dialogowym, widoku formularza lub obiekcie widoku sterującego.

### <a name="ddx_oc-functions"></a>funkcje DDX_OC

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|Zarządza transferem danych **BOOL** między właściwością formantu OLE a elementem członkowskim danych **BOOL.**|
|[DDX_OCBoolRO](#ddx_ocboolro)|Zarządza transferem danych **BOOL** między właściwością tylko do odczytu formantu OLE a elementem członkowskim danych **BOOL.**|
|[DDX_OCColor](#ddx_occolor)|Zarządza transferem **danych OLE_COLOR** między właściwością formantu OLE a **OLE_COLOR** element członkowski danych.|
|[DDX_OCColorRO](#ddx_occolorro)|Zarządza transferem **danych OLE_COLOR** między właściwością tylko do odczytu formantu OLE a **OLE_COLOR** element członkowski danych.|
|[DDX_OCFloat](#ddx_ocfloat)|Zarządza **transferem** danych float (lub **double)** między właściwością formantu OLE a elementem członkowskim danych **float** (lub **double).**|
|[DDX_OCFloatRO](#ddx_ocfloatro)|Zarządza **transferem** danych float (lub **double)** między właściwością tylko do odczytu formantu OLE a elementem członkowskim danych **float** (lub **double).**|
|[DDX_OCInt](#ddx_ocint)|Zarządza transferem danych **int** (lub **long)** między właściwością formantu OLE a elementem członkowskim danych **int** (lub **long).**|
|[DDX_OCIntRO](#ddx_ocintro)|Zarządza transferem danych **int** (lub **long)** między właściwością tylko do odczytu formantu OLE a elementem członkowskim danych **int** (lub **long).**|
|[DDX_OCShort](#ddx_ocshort)|Zarządza transferem **danych krótkich** między właściwością formantu OLE a **krótkim** elementem członkowskim danych.|
|[DDX_OCShortRO](#ddx_ocshortro)|Zarządza transferem **krótkich** danych między właściwością tylko do odczytu formantu OLE a **krótkim** elementem członkowskim danych.|
|[DDX_OCText](#ddx_octext)|Zarządza transferem danych **CString** między właściwością formantu OLE a elementem członkowskim danych **CString.**|
|[DDX_OCTextRO](#ddx_octextro)|Zarządza transferem danych **CString** między właściwością tylko do odczytu formantu OLE a elementem członkowskim danych **CString.**|

## <a name="ddx_ocbool"></a><a name="ddx_ocbool"></a>DDX_OCBool

Funkcja `DDX_OCBool` zarządza transferem danych **BOOL** między właściwością formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem członkowskim danych **BOOL** w oknie dialogowym, widoku formularza lub obiekcie widoku sterującego.

```cpp
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

*Dispid*<br/>
Identyfikator wysyłki właściwości formantu.

*value*<br/>
Odwołanie do zmiennej członkowskiej okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek:** afxdisp.h

## <a name="ddx_ocboolro"></a><a name="ddx_ocboolro"></a>DDX_OCBoolRO

Funkcja `DDX_OCBoolRO` zarządza transferem danych **BOOL** między właściwością tylko do odczytu formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem członkowskim danych **BOOL** w oknie dialogowym, widoku formularza lub obiekcie widoku sterującego.

```cpp
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

*Dispid*<br/>
Identyfikator wysyłki właściwości formantu.

*value*<br/>
Odwołanie do zmiennej członkowskiej okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="ddx_occolor"></a><a name="ddx_occolor"></a>DDX_OCColor

Funkcja `DDX_OCColor` zarządza transferem danych OLE_COLOR między właściwością formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a OLE_COLOR element członkowski danych w obiekcie okna dialogowego, widoku formularza lub widoku sterującego.

```cpp
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

*Dispid*<br/>
Identyfikator wysyłki właściwości formantu.

*value*<br/>
Odwołanie do zmiennej członkowskiej okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="ddx_occolorro"></a><a name="ddx_occolorro"></a>DDX_OCColorRO

Funkcja `DDX_OCColorRO` zarządza transferem OLE_COLOR danych między właściwością tylko do odczytu formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a OLE_COLOR element członkowski danych w oknie dialogowym, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

*Dispid*<br/>
Identyfikator wysyłki właściwości formantu.

*value*<br/>
Odwołanie do zmiennej członkowskiej okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="ddx_ocfloat"></a><a name="ddx_ocfloat"></a>DDX_OCFloat

Funkcja `DDX_OCFloat` zarządza transferem danych **float** (lub **double)** między właściwością formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem **zmiennoprzecinowym** (lub **podwójnym)** elementu członkowskiego danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

*Dispid*<br/>
Identyfikator wysyłki właściwości formantu.

*value*<br/>
Odwołanie do zmiennej członkowskiej okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="ddx_ocfloatro"></a><a name="ddx_ocfloatro"></a>DDX_OCFloatRO

Funkcja `DDX_OCFloatRO` zarządza **transferem** danych float (lub **double)** między właściwością tylko do odczytu formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem **zmiennoprzecinowym** (lub **podwójnym)** elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego.

```cpp
void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

*Dispid*<br/>
Identyfikator wysyłki właściwości formantu.

*value*<br/>
Odwołanie do zmiennej członkowskiej okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="ddx_ocint"></a><a name="ddx_ocint"></a>DDX_OCInt

Funkcja `DDX_OCInt` zarządza transferem danych **int** (lub **long)** między właściwością formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem członkowskim danych **int** (lub **długim)** w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

```cpp
void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

*Dispid*<br/>
Identyfikator wysyłki właściwości formantu.

*value*<br/>
Odwołanie do zmiennej członkowskiej okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="ddx_ocintro"></a><a name="ddx_ocintro"></a>DDX_OCIntRO

Funkcja `DDX_OCIntRO` zarządza transferem danych **int** (lub **long)** między właściwością tylko do odczytu formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem członkowskim danych **int** (lub **długim)** okna dialogowego, widoku formularza lub obiektu widoku sterującego.

```cpp
void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

*Dispid*<br/>
Identyfikator wysyłki właściwości formantu.

*value*<br/>
Odwołanie do zmiennej członkowskiej okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="ddx_ocshort"></a><a name="ddx_ocshort"></a>DDX_OCShort

Funkcja `DDX_OCShort` zarządza transferem krótkich danych między właściwością formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a krótkim elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku sterującego.

```cpp
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

*Dispid*<br/>
Identyfikator wysyłki właściwości formantu.

*value*<br/>
Odwołanie do zmiennej członkowskiej okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="ddx_ocshortro"></a><a name="ddx_ocshortro"></a>DDX_OCShortRO

Funkcja `DDX_OCShortRO` zarządza transferem krótkich danych między właściwością tylko do odczytu formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a krótkim elementem członkowskim danych w oknie dialogowym, widoku formularza lub obiekcie widoku sterującego.

```cpp
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

*Dispid*<br/>
Identyfikator wysyłki właściwości formantu.

*value*<br/>
Odwołanie do zmiennej członkowskiej okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="ddx_octext"></a><a name="ddx_octext"></a>DDX_OCText

Funkcja **DDX_OCText** zarządza transferem danych **CString** między właściwością formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem członkowskim danych **CString** w oknie dialogowym, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do **obiektu CDataExchange.** Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

*Dispid*<br/>
Identyfikator wysyłki właściwości formantu.

*value*<br/>
Odwołanie do zmiennej członkowskiej okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="ddx_octextro"></a><a name="ddx_octextro"></a>DDX_OCTextRO

Funkcja `DDX_OCTextRO` zarządza transferem `CString` danych między właściwością tylko do odczytu formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem `CString` członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku sterującego.

```cpp
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu OLE w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

*Dispid*<br/>
Identyfikator wysyłki właściwości formantu.

*value*<br/>
Odwołanie do zmiennej członkowskiej okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
