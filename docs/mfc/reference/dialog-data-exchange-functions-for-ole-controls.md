---
title: Funkcje wymiany danych w oknie dialogowym dla formantów OLE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 542afe8ba67e1d9c6138998320483a964a08724a
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121828"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Funkcje wymiany danych w oknie dialogowym dla formantów OLE
W tym temacie wymieniono funkcje DDX_OC używanego do wymiany danych między właściwości formantu OLE w okno dialogowe, widoku formularza lub kontrolki widoku obiektu i element członkowski danych klasy okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
### <a name="ddxoc-functions"></a>Funkcje DDX_OC  
  
|||  
|-|-|  
|[Ddx_ocbool —](#ddx_ocbool)|Zarządza transferem **BOOL** danych między właściwości formantu OLE i **BOOL** element członkowski danych.|  
|[Ddx_ocboolro —](#ddx_ocboolro)|Zarządza transferem **BOOL** danych między właściwością tylko do odczytu formantów OLE i **BOOL** element członkowski danych.|  
|[Ddx_occolor —](#ddx_occolor)|Zarządza transferem **OLE_COLOR** danych między właściwości formantu OLE i **OLE_COLOR** element członkowski danych.|  
|[Ddx_occolorro —](#ddx_occolorro)|Zarządza transferem **OLE_COLOR** danych między właściwością tylko do odczytu formantów OLE i **OLE_COLOR** element członkowski danych.|  
|[Ddx_ocfloat —](#ddx_ocfloat)|Zarządza transferem **float** (lub **podwójne**) dane między właściwością kontrolkę OLE i **float** (lub **podwójne**) elementu członkowskiego danych.|  
|[Ddx_ocfloatro —](#ddx_ocfloatro)|Zarządza transferem **float** (lub **podwójne**) dane między właściwością tylko do odczytu formantów OLE i **float** (lub **podwójne**) danych element członkowski.|  
|[Ddx_ocint —](#ddx_ocint)|Zarządza transferem **int** (lub **długi**) dane między właściwością kontrolkę OLE i **int** (lub **długi**) elementu członkowskiego danych.|  
|[Ddx_ocintro —](#ddx_ocintro)|Zarządza transferem **int** (lub **długi**) dane między właściwością tylko do odczytu formantów OLE i **int** (lub **długi**) elementu członkowskiego danych.|  
|[Ddx_ocshort —](#ddx_ocshort)|Zarządza transferem **krótki** danych między właściwości formantu OLE i **krótki** element członkowski danych.|  
|[Ddx_ocshortro —](#ddx_ocshortro)|Zarządza transferem **krótki** danych między właściwością tylko do odczytu formantów OLE i **krótki** element członkowski danych.|  
|[Ddx_octext —](#ddx_octext)|Zarządza transferem **cstring —** danych między właściwości formantu OLE i **cstring —** element członkowski danych.|  
|[Ddx_octextro —](#ddx_octextro)|Zarządza transferem **cstring —** danych między właściwością tylko do odczytu formantów OLE i **cstring —** element członkowski danych.|  
  
##  <a name="ddx_ocbool"></a>  Ddx_ocbool —  
 `DDX_OCBool` Funkcji zarządzania transferem **BOOL** tworzą dane między właściwością kontrolkę OLE w oknie dialogowym, widoku lub formantu widoku obiektu i **BOOL** element członkowski danych okna dialogowego, w widoku formularza lub Obiekt widoku formantu.  
  
```   
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    BOOL& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *nIDC*  
 Identyfikator formantu OLE w okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
 *identyfikator DISPID*  
 Identyfikator wysyłania właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant wyświetlania obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek:** afxdisp.h  
  
##  <a name="ddx_ocboolro"></a>  Ddx_ocboolro —  
 `DDX_OCBoolRO` Funkcji zarządzania transferem **BOOL** danych między formantów OLE w oknie dialogowym właściwości tylko do odczytu formularza widoku lub formantu widoku obiektu i **BOOL** element członkowski danych okna dialogowego Widok formularza, lub obiekt formantu widoku.  
  
```   
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    BOOL& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *nIDC*  
 Identyfikator formantu OLE w okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
 *identyfikator DISPID*  
 Identyfikator wysyłania właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant wyświetlania obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="ddx_occolor"></a>  Ddx_occolor —  
 `DDX_OCColor` Funkcja zarządza transferem danych OLE_COLOR między właściwości formantu OLE w widoku formularza, okno dialogowe lub obiekt formantu widoku i element członkowski danych OLE_COLOR okna dialogowego widok formularza lub kontrolować obiekt widoku.  
  
```   
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    OLE_COLOR& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *nIDC*  
 Identyfikator formantu OLE w okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
 *identyfikator DISPID*  
 Identyfikator wysyłania właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant wyświetlania obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="ddx_occolorro"></a>  Ddx_occolorro —  
 `DDX_OCColorRO` Funkcja zarządza transferem danych OLE_COLOR między właściwością tylko do odczytu formantu OLE w widoku formularza, okno dialogowe lub obiekt formantu widoku i element członkowski danych OLE_COLOR okna dialogowego widok formularza lub kontrolować obiekt widoku.  
  
```   
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    OLE_COLOR& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *nIDC*  
 Identyfikator formantu OLE w okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
 *identyfikator DISPID*  
 Identyfikator wysyłania właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant wyświetlania obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="ddx_ocfloat"></a>  Ddx_ocfloat —  
 `DDX_OCFloat` Funkcji zarządzania transferem **float** (lub **podwójne**) tworzą dane między właściwością kontrolkę OLE w oknie dialogowym, widoku lub formantu widoku obiektu i **float** (lub **podwójne**) elementu członkowskiego danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
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
 *pDX*  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *nIDC*  
 Identyfikator formantu OLE w okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
 *identyfikator DISPID*  
 Identyfikator wysyłania właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant wyświetlania obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="ddx_ocfloatro"></a>  Ddx_ocfloatro —  
 `DDX_OCFloatRO` Funkcji zarządzania transferem **float** (lub **podwójne**) tworzą dane między właściwością tylko do odczytu formantów OLE w oknie dialogowym, widoku lub formantu widoku obiektu i  **float** (lub **podwójne**) elementu członkowskiego danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
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
 *pDX*  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *nIDC*  
 Identyfikator formantu OLE w okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
 *identyfikator DISPID*  
 Identyfikator wysyłania właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant wyświetlania obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="ddx_ocint"></a>  Ddx_ocint —  
 `DDX_OCInt` Funkcji zarządzania transferem **int** (lub **długi**) tworzą dane między właściwością kontrolkę OLE w oknie dialogowym, widoku lub formantu widoku obiektu i **int**(lub **długi**) elementu członkowskiego danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
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
 *pDX*  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *nIDC*  
 Identyfikator formantu OLE w okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
 *identyfikator DISPID*  
 Identyfikator wysyłania właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant wyświetlania obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="ddx_ocintro"></a>  Ddx_ocintro —  
 `DDX_OCIntRO` Funkcji zarządzania transferem **int** (lub **długi**) tworzą dane między właściwością tylko do odczytu formantów OLE w oknie dialogowym, widoku lub formantu widoku obiektu i **int** (lub **długi**) elementu członkowskiego danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
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
 *pDX*  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *nIDC*  
 Identyfikator formantu OLE w okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
 *identyfikator DISPID*  
 Identyfikator wysyłania właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant wyświetlania obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="ddx_ocshort"></a>  Ddx_ocshort —  
 `DDX_OCShort` Funkcja zarządza transferem danych krótki między właściwości formantu OLE w widoku formularza, okno dialogowe lub obiekt formantu widoku i element członkowski danych krótkich okna dialogowego widok formularza lub kontrolować obiekt widoku.  
  
```   
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    short& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *nIDC*  
 Identyfikator formantu OLE w okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
 *identyfikator DISPID*  
 Identyfikator wysyłania właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant wyświetlania obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="ddx_ocshortro"></a>  Ddx_ocshortro —  
 `DDX_OCShortRO` Funkcja zarządza transferem danych krótki między właściwością tylko do odczytu formantów OLE w oknie dialogowym widoku formularza lub obiekt formantu widoku i element członkowski danych krótkich okna dialogowego widok formularza lub kontrolować obiekt widoku.  
  
```   
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    short& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *nIDC*  
 Identyfikator formantu OLE w okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
 *identyfikator DISPID*  
 Identyfikator wysyłania właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant wyświetlania obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="ddx_octext"></a>  Ddx_octext —  
 **Ddx_octext —** funkcji zarządzania transferem **cstring —** tworzą dane między właściwością kontrolkę OLE w oknie dialogowym, widoku lub formantu widoku obiektu i **cstring —** danych element członkowski — okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
```   
void AFXAPI DDX_OCText(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    CString& value); 
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Wskaźnik do **cdataexchange —** obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *nIDC*  
 Identyfikator formantu OLE w okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
 *identyfikator DISPID*  
 Identyfikator wysyłania właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant wyświetlania obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h  
  
##  <a name="ddx_octextro"></a>  Ddx_octextro —  
 `DDX_OCTextRO` Funkcji zarządzania transferem `CString` danych między formantów OLE w oknie dialogowym właściwości tylko do odczytu formularza widoku lub formantu widoku obiektu i `CString` element członkowski danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
```  
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    CString& value); 
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 *nIDC*  
 Identyfikator formantu OLE w okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
 *identyfikator DISPID*  
 Identyfikator wysyłania właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant wyświetlania obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdisp.h
    
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
