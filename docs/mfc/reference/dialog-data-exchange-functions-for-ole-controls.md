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
ms.openlocfilehash: 5d330d8dd423927a3f4abbe6475a8d6219fa9af2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531251"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Funkcje wymiany danych w oknie dialogowym dla formantów OLE

W tym temacie wymieniono funkcje DDX_OC umożliwia wymianę danych między właściwości kontrolki OLE w okno dialogowe, widok formularza lub kontrolki widoku obiektu i element członkowski danych, okno dialogowe, widok formularza lub formantu obiekt widoku.

### <a name="ddxoc-functions"></a>Funkcje DDX_OC

|||
|-|-|
|[Ddx_ocbool —](#ddx_ocbool)|Zarządza transferem **BOOL** danych między właściwości kontrolki OLE i **BOOL** element członkowski danych.|
|[Ddx_ocboolro —](#ddx_ocboolro)|Zarządza transferem **BOOL** danych między tylko do odczytu właściwości kontrolki OLE i **BOOL** element członkowski danych.|
|[Ddx_occolor —](#ddx_occolor)|Zarządza transferem **OLE_COLOR** danych między właściwości kontrolki OLE i **OLE_COLOR** element członkowski danych.|
|[Ddx_occolorro —](#ddx_occolorro)|Zarządza transferem **OLE_COLOR** danych między tylko do odczytu właściwości kontrolki OLE i **OLE_COLOR** element członkowski danych.|
|[Ddx_ocfloat —](#ddx_ocfloat)|Zarządza transferem **float** (lub **double**) dane między właściwości kontrolki OLE i **float** (lub **double**) element członkowski danych.|
|[Ddx_ocfloatro —](#ddx_ocfloatro)|Zarządza transferem **float** (lub **double**) dane między tylko do odczytu właściwości kontrolki OLE i **float** (lub **double**) danych element członkowski.|
|[Ddx_ocint —](#ddx_ocint)|Zarządza transferem **int** (lub **długie**) dane między właściwości kontrolki OLE i **int** (lub **długie**) element członkowski danych.|
|[Ddx_ocintro —](#ddx_ocintro)|Zarządza transferem **int** (lub **długie**) dane między tylko do odczytu właściwości kontrolki OLE i **int** (lub **długie**) element członkowski danych.|
|[Ddx_ocshort —](#ddx_ocshort)|Zarządza transferem **krótki** danych między właściwości kontrolki OLE i **krótki** element członkowski danych.|
|[Ddx_ocshortro —](#ddx_ocshortro)|Zarządza transferem **krótki** danych między tylko do odczytu właściwości kontrolki OLE i **krótki** element członkowski danych.|
|[Ddx_octext —](#ddx_octext)|Zarządza transferem **CString** danych między właściwości kontrolki OLE i **CString** element członkowski danych.|
|[Ddx_octextro —](#ddx_octextro)|Zarządza transferem **CString** danych między tylko do odczytu właściwości kontrolki OLE i **CString** element członkowski danych.|

##  <a name="ddx_ocbool"></a>  Ddx_ocbool —

`DDX_OCBool` Funkcja zarządza transferem **BOOL** danych między właściwości kontrolki OLE w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i **BOOL** element członkowski danych okna dialogowego widok formularza lub Obiekt widoku formantu.

```
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki OLE w okno dialogowe, widok formularza lub formantu obiekt widoku.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu wyświetlić obiekt wymiany danych.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek:** afxdisp.h

##  <a name="ddx_ocboolro"></a>  Ddx_ocboolro —

`DDX_OCBoolRO` Funkcja zarządza transferem **BOOL** danych między tylko do odczytu właściwości kontrolki OLE w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i **BOOL** element członkowski danych okna dialogowego Widok formularza lub formantu obiekt widoku.

```
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki OLE w okno dialogowe, widok formularza lub formantu obiekt widoku.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu wyświetlić obiekt wymiany danych.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="ddx_occolor"></a>  Ddx_occolor —

`DDX_OCColor` Funkcja zarządza transferem danych OLE_COLOR między właściwości kontrolki OLE w oknie dialogowym, widok formularza lub kontrolki widoku obiektu i element członkowski danych OLE_COLOR okna dialogowego widok formularza lub kontrolować obiekt widoku.

```
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki OLE w okno dialogowe, widok formularza lub formantu obiekt widoku.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu wyświetlić obiekt wymiany danych.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="ddx_occolorro"></a>  Ddx_occolorro —

`DDX_OCColorRO` Funkcja zarządza transferem danych OLE_COLOR między tylko do odczytu właściwości kontrolki OLE w oknie dialogowym, widok formularza lub kontrolki widoku obiektu i element członkowski danych OLE_COLOR okna dialogowego widok formularza lub kontrolować obiekt widoku.

```
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki OLE w okno dialogowe, widok formularza lub formantu obiekt widoku.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu wyświetlić obiekt wymiany danych.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="ddx_ocfloat"></a>  Ddx_ocfloat —

`DDX_OCFloat` Funkcja zarządza transferem **float** (lub **double**) dane między właściwości kontrolki OLE w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i **float** (lub **double**) okno dialogowe, widok formularza lub formantu obiekt widoku element członkowski danych.

```
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

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki OLE w okno dialogowe, widok formularza lub formantu obiekt widoku.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu wyświetlić obiekt wymiany danych.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="ddx_ocfloatro"></a>  Ddx_ocfloatro —

`DDX_OCFloatRO` Funkcja zarządza transferem **float** (lub **double**) dane między tylko do odczytu właściwości kontrolki OLE w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i  **float** (lub **double**) okno dialogowe, widok formularza lub formantu obiekt widoku element członkowski danych.

```
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

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki OLE w okno dialogowe, widok formularza lub formantu obiekt widoku.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu wyświetlić obiekt wymiany danych.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="ddx_ocint"></a>  Ddx_ocint —

`DDX_OCInt` Funkcja zarządza transferem **int** (lub **długie**) dane między właściwości kontrolki OLE w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i **int**(lub **długie**) okno dialogowe, widok formularza lub formantu obiekt widoku element członkowski danych.

```
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

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki OLE w okno dialogowe, widok formularza lub formantu obiekt widoku.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu wyświetlić obiekt wymiany danych.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="ddx_ocintro"></a>  Ddx_ocintro —

`DDX_OCIntRO` Funkcja zarządza transferem **int** (lub **długie**) dane między tylko do odczytu właściwości kontrolki OLE w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i **int** (lub **długie**) okno dialogowe, widok formularza lub formantu obiekt widoku element członkowski danych.

```
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

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki OLE w okno dialogowe, widok formularza lub formantu obiekt widoku.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu wyświetlić obiekt wymiany danych.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="ddx_ocshort"></a>  Ddx_ocshort —

`DDX_OCShort` Funkcja zarządza transferem danych krótki między właściwości kontrolki OLE w oknie dialogowym, widok formularza lub kontrolki widoku obiektu i element członkowski danych krótki, okno dialogowe widok formularza lub kontrolować obiekt widoku.

```
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki OLE w okno dialogowe, widok formularza lub formantu obiekt widoku.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu wyświetlić obiekt wymiany danych.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="ddx_ocshortro"></a>  Ddx_ocshortro —

`DDX_OCShortRO` Funkcja zarządza transferem danych krótki między tylko do odczytu właściwości kontrolki OLE w oknie dialogowym, widok formularza lub kontrolki widoku obiektu i element członkowski danych krótki, okno dialogowe widok formularza lub kontrolować obiekt widoku.

```
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki OLE w okno dialogowe, widok formularza lub formantu obiekt widoku.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu wyświetlić obiekt wymiany danych.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="ddx_octext"></a>  Ddx_octext —

**Ddx_octext —** funkcja zarządza transferem **CString** danych między właściwości kontrolki OLE w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i **CString** danych element członkowski na to, że okno dialogowe, widok formularza lub formantu obiekt widoku.

```
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do **CDataExchange** obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki OLE w okno dialogowe, widok formularza lub formantu obiekt widoku.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu wyświetlić obiekt wymiany danych.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="ddx_octextro"></a>  Ddx_octextro —

`DDX_OCTextRO` Funkcja zarządza transferem `CString` danych między tylko do odczytu właściwości kontrolki OLE w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i `CString` element członkowski danych okno dialogowe, widok formularza lub formantu obiekt widoku.

```
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki OLE w okno dialogowe, widok formularza lub formantu obiekt widoku.

*identyfikator DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu wyświetlić obiekt wymiany danych.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
