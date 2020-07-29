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
ms.openlocfilehash: b5a7263ae5cac81508ab2450a530132879ed45b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222826"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Funkcje wymiany danych w oknie dialogowym dla formantów OLE

W tym temacie wymieniono funkcje DDX_OC używane do wymiany danych między właściwością kontrolki OLE w oknie dialogowym, widoku Formularz lub obiektem widoku formantu oraz elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

### <a name="ddx_oc-functions"></a>Funkcje DDX_OC

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|Zarządza transferem danych **bool** między właściwością kontrolki OLE a elementem członkowskim danych **bool** .|
|[DDX_OCBoolRO](#ddx_ocboolro)|Zarządza transferem danych **bool** między właściwością tylko do odczytu formantu OLE a elementem członkowskim danych **bool** .|
|[DDX_OCColor](#ddx_occolor)|Zarządza transferem danych **OLE_COLOR** między właściwością kontrolki OLE i **OLE_COLOR** składową danych.|
|[DDX_OCColorRO](#ddx_occolorro)|Zarządza transferem danych **OLE_COLOR** między właściwością tylko do odczytu formantu OLE i **OLE_COLOR** składową danych.|
|[DDX_OCFloat](#ddx_ocfloat)|Zarządza transferem **`float`** (lub **`double`** ) danych między właściwością kontrolki OLE i **`float`** (lub **`double`** ) składową danych.|
|[DDX_OCFloatRO](#ddx_ocfloatro)|Zarządza transferem **`float`** (lub **`double`** ) danych między właściwością tylko do odczytu formantu OLE i **`float`** (lub **`double`** ) składową danych.|
|[DDX_OCInt](#ddx_ocint)|Zarządza transferem **`int`** (lub **`long`** ) danych między właściwością kontrolki OLE a **`int`** **`long`** elementem członkowskim danych (lub).|
|[DDX_OCIntRO](#ddx_ocintro)|Zarządza transferem **`int`** (lub **`long`** ) danych między właściwością tylko do odczytu formantu OLE i **`int`** (lub **`long`** ) składową danych.|
|[DDX_OCShort](#ddx_ocshort)|Zarządza przesyłaniem **`short`** danych między właściwością kontrolki OLE i **`short`** składową danych.|
|[DDX_OCShortRO](#ddx_ocshortro)|Zarządza przesyłaniem **`short`** danych między właściwością tylko do odczytu formantu OLE i **`short`** składową danych.|
|[DDX_OCText](#ddx_octext)|Zarządza transferem danych **CString** między właściwościami kontrolki OLE i elementu członkowskiego danych **CString** .|
|[DDX_OCTextRO](#ddx_octextro)|Zarządza transferem danych **CString** między właściwością tylko do odczytu formantu OLE i składową danych **CString** .|

## <a name="ddx_ocbool"></a><a name="ddx_ocbool"></a>DDX_OCBool

`DDX_OCBool`Funkcja zarządza transferem danych **bool** między właściwością kontrolki OLE w oknie dialogowym, widoku Formularz lub obiektem widoku formantu oraz elementem członkowskim danych **bool** okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki OLE w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu.

*DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku kontrolki, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek:** AFXDISP. h

## <a name="ddx_ocboolro"></a><a name="ddx_ocboolro"></a>DDX_OCBoolRO

`DDX_OCBoolRO`Funkcja zarządza transferem danych **bool** między właściwością tylko do odczytu kontrolki OLE w oknie dialogowym, widoku Formularz lub obiektem widoku formantu oraz elementem członkowskim danych **bool** okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki OLE w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu.

*DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku kontrolki, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="ddx_occolor"></a><a name="ddx_occolor"></a>DDX_OCColor

`DDX_OCColor`Funkcja zarządza transferem danych OLE_COLOR między właściwością kontrolki OLE w oknie dialogowym, widoku Formularz lub obiektem widoku kontrolki i OLE_COLOR członkiem danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki OLE w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu.

*DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku kontrolki, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="ddx_occolorro"></a><a name="ddx_occolorro"></a>DDX_OCColorRO

`DDX_OCColorRO`Funkcja zarządza transferem danych OLE_COLOR między właściwością tylko do odczytu kontrolki OLE w oknie dialogowym, widoku Formularz lub obiektem widoku kontrolki OLE_COLOR i elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki OLE w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu.

*DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku kontrolki, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="ddx_ocfloat"></a><a name="ddx_ocfloat"></a>DDX_OCFloat

`DDX_OCFloat`Funkcja zarządza transferem **`float`** (lub **`double`** ) danych między właściwością kontrolki OLE w oknie dialogowym, widoku Formularz lub obiektem widoku kontroli i **`float`** (lub **`double`** ) elementem członkowskim danych w oknie dialogowym, widoku formularza lub w obiekcie widoku formantu.

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

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki OLE w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu.

*DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku kontrolki, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="ddx_ocfloatro"></a><a name="ddx_ocfloatro"></a>DDX_OCFloatRO

`DDX_OCFloatRO`Funkcja zarządza transferem **`float`** (lub **`double`** ) danych między właściwością tylko do odczytu kontrolki OLE w oknie dialogowym, widoku Formularz lub obiektem widoku kontrolki i **`float`** (lub **`double`** ) elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

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

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki OLE w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu.

*DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku kontrolki, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="ddx_ocint"></a><a name="ddx_ocint"></a>DDX_OCInt

`DDX_OCInt`Funkcja zarządza transferem **`int`** (lub **`long`** ) danych między właściwością kontrolki OLE w oknie dialogowym, widoku Formularz lub obiektem widoku kontroli i **`int`** (lub **`long`** ) elementem członkowskim danych w oknie dialogowym, widoku formularza lub w obiekcie widoku formantu.

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

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki OLE w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu.

*DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku kontrolki, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="ddx_ocintro"></a><a name="ddx_ocintro"></a>DDX_OCIntRO

`DDX_OCIntRO`Funkcja zarządza transferem **`int`** (lub **`long`** ) danych między właściwością tylko do odczytu kontrolki OLE w oknie dialogowym, widoku Formularz lub obiektem widoku kontrolki i **`int`** (lub **`long`** ) elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

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

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki OLE w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu.

*DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku kontrolki, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="ddx_ocshort"></a><a name="ddx_ocshort"></a>DDX_OCShort

`DDX_OCShort`Funkcja zarządza transferem krótkich danych między właściwością kontrolki OLE w oknie dialogowym, widoku Formularz lub obiektem widoku kontroli i krótkim elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki OLE w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu.

*DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku kontrolki, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="ddx_ocshortro"></a><a name="ddx_ocshortro"></a>DDX_OCShortRO

`DDX_OCShortRO`Funkcja zarządza transferem krótkich danych między właściwością tylko do odczytu kontrolki OLE w oknie dialogowym, widoku Formularz lub obiektem widoku kontrolki i krótkim elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki OLE w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu.

*DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku kontrolki, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="ddx_octext"></a><a name="ddx_octext"></a>DDX_OCText

Funkcja **DDX_OCText** zarządza transferem danych **CString** między właściwością kontrolki OLE w oknie dialogowym, widoku Formularz lub obiektem widoku kontrolki **i elementem członkowskim danych w** oknie dialogowym, widoku formularza lub w obiekcie widoku formantu.

```cpp
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do obiektu **CDataExchange** . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki OLE w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu.

*DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku kontrolki, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="ddx_octextro"></a><a name="ddx_octextro"></a>DDX_OCTextRO

`DDX_OCTextRO`Funkcja zarządza transferem `CString` danych między właściwością tylko do odczytu formantu OLE w oknie dialogowym, widoku Formularz lub obiektem widoku kontrolki i `CString` elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki OLE w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu.

*DISPID*<br/>
Identyfikator wysyłania właściwości formantu.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku kontrolki, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="see-also"></a>Zobacz także

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
