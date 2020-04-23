---
title: Strony właściwości (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 6456a192a502a0fcc032eaefc667c90ecec86d42
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751140"
---
# <a name="property-pages-mfc"></a>Strony właściwości (MFC)

Strony właściwości wyświetlają bieżące wartości określonych właściwości sterowania OLE w dostosowywanym, graficznym interfejsie do przeglądania i edycji, obsługując mechanizm mapowania danych oparty na wymianie danych dialogowych (DDX).

Ten mechanizm mapowania danych mapuje formanty strony właściwości do poszczególnych właściwości formantu OLE. Wartość właściwości control odzwierciedla stan lub zawartość formantu strony właściwości. Mapowanie między formantami strony właściwości **DDP_** i właściwości jest określona przez `DoDataExchange` DDP_ wywołania funkcji funkcji w funkcji elementu członkowskiego strony właściwości. Poniżej znajduje się lista **DDP_** funkcji, które wymieniają dane wprowadzone przy użyciu strony właściwości formantu:

### <a name="property-page-data-transfer"></a>Transfer danych strony właściwości

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|Łączy indeks wybranego ciągu w polu kombi z właściwością formantu.|
|[DDP_CBString](#ddp_cbstring)|Łączy zaznaczony ciąg w polu kombi z właściwością formantu. Wybrany ciąg może zaczynać się od tych samych liter co wartość właściwości, ale nie musi być w pełni dopasowany.|
|[DDP_CBStringExact](#ddp_cbstringexact)|Łączy zaznaczony ciąg w polu kombi z właściwością formantu. Wybrany ciąg i wartość ciągu właściwości musi być dokładnie zgodna.|
|[DDP_Check](#ddp_check)|Łączy pole wyboru na stronie właściwości formantu z właściwością formantu.|
|[DDP_LBIndex](#ddp_lbindex)|Łączy indeks wybranego ciągu w polu listy z właściwością formantu.|
|[DDP_LBString](#ddp_lbstring)|Łączy zaznaczony ciąg w polu listy z właściwością formantu. Wybrany ciąg może zaczynać się od tych samych liter co wartość właściwości, ale nie musi być w pełni dopasowany.|
|[DDP_LBStringExact](#ddp_lbstringexact)|Łączy zaznaczony ciąg w polu listy z właściwością formantu. Wybrany ciąg i wartość ciągu właściwości musi być dokładnie zgodna.|
|[DDP_PostProcessing](#ddp_postprocessing)|Kończy przenoszenie wartości właściwości z formantu.|
|[DDP_Radio](#ddp_radio)|Łączy grupę przycisków opcji na stronie właściwości formantu z właściwością formantu.|
|[DDP_Text](#ddp_text)|Łączy formant na stronie właściwości formantu z właściwością formantu. Ta funkcja obsługuje kilka różnych typów właściwości, takich jak **double**, **short**, BSTR i **long**.|

Aby uzyskać więcej `DoDataExchange` informacji na temat funkcji i stron właściwości, zobacz artykuł [ActiveX Formanty: Strony właściwości](../../mfc/mfc-activex-controls-property-pages.md).

Poniżej znajduje się lista makr używanych do tworzenia stron właściwości i zarządzania nimi dla formantu OLE:

### <a name="property-pages"></a>Strony właściwości

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Rozpoczyna się lista identyfikatorów strony właściwości.|
|[END_PROPPAGEIDS](#end_proppageids)|Kończy listę identyfikatorów stron właściwości.|
|[PROPPAGEID (PROPPAGEID)](#proppageid)|Deklaruje stronę właściwości klasy formantu.|

## <a name="ddp_cbindex"></a><a name="ddp_cbindex"></a>DDP_CBIndex

Wywołanie tej funkcji w `DoDataExchange` funkcji strony właściwości, aby zsynchronizować wartość właściwości całkowitej z indeksem bieżącego zaznaczenia w polu kombi na stronie właściwości.

```cpp
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*Identyfikator*<br/>
Identyfikator zasobu formantu pola kombi skojarzonego z właściwością formantu określoną przez *pszPropName*.

*Członkowskich*<br/>
Zmienna elementu członkowskiego skojarzona z formantem strony właściwości określonym przez *identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości formantu, która ma być wymieniona z formantem pola kombi określonym przez *id*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być `DDX_CBIndex` wywoływana przed odpowiednim wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="ddp_cbstring"></a><a name="ddp_cbstring"></a>DDP_CBString

Wywołanie tej funkcji w `DoDataExchange` funkcji strony właściwości, aby zsynchronizować wartość właściwości string z bieżącym zaznaczeniem w polu kombi na stronie właściwości.

```cpp
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*Identyfikator*<br/>
Identyfikator zasobu formantu pola kombi skojarzonego z właściwością formantu określoną przez *pszPropName*.

*Członkowskich*<br/>
Zmienna elementu członkowskiego skojarzona z formantem strony właściwości określonym przez *identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości formantu, która ma być wymieniona z ciągiem pola kombi określonym przez *id*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być `DDX_CBString` wywoływana przed odpowiednim wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="ddp_cbstringexact"></a><a name="ddp_cbstringexact"></a>DDP_CBStringExact

Wywołanie tej funkcji w `DoDataExchange` funkcji strony właściwości, aby zsynchronizować wartość właściwości string, która dokładnie pasuje do bieżącego zaznaczenia w polu kombi na stronie właściwości.

```cpp
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*Identyfikator*<br/>
Identyfikator zasobu formantu pola kombi skojarzonego z właściwością formantu określoną przez *pszPropName*.

*Członkowskich*<br/>
Zmienna elementu członkowskiego skojarzona z formantem strony właściwości określonym przez *identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości formantu, która ma być wymieniona z ciągiem pola kombi określonym przez *id*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być `DDX_CBStringExact` wywoływana przed odpowiednim wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="ddp_check"></a><a name="ddp_check"></a>DDP_Check

Wywołanie tej funkcji w `DoDataExchange` funkcji strony właściwości, aby zsynchronizować wartość właściwości z formantem pola wyboru strony skojarzonej właściwości.

```cpp
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*Identyfikator*<br/>
Identyfikator zasobu formantu pola wyboru skojarzonego z właściwością formantu określoną przez *pszPropName*.

*Członkowskich*<br/>
Zmienna elementu członkowskiego skojarzona z formantem strony właściwości określonym przez *identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości formantu, która ma być wymieniona z formantem pola wyboru określonym przez *id*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być `DDX_Check` wywoływana przed odpowiednim wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="ddp_lbindex"></a><a name="ddp_lbindex"></a>DDP_LBIndex

Wywołanie tej funkcji w `DoDataExchange` funkcji strony właściwości, aby zsynchronizować wartość właściwości całkowitej z indeksem bieżącego zaznaczenia w polu listy na stronie właściwości.

```cpp
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*Identyfikator*<br/>
Identyfikator zasobu formantu pola listy skojarzonego z właściwością formantu określoną przez *pszPropName*.

*Członkowskich*<br/>
Zmienna elementu członkowskiego skojarzona z formantem strony właściwości określonym przez *identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości formantu, która ma być wymieniona z ciągiem pola listy określonym przez *id*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być `DDX_LBIndex` wywoływana przed odpowiednim wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="ddp_lbstring"></a><a name="ddp_lbstring"></a>DDP_LBString

Wywołanie tej funkcji w `DoDataExchange` funkcji strony właściwości, aby zsynchronizować wartość właściwości string z bieżącym zaznaczeniem w polu listy na stronie właściwości.

```cpp
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*Identyfikator*<br/>
Identyfikator zasobu formantu pola listy skojarzonego z właściwością formantu określoną przez *pszPropName*.

*Członkowskich*<br/>
Zmienna elementu członkowskiego skojarzona z formantem strony właściwości określonym przez *identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości formantu, która ma być wymieniona z ciągiem pola listy określonym przez *id*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być `DDX_LBString` wywoływana przed odpowiednim wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="ddp_lbstringexact"></a><a name="ddp_lbstringexact"></a>DDP_LBStringExact

Wywołanie tej funkcji w `DoDataExchange` funkcji strony właściwości, aby zsynchronizować wartość właściwości string, która dokładnie pasuje do bieżącego zaznaczenia w polu listy na stronie właściwości.

```cpp
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*Identyfikator*<br/>
Identyfikator zasobu formantu pola listy skojarzonego z właściwością formantu określoną przez *pszPropName*.

*Członkowskich*<br/>
Zmienna elementu członkowskiego skojarzona z formantem strony właściwości określonym przez *identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości formantu, która ma być wymieniona z ciągiem pola listy określonym przez *id*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być `DDX_LBStringExact` wywoływana przed odpowiednim wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="ddp_postprocessing"></a><a name="ddp_postprocessing"></a>DDP_PostProcessing

Wywołanie tej funkcji w `DoDataExchange` funkcji strony właściwości, aby zakończyć przenoszenie wartości właściwości ze strony właściwości do formantu, gdy wartości właściwości są zapisywane.

```cpp
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być wywoływana po zakończeniu wszystkich funkcji wymiany danych. Przykład:

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="ddp_radio"></a><a name="ddp_radio"></a>DDP_Radio

Wywołanie tej funkcji w `DoPropExchange` funkcji formantu, aby zsynchronizować wartość właściwości z kontrolką przycisku radiowego powiązanej strony właściwości.

```cpp
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*Identyfikator*<br/>
Identyfikator zasobu formantu przycisku radiowego skojarzonego z właściwością formantu określoną przez *pszPropName*.

*Członkowskich*<br/>
Zmienna elementu członkowskiego skojarzona z formantem strony właściwości określonym przez *identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości formantu, która ma być wymieniona za pomocą kontrolki przycisku radiowego określonej przez *id*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być `DDX_Radio` wywoływana przed odpowiednim wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="ddp_text"></a><a name="ddp_text"></a>DDP_Text

Wywołanie tej funkcji w `DoDataExchange` funkcji formantu, aby zsynchronizować wartość właściwości z formantu strony skojarzonej właściwości.

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

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*Identyfikator*<br/>
Identyfikator zasobu formantu skojarzonego z właściwością formantu określoną przez *pszPropName*.

*Członkowskich*<br/>
Zmienna elementu członkowskiego skojarzona z formantem strony właściwości określonym przez *identyfikator* i właściwość określoną przez *pszPropName*.

*pszPropName*<br/>
Nazwa właściwości właściwości formantu, która ma być wymieniona z formantem określonym przez *id*.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być `DDX_Text` wywoływana przed odpowiednim wywołaniem funkcji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="begin_proppageids"></a><a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS

Rozpoczyna definicję listy identyfikatorów stron właściwości formantu.

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy formantu, dla której są określone strony właściwości.

*Liczba*<br/>
Liczba stron właściwości używanych przez klasę kontrolną.

### <a name="remarks"></a>Uwagi

W pliku implementacji (.cpp), który definiuje funkcje członkowskie dla klasy, uruchom listę stron właściwości BEGIN_PROPPAGEIDS makra, a następnie dodaj wpisy makr dla każdej ze stron właściwości i uzupełnij listę stron właściwości END_PROPPAGEIDS makra.

Aby uzyskać więcej informacji na temat stron właściwości, zobacz artykuł [ActiveX Controls: Property Pages](../../mfc/mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="end_proppageids"></a><a name="end_proppageids"></a>END_PROPPAGEIDS

Kończy definicję listy identyfikatorów strony właściwości.

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy formantu, która jest właścicielem strony właściwości.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="proppageid"></a><a name="proppageid"></a>PROPPAGEID (PROPPAGEID)

Dodaje stronę właściwości do użycia przez formant OLE.

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
Unikatowy identyfikator klasy strony właściwości.

### <a name="remarks"></a>Uwagi

Wszystkie makra PROPPAGEID muszą być umieszczone między makrami BEGIN_PROPPAGEIDS i END_PROPPAGEIDS w pliku implementacji formantu.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
