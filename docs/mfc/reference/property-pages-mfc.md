---
title: Strony właściwości (MFC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6d72a6dbe8480e37751b760961f466db02c0c0d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403085"
---
# <a name="property-pages-mfc"></a>Strony właściwości (MFC)

Strony właściwości wyświetlić bieżących wartości określonych właściwości kontrolki OLE w można dostosować interfejs graficzny służący do wyświetlania i edytowania dzięki obsłudze mechanizmu mapowania danych oparte na wymiana danych okna dialogowego (DDX).

Ten mechanizm mapowanie danych mapuje właściwości formantów strony do poszczególnych właściwości kontrolki OLE. Wartość właściwości kontrolki odzwierciedla stan lub zawartość formantu strony właściwości. Mapowanie między formantów strony właściwości i właściwości jest określona przez **ddp_ —** funkcja wywołuje na stronie właściwości `DoDataExchange` funkcja elementu członkowskiego. Poniżej przedstawiono listę **ddp_ —** funkcje, które wymiany danych wprowadzonych, używając strony właściwości kontrolki:

### <a name="property-page-data-transfer"></a>Transfer danych strony właściwości

|||
|-|-|
|[Ddp_cbindex —](#ddp_cbindex)|Łączy indeksu zaznaczony ciąg w polu kombi z właściwością kontrolki.|
|[Ddp_cbstring —](#ddp_cbstring)|Łączy zaznaczony ciąg w polu kombi z właściwością kontrolki. Zaznaczony ciąg może rozpoczynać się od tych samych liter jako wartość właściwości, ale nie musi, w pełni zgodny.|
|[Ddp_cbstringexact —](#ddp_cbstringexact)|Łączy zaznaczony ciąg w polu kombi z właściwością kontrolki. Zaznaczony ciąg i wartość ciągu dla właściwości muszą być zgodne.|
|[Ddp_check —](#ddp_check)|Pole wyboru na stronie właściwości kontrolki z właściwością kontrolki łącza.|
|[Ddp_lbindex —](#ddp_lbindex)|Łączy indeksu zaznaczony ciąg w polu listy, z właściwością kontrolki.|
|[Ddp_lbstring —](#ddp_lbstring)|Łączy zaznaczony ciąg w polu listy, z właściwością kontrolki. Zaznaczony ciąg może rozpoczynać się od tych samych liter jako wartość właściwości, ale nie musi być zgodna go całkowicie.|
|[Ddp_lbstringexact —](#ddp_lbstringexact)|Łączy zaznaczony ciąg w polu listy, z właściwością kontrolki. Zaznaczony ciąg i wartość ciągu dla właściwości muszą być zgodne.|
|[Ddp_postprocessing —](#ddp_postprocessing)|Kończy transfer wartości właściwości z Twoją kontrolą.|
|[Ddp_radio —](#ddp_radio)|Grupa przycisków radiowych, na stronie właściwości kontrolki z właściwością kontrolki łącza.|
|[Ddp_text —](#ddp_text)|Łączy kontrolki na stronie właściwości kontrolki z właściwością kontrolki. Ta funkcja obsługuje kilka różnych typów właściwości, takie jak **double**, **krótki**, BSTR, i **długie**.|

Aby uzyskać więcej informacji na temat `DoDataExchange` strony funkcji i właściwości, zobacz artykuł [kontrolek ActiveX: strony właściwości](../../mfc/mfc-activex-controls-property-pages.md).

Oto lista makra używane do tworzenia i zarządzania nimi stron właściwości kontrolki OLE:

### <a name="property-pages"></a>Strony właściwości

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Rozpoczyna się na liście identyfikatory stron właściwości.|
|[END_PROPPAGEIDS](#end_proppageids)|Kończy się na liście identyfikatory stron właściwości.|
|[PROPPAGEID](#proppageid)|Deklaruje strony właściwości klasy kontrolki.|

##  <a name="ddp_cbindex"></a>  Ddp_cbindex —

Wywołaj tę funkcję, na stronie właściwości `DoDataExchange` funkcję, aby zsynchronizować wartość właściwości Liczba całkowita z indeksem bieżące zaznaczenie w polu kombi na stronie właściwości.

```
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*id*<br/>
Identyfikator zasobu kombi polu kontrolkę skojarzoną z określonym przez właściwości kontrolki *pszPropName*.

*Element członkowski*<br/>
Skojarzony formant strony właściwości, które są określone przez zmienną członkowską *identyfikator* i określona przez właściwość *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości wymieniane z kontrolki pola kombi, które są określone przez właściwości kontrolki *identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna zostać wywołana przed odpowiednimi `DDX_CBIndex` wywołania funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="ddp_cbstring"></a>  Ddp_cbstring —

Wywołaj tę funkcję, na stronie właściwości `DoDataExchange` funkcję, aby zsynchronizować wartość właściwości ciągu zachowując bieżący wybór w polu kombi na stronie właściwości.

```
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*id*<br/>
Identyfikator zasobu kombi polu kontrolkę skojarzoną z określonym przez właściwości kontrolki *pszPropName*.

*Element członkowski*<br/>
Skojarzony formant strony właściwości, które są określone przez zmienną członkowską *identyfikator* i określona przez właściwość *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości wymieniane parametrami pola kombi, określone przez właściwości kontrolki *identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna zostać wywołana przed odpowiednimi `DDX_CBString` wywołania funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="ddp_cbstringexact"></a>  Ddp_cbstringexact —

Wywołaj tę funkcję, na stronie właściwości `DoDataExchange` funkcję, aby zsynchronizować wartość właściwości ciągu, który dokładnie pasuje do bieżącego zaznaczenia w polu kombi na stronie właściwości.

```
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*id*<br/>
Identyfikator zasobu kombi polu kontrolkę skojarzoną z określonym przez właściwości kontrolki *pszPropName*.

*Element członkowski*<br/>
Skojarzony formant strony właściwości, które są określone przez zmienną członkowską *identyfikator* i określona przez właściwość *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości wymieniane parametrami pola kombi, określone przez właściwości kontrolki *identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna zostać wywołana przed odpowiednimi `DDX_CBStringExact` wywołania funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="ddp_check"></a>  Ddp_check —

Wywołaj tę funkcję, na stronie właściwości `DoDataExchange` funkcję, aby zsynchronizować wartości właściwości z kontrolka pola wyboru strony skojarzonej właściwości.

```
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*id*<br/>
Identyfikator zasobu w kontrolce pola wyboru skojarzone z określonym przez właściwości kontrolki *pszPropName*.

*Element członkowski*<br/>
Skojarzony formant strony właściwości, które są określone przez zmienną członkowską *identyfikator* i określona przez właściwość *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości wymieniane z określonego przez formant pola wyboru właściwości kontrolki *identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna zostać wywołana przed odpowiednimi `DDX_Check` wywołania funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="ddp_lbindex"></a>  Ddp_lbindex —

Wywołaj tę funkcję, na stronie właściwości `DoDataExchange` funkcję, aby zsynchronizować wartość właściwości Liczba całkowita z indeksem bieżące zaznaczenie w polu listy na stronie właściwości.

```
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*id*<br/>
Identyfikator zasobu listy polu kontrolkę skojarzoną z określonym przez właściwości kontrolki *pszPropName*.

*Element członkowski*<br/>
Skojarzony formant strony właściwości, które są określone przez zmienną członkowską *identyfikator* i określona przez właściwość *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości wymieniane z określonej przez ciąg pole listy właściwości kontrolki *identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna zostać wywołana przed odpowiednimi `DDX_LBIndex` wywołania funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="ddp_lbstring"></a>  Ddp_lbstring —

Wywołaj tę funkcję, na stronie właściwości `DoDataExchange` funkcję, aby zsynchronizować wartość właściwości ciągu zachowując bieżący wybór w polu listy na stronie właściwości.

```
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*id*<br/>
Identyfikator zasobu listy polu kontrolkę skojarzoną z określonym przez właściwości kontrolki *pszPropName*.

*Element członkowski*<br/>
Skojarzony formant strony właściwości, które są określone przez zmienną członkowską *identyfikator* i określona przez właściwość *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości wymieniane z określonej przez ciąg pole listy właściwości kontrolki *identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna zostać wywołana przed odpowiednimi `DDX_LBString` wywołania funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="ddp_lbstringexact"></a>  Ddp_lbstringexact —

Wywołaj tę funkcję, na stronie właściwości `DoDataExchange` funkcję, aby zsynchronizować wartość właściwości ciągu, który dokładnie pasuje do bieżącego zaznaczenia w polu listy na stronie właściwości.

```
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*id*<br/>
Identyfikator zasobu listy polu kontrolkę skojarzoną z określonym przez właściwości kontrolki *pszPropName*.

*Element członkowski*<br/>
Skojarzony formant strony właściwości, które są określone przez zmienną członkowską *identyfikator* i określona przez właściwość *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości wymieniane z określonej przez ciąg pole listy właściwości kontrolki *identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna zostać wywołana przed odpowiednimi `DDX_LBStringExact` wywołania funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="ddp_postprocessing"></a>  Ddp_postprocessing —

Wywołaj tę funkcję, na stronie właściwości `DoDataExchange` funkcji, aby zakończyć transferu wartości właściwości na stronie właściwości do kontrolki, po zapisaniu wartości właściwości.

```
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana po wykonaniu wszystkie funkcje wymiany danych. Na przykład:

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="ddp_radio"></a>  Ddp_radio —

Wywołaj tę funkcję w kontroli nad `DoPropExchange` funkcję, aby zsynchronizować wartości właściwości z kontrolkę przycisku radiowego strony skojarzonej właściwości.

```
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*id*<br/>
Identyfikator zasobu radiowego przycisk kontrolkę skojarzoną z określonym przez właściwości kontrolki *pszPropName*.

*Element członkowski*<br/>
Skojarzony formant strony właściwości, które są określone przez zmienną członkowską *identyfikator* i określona przez właściwość *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości kontrolki wymieniane z określonym przez kontrolkę przycisku radiowego *identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna zostać wywołana przed odpowiednimi `DDX_Radio` wywołania funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="ddp_text"></a>  Ddp_text —

Wywołaj tę funkcję w kontroli nad `DoDataExchange` funkcję, aby zsynchronizować wartości właściwości z formantu strony skojarzonej właściwości.

```
void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    BYTE & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    UINT & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    long & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    DWORD & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    float & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    double & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    CString & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*id*<br/>
Identyfikator zasobu kontrolki skojarzone z określonym przez właściwości kontrolki *pszPropName*.

*Element członkowski*<br/>
Skojarzony formant strony właściwości, które są określone przez zmienną członkowską *identyfikator* i określona przez właściwość *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości wymieniane z kontrolki określonej przez właściwości kontrolki *identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna zostać wywołana przed odpowiednimi `DDX_Text` wywołania funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="begin_proppageids"></a>  BEGIN_PROPPAGEIDS

Rozpoczyna się definicji listy kontroli nad identyfikatory stron właściwości.

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki dla właściwości, które są określone strony.

*Liczba*<br/>
Liczba stron właściwości używane przez klasę formantu.

### <a name="remarks"></a>Uwagi

W pliku implementacji (.cpp), który definiuje funkcji elementów członkowskich dla swojej klasy rozpoczynać lista stron właściwości BEGIN_PROPPAGEIDS — makro, a następnie dodaj makro wpisy dla każdej ze stron właściwości i Pełna lista strony właściwości, za pomocą END_PROPPAGEIDS makra.

Aby uzyskać więcej informacji na stronach właściwości, zobacz artykuł [kontrolek ActiveX: strony właściwości](../../mfc/mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="end_proppageids"></a>  END_PROPPAGEIDS

Kończy definicję listy identyfikator strony właściwości.

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki, która jest właścicielem strony właściwości.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="proppageid"></a>  PROPPAGEID

Dodaje do użycia strony właściwości kontrolki OLE.

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>Parametry

*Identyfikator klasy*<br/>
Identyfikator unikatowy klasy strony właściwości.

### <a name="remarks"></a>Uwagi

Wszystkie makra PROPPAGEID muszą być umieszczone między BEGIN_PROPPAGEIDS i END_PROPPAGEIDS makr w pliku implementacji formantu.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
