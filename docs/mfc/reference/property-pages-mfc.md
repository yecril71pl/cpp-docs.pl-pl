---
title: Strony właściwości (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 9689d511760752903b83b34199fb035c0e7a8d37
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214051"
---
# <a name="property-pages-mfc"></a>Strony właściwości (MFC)

Na stronach właściwości są wyświetlane bieżące wartości określonych właściwości kontrolki OLE w dostosowywalnym interfejsie graficznym do wyświetlania i edytowania poprzez obsługę mechanizmu mapowania danych opartego na wymianie danych okna dialogowego (DDX).

Mechanizm mapowania danych mapuje kontrolki strony właściwości na poszczególne właściwości kontrolki OLE. Wartość właściwości kontrolki odzwierciedla stan lub zawartość kontrolki strony właściwości. Mapowanie między kontrolkami i właściwościami strony właściwości jest określane przez **DDP_** wywołań funkcji w `DoDataExchange` funkcji składowej strony właściwości. Poniżej znajduje się lista funkcji **DDP_** , które wprowadzają dane przy użyciu strony właściwości kontrolki:

### <a name="property-page-data-transfer"></a>Transfer danych strony właściwości

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|Łączy indeks zaznaczonego ciągu w polu kombi z właściwością kontrolki.|
|[DDP_CBString](#ddp_cbstring)|Łączy wybrany ciąg w polu kombi z właściwością kontrolki. Wybrany ciąg może rozpoczynać się od tych samych liter co wartość właściwości, ale nie musi być w pełni dopasowany.|
|[DDP_CBStringExact](#ddp_cbstringexact)|Łączy wybrany ciąg w polu kombi z właściwością kontrolki. Wybrany ciąg i wartość ciągu właściwości muszą być dokładnie zgodne.|
|[DDP_Check](#ddp_check)|Łączy pole wyboru na stronie właściwości kontrolki z właściwością kontrolki.|
|[DDP_LBIndex](#ddp_lbindex)|Łączy indeks zaznaczonego ciągu w polu listy z właściwością kontrolki.|
|[DDP_LBString](#ddp_lbstring)|Łączy wybrany ciąg w polu listy z właściwością kontrolki. Wybrany ciąg może rozpoczynać się od tych samych liter co wartość właściwości, ale nie musi być w pełni dopasowany.|
|[DDP_LBStringExact](#ddp_lbstringexact)|Łączy wybrany ciąg w polu listy z właściwością kontrolki. Wybrany ciąg i wartość ciągu właściwości muszą być dokładnie zgodne.|
|[DDP_PostProcessing](#ddp_postprocessing)|Kończy transfer wartości właściwości z formantu.|
|[DDP_Radio](#ddp_radio)|Łączy grupę przycisków radiowych na stronie właściwości kontrolki z właściwością kontrolki.|
|[DDP_Text](#ddp_text)|Łączy formant na stronie właściwości kontrolki z właściwością kontrolki. Ta funkcja obsługuje kilka różnych typów właściwości, takich jak **`double`** , **`short`** , BSTR i **`long`** .|

Aby uzyskać więcej informacji na temat `DoDataExchange` funkcji i stron właściwości, zobacz artykuł [formanty ActiveX: strony właściwości](../../mfc/mfc-activex-controls-property-pages.md).

Poniżej znajduje się lista makr służących do tworzenia stron właściwości kontrolki OLE i zarządzania nimi:

### <a name="property-pages"></a>Strony właściwości

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Rozpoczyna listę identyfikatorów stron właściwości.|
|[END_PROPPAGEIDS](#end_proppageids)|Zamyka listę identyfikatorów stron właściwości.|
|[PROPPAGEID](#proppageid)|Deklaruje stronę właściwości klasy kontrolki.|

## <a name="ddp_cbindex"></a><a name="ddp_cbindex"></a>DDP_CBIndex

Wywołaj tę funkcję w funkcji strony właściwości `DoDataExchange` , aby zsynchronizować wartość właściwości Integer z indeksem bieżącego zaznaczenia w polu kombi na stronie właściwości.

```cpp
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*id*<br/>
Identyfikator zasobu kontrolki pola kombi skojarzonej z właściwością kontrolki określoną przez *pszPropName*.

*członkiem*<br/>
Zmienna członkowska skojarzona z kontrolką strony właściwości określoną przez *Identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości kontrolki, która ma być wymieniana z kontrolką pola kombi określoną przez *Identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana przed odpowiednim `DDX_CBIndex` wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="ddp_cbstring"></a><a name="ddp_cbstring"></a>DDP_CBString

Wywołaj tę funkcję w funkcji strony właściwości `DoDataExchange` , aby zsynchronizować wartość właściwości String z bieżącym wyborem w polu kombi na stronie właściwości.

```cpp
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*id*<br/>
Identyfikator zasobu kontrolki pola kombi skojarzonej z właściwością kontrolki określoną przez *pszPropName*.

*członkiem*<br/>
Zmienna członkowska skojarzona z kontrolką strony właściwości określoną przez *Identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości kontrolki, która ma być wymieniana z ciągiem pola kombi określonym przez *Identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana przed odpowiednim `DDX_CBString` wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="ddp_cbstringexact"></a><a name="ddp_cbstringexact"></a>DDP_CBStringExact

Wywołaj tę funkcję w funkcji strony właściwości `DoDataExchange` , aby zsynchronizować wartość właściwości ciągu, która dokładnie pasuje do bieżącego zaznaczenia w polu kombi na stronie właściwości.

```cpp
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*id*<br/>
Identyfikator zasobu kontrolki pola kombi skojarzonej z właściwością kontrolki określoną przez *pszPropName*.

*członkiem*<br/>
Zmienna członkowska skojarzona z kontrolką strony właściwości określoną przez *Identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości kontrolki, która ma być wymieniana z ciągiem pola kombi określonym przez *Identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana przed odpowiednim `DDX_CBStringExact` wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="ddp_check"></a><a name="ddp_check"></a>DDP_Check

Wywołaj tę funkcję w funkcji strony właściwości, `DoDataExchange` Aby zsynchronizować wartość właściwości ze skojarzoną stroną właściwości formant pola wyboru.

```cpp
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*id*<br/>
Identyfikator zasobu kontrolki pola wyboru skojarzonej z właściwością kontrolki określoną przez *pszPropName*.

*członkiem*<br/>
Zmienna członkowska skojarzona z kontrolką strony właściwości określoną przez *Identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości kontrolki, która ma być wymieniana z kontrolką pola wyboru określoną przez *Identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana przed odpowiednim `DDX_Check` wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="ddp_lbindex"></a><a name="ddp_lbindex"></a>DDP_LBIndex

Wywołaj tę funkcję w funkcji strony właściwości `DoDataExchange` , aby zsynchronizować wartość właściwości Integer z indeksem bieżącego zaznaczenia w polu listy na stronie właściwości.

```cpp
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*id*<br/>
Identyfikator zasobu kontrolki pole listy skojarzonej z właściwością kontrolki określoną przez *pszPropName*.

*członkiem*<br/>
Zmienna członkowska skojarzona z kontrolką strony właściwości określoną przez *Identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości kontrolki, która ma być wymieniana z ciągiem pola listy określonym przez *Identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana przed odpowiednim `DDX_LBIndex` wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="ddp_lbstring"></a><a name="ddp_lbstring"></a>DDP_LBString

Wywołaj tę funkcję w funkcji strony właściwości `DoDataExchange` , aby zsynchronizować wartość właściwości String z bieżącym wyborem w polu listy na stronie właściwości.

```cpp
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*id*<br/>
Identyfikator zasobu kontrolki pole listy skojarzonej z właściwością kontrolki określoną przez *pszPropName*.

*członkiem*<br/>
Zmienna członkowska skojarzona z kontrolką strony właściwości określoną przez *Identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości kontrolki, która ma być wymieniana z ciągiem pola listy określonym przez *Identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana przed odpowiednim `DDX_LBString` wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="ddp_lbstringexact"></a><a name="ddp_lbstringexact"></a>DDP_LBStringExact

Wywołaj tę funkcję w funkcji strony właściwości `DoDataExchange` , aby zsynchronizować wartość właściwości ciągu, która dokładnie pasuje do bieżącego zaznaczenia w polu listy na stronie właściwości.

```cpp
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*id*<br/>
Identyfikator zasobu kontrolki pole listy skojarzonej z właściwością kontrolki określoną przez *pszPropName*.

*członkiem*<br/>
Zmienna członkowska skojarzona z kontrolką strony właściwości określoną przez *Identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości kontrolki, która ma być wymieniana z ciągiem pola listy określonym przez *Identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana przed odpowiednim `DDX_LBStringExact` wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="ddp_postprocessing"></a><a name="ddp_postprocessing"></a>DDP_PostProcessing

Wywołaj tę funkcję w funkcji strony właściwości `DoDataExchange` , aby zakończyć transfer wartości właściwości ze strony właściwości do kontrolki, gdy są zapisywane wartości właściwości.

```cpp
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana po zakończeniu wszystkich funkcji wymiany danych. Na przykład:

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="ddp_radio"></a><a name="ddp_radio"></a>DDP_Radio

Wywołaj tę funkcję w funkcji kontrolki `DoPropExchange` , aby zsynchronizować wartość właściwości ze skojarzoną kontrolką przycisku radiowego strony właściwości.

```cpp
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*id*<br/>
Identyfikator zasobu kontrolki przycisku radiowego skojarzonej z właściwością kontrolki określoną przez *pszPropName*.

*członkiem*<br/>
Zmienna członkowska skojarzona z kontrolką strony właściwości określoną przez *Identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości kontrolki, która ma być wymieniana z kontrolką przycisku radiowego określoną przez *Identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana przed odpowiednim `DDX_Radio` wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="ddp_text"></a><a name="ddp_text"></a>DDP_Text

Wywołaj tę funkcję w funkcji kontrolki `DoDataExchange` , aby zsynchronizować wartość właściwości ze skojarzoną kontrolką strony właściwości.

```cpp
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
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*id*<br/>
Identyfikator zasobu kontrolki skojarzonej z właściwością kontrolki określoną przez *pszPropName*.

*członkiem*<br/>
Zmienna członkowska skojarzona z kontrolką strony właściwości określoną przez *Identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości kontrolki, która ma być wymieniana z kontrolką określoną przez *Identyfikator*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana przed odpowiednim `DDX_Text` wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="begin_proppageids"></a><a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS

Rozpoczyna definicję listy identyfikatorów stron właściwości formantu.

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki, dla której są określone strony właściwości.

*liczbą*<br/>
Liczba stron właściwości używanych przez klasę formantu.

### <a name="remarks"></a>Uwagi

W pliku implementacji (. cpp), który definiuje funkcje elementów członkowskich klasy, uruchom listę stron właściwości za pomocą makra BEGIN_PROPPAGEIDS, a następnie Dodaj wpisy makr dla każdej ze stron właściwości i wypełnij listę stron właściwości za pomocą makra END_PROPPAGEIDS.

Aby uzyskać więcej informacji na temat stron właściwości, zobacz artykuł [formanty ActiveX: strony właściwości](../../mfc/mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="end_proppageids"></a><a name="end_proppageids"></a>END_PROPPAGEIDS

Zamyka definicję listy identyfikatorów stron właściwości.

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki, która jest właścicielem strony właściwości.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="proppageid"></a><a name="proppageid"></a>PROPPAGEID

Dodaje stronę właściwości do użycia przez formant OLE.

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
Unikatowy identyfikator klasy strony właściwości.

### <a name="remarks"></a>Uwagi

Wszystkie makra PROPPAGEID należy umieścić między makrami BEGIN_PROPPAGEIDS i END_PROPPAGEIDS w pliku implementacji formantu.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="see-also"></a>Zobacz także

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
