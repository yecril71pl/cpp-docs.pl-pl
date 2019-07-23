---
title: Funkcje kodowania tekstu ATL
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
ms.assetid: 2ae1648b-2b87-4112-92aa-0069fcfd23da
ms.openlocfilehash: 1380d33c485c1ac895558bbcaf86c902c6074cd4
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375897"
---
# <a name="atl-text-encoding-functions"></a>Funkcje kodowania tekstu ATL

Te funkcje obsługują kodowanie tekstu i dekodowanie.

|||
|-|-|
|[AtlGetHexValue](#atlgethexvalue)|Wywołaj tę funkcję, aby uzyskać wartość liczbową z liczby szesnastkowej.|
|[AtlGetVersion](#atlgetversion)|Wywołaj tę funkcję, aby uzyskać wersję biblioteki ATL, która jest używana.  |
|[AtlHexDecode](#atlhexdecode)|Dekoduje ciąg danych, który został zakodowany jako tekst szesnastkowy, na przykład przez poprzednie wywołanie do [AtlHexEncode](#atlhexencode).|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego szesnastkowo o określonej długości.|
|[AtlHexEncode](#atlhexencode)|Wywołaj tę funkcję, aby zakodować dane jako ciąg tekstu szesnastkowego.|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.|
|[AtlHexValue](#atlhexvalue)|Wywołaj tę funkcję, aby uzyskać wartość liczbową z liczby szesnastkowej. |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|Wywołaj tę funkcję, aby przekonwertować ciąg Unicode na UTF-8. |
|[BEncode](#bencode)|Wywołaj tę funkcję, aby skonwertować dane przy użyciu kodowania „B”.|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.|
|[EscapeXML](#escapexml)|Wywołaj tę funkcję, aby skonwertować znaki niebezpieczne w XML na ich bezpieczne odpowiedniki.|
|[GetExtendedChars](#getextendedchars)|Wywołaj tę funkcję, aby uzyskać liczbę znaków rozszerzonych w ciągu.|
|[IsExtendedChar](#isextendedchar)|Wywołaj tę funkcję, aby dowiedzieć się, czy dany znak jest znakiem rozszerzonym (mniejszym niż 32, większym niż 126, a nie tabulatorem, znakiem wysuwu wiersza ani returnem)|
|[QEncode](#qencode)|Wywołaj tę funkcję, aby skonwertować dane przy użyciu kodowania „Q”.  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.|
|[QPDecode](#qpdecode)|Dekoduje ciąg danych, który został zakodowany w formacie do drukowania w cudzysłowie, na przykład przez poprzednie wywołanie do [QPEncode](#qpencode).|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego w quoted-printable o określonej długości.|
|[QPEncode](#qpencode)|Wywołaj tę funkcję, aby zakodować dane w formacie quoted-printable.|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.|
|[UUDecode](#uudecode)|Dekoduje ciąg danych, który został wystawiony na przykład przez poprzednie wywołanie do [UUENCODE](#uuencode).|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego w uuencode o określonej długości.|
|[UUEncode](#uuencode)|Wywołaj tę funkcję, aby zakodować dane w uuencode. |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlenc. h

## <a name="atlgethexvalue"></a>AtlGetHexValue

Wywołaj tę funkcję, aby uzyskać wartość liczbową z liczby szesnastkowej.

```
inline char AtlGetHexValue(char chIn) throw();
```

### <a name="parameters"></a>Parametry

*chIn*<br/>
Znak szesnastkowy "0"-"9", "od-'F" lub "od-'F".

### <a name="return-value"></a>Wartość zwracana

Wartość liczbowa znaku wejściowego interpretowana jako cyfra szesnastkowa. Na przykład wejście "0" zwraca wartość 0, a dane wejściowe elementu "A" zwracają wartość 10. Jeśli znak wejściowy nie jest cyfrą szesnastkową, ta funkcja zwraca wartość-1.

## <a name="atlgetversion"></a>AtlGetVersion

Wywołaj tę funkcję, aby uzyskać wersję biblioteki ATL, która jest używana.

```
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);
```

### <a name="parameters"></a>Parametry

*pReserved*<br/>
Zastrzeżony wskaźnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość typu DWORD o wartości całkowitej wersji biblioteki ATL, która jest kompilowana lub uruchomiona.

## <a name="example"></a>Przykład

Funkcja powinna być wywoływana w następujący sposób.

[!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="atlhexdecode"></a>AtlHexDecode

Dekoduje ciąg danych, który został zakodowany jako tekst szesnastkowy, na przykład przez poprzednie wywołanie do [AtlHexEncode](#atlhexencode).

```
inline BOOL AtlHexDecode(
   LPCSTR pSrcData,
   int nSrcLen,
   LPBYTE pbDest,
   int* pnDestLen) throw();
```

### <a name="parameters"></a>Parametry

*pSrcData*<br/>
Ciąg zawierający dane, które mają zostać zdekodowane.

*nSrcLen*<br/>
Długość w znakach *pSrcData*.

*pbDest*<br/>
Bufor przydzielony przez obiekt wywołujący, który odbiera zdekodowane dane.

*pnDestLen*<br/>
Wskaźnik do zmiennej zawierającej długość w bajtach *pbDest*. Jeśli funkcja się powiedzie, zmienna otrzymuje liczbę bajtów zapisywanych w buforze. Jeśli funkcja się nie powiedzie, zmienna otrzymuje wymaganą długość w bajtach buforu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

## <a name="atlhexdecodegetrequiredlength"></a>AtlHexDecodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego szesnastkowo o określonej długości.

```
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba znaków w zakodowanym ciągu.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów wymagana dla buforu, który może zawierać zdekodowany ciąg znaków *nSrcLen* .

## <a name="atlhexencode"></a>AtlHexEncode

Wywołaj tę funkcję, aby zakodować dane jako ciąg tekstu szesnastkowego.

```
inline BOOL AtlHexEncode(
   const BYTE * pbSrcData,
   int nSrcLen,
   LPSTR szDest,
int * pnDestLen) throw();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
Bufor zawierający dane, które mają zostać zakodowane.

*nSrcLen*<br/>
Długość w bajtach danych, które mają zostać zakodowane.

*szDest*<br/>
Bufor przydzielony przez obiekt wywołujący, który ma odbierać zakodowane dane.

*pnDestLen*<br/>
Wskaźnik do zmiennej zawierającej długość w znakach *szDest*. Jeśli funkcja się powiedzie, zmienna otrzymuje liczbę znaków zapisywanych w buforze. Jeśli funkcja się nie powiedzie, zmienna otrzymuje wymaganą długość w znakach bufora.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Każdy bajt danych źródłowych jest zakodowany jako 2 znaki szesnastkowe.

## <a name="atlhexencodegetrequiredlength"></a> AtlHexEncodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.

```
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba bajtów danych do zakodowania.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków wymagana dla buforu, który może przechowywać zakodowane dane z *nSrcLen* bajtów.

## <a name="atlhexvalue"></a>AtlHexValue

Wywołaj tę funkcję, aby uzyskać wartość liczbową z liczby szesnastkowej.

```
inline short AtlHexValue(char chIn) throw();
```

### <a name="parameters"></a>Parametry

*chIn*<br/>
Znak szesnastkowy "0"-"9", "od-'F" lub "od-'F".

### <a name="return-value"></a>Wartość zwracana

Wartość liczbowa znaku wejściowego interpretowana jako cyfra szesnastkowa. Na przykład wejście "0" zwraca wartość 0, a dane wejściowe elementu "A" zwracają wartość 10. Jeśli znak wejściowy nie jest cyfrą szesnastkową, ta funkcja zwraca wartość-1.

## <a name="atlunicodetoutf8"></a>AtlUnicodeToUTF8

Wywołaj tę funkcję, aby przekonwertować ciąg Unicode na UTF-8.

```
ATL_NOINLINE inline int AtlUnicodeToUTF8(
   LPCWSTR wszSrc,
   int nSrc,
   LPSTR szDest,
   int nDest) throw();
```

### <a name="parameters"></a>Parametry

*wszSrc*<br/>
Ciąg Unicode do przekonwertowania

*nSrc*<br/>
Długość w znakach ciągu Unicode.

*szDest*<br/>
Bufor przydzielony przez obiekt wywołujący, aby otrzymać przekonwertowany ciąg.

*nDest*<br/>
Długość w bajtach buforu.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę znaków dla przekonwertowanego ciągu.

### <a name="remarks"></a>Uwagi

Aby określić rozmiar buforu wymaganego przez przekonwertowany ciąg, Wywołaj tę funkcję, przekazując wartość 0 dla *szDest* i *nDest*.

## <a name="bencode"></a>BEncode

Wywołaj tę funkcję, aby skonwertować dane przy użyciu kodowania „B”.

```
inline BOOL BEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet) throw();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
Bufor zawierający dane, które mają zostać zakodowane.

*nSrcLen*<br/>
Długość w bajtach danych, które mają zostać zakodowane.

*szDest*<br/>
Bufor przydzielony przez obiekt wywołujący, który ma odbierać zakodowane dane.

*pnDestLen*<br/>
Wskaźnik do zmiennej zawierającej długość w znakach *szDest*. Jeśli funkcja się powiedzie, zmienna otrzymuje liczbę znaków zapisywanych w buforze. Jeśli funkcja się nie powiedzie, zmienna otrzymuje wymaganą długość w znakach bufora.

*pszCharSet*<br/>
Zestaw znaków do użycia podczas konwersji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Schemat kodowania "B" został opisany w dokumencie RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)).

## <a name="bencodegetrequiredlength"></a>BEncodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.

```
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba bajtów danych do zakodowania.

*nCharsetLen*<br/>
Długość w znakach zestawu znaków, który ma zostać użyty do konwersji.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków wymagana dla buforu, który może przechowywać zakodowane dane z *nSrcLen* bajtów.

### <a name="remarks"></a>Uwagi

Schemat kodowania "B" został opisany w dokumencie RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)).

## <a name="escapexml"></a>EscapeXML

Wywołaj tę funkcję, aby skonwertować znaki niebezpieczne w XML na ich bezpieczne odpowiedniki.

```
inline int EscapeXML(
   const wchar_t * szIn,
   int nSrcLen,
   wchar_t * szEsc,
   int nDestLen,
   DWORD dwFlags = ATL_ESC_FLAG_NONE) throw();
```

### <a name="parameters"></a>Parametry

*szIn*<br/>
Ciąg do przekonwertowania.

*nSrclen*<br/>
Długość ciągu znaków do przekonwertowania.

*szEsc*<br/>
Bufor przydzielony przez obiekt wywołujący, aby otrzymać przekonwertowany ciąg.

*nDestLen*<br/>
Długość w znakach w buforze przydzielonym przez wywołującego.

*flagiDW*<br/>
ATL_ESC flagi opisujące, jak ma zostać wykonana konwersja.

- ATL_ESC_FLAG_NONE zachowanie domyślne. Znaki cudzysłowu i apostrofy nie są konwertowane.
- Znaki cudzysłowu ATL_ESC_FLAG_ATTR i apostrofy są konwertowane `&quot;` na `&apos;` i odpowiednio.

### <a name="return-value"></a>Wartość zwracana

Długość przekonwertowanego ciągu znaków.

### <a name="remarks"></a>Uwagi

W tabeli przedstawiono możliwe konwersje wykonywane przez tę funkcję:

|Source|Miejsce docelowe|
|------------|-----------------|
|\<|&lt;|
|>|&gt;|
|&|&amp;|
|'|&apos;|
|"|&quot;|

## <a name="getextendedchars"></a>GetExtendedChars

Wywołaj tę funkcję, aby uzyskać liczbę znaków rozszerzonych w ciągu.

```
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();
```

### <a name="parameters"></a>Parametry

*szSrc*<br/>
Ciąg do analizy.

*nSrcLen*<br/>
Długość ciągu znaków.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę znaków rozszerzonych znalezionych w ciągu określonym przez [IsExtendedChar](#isextendedchar).

## <a name="isextendedchar"></a>IsExtendedChar

Wywołaj tę funkcję, aby dowiedzieć się, czy dany znak jest znakiem rozszerzonym (mniejszym niż 32, większym niż 126, a nie tabulatorem, znakiem wysuwu wiersza ani returnem)

```
inline int IsExtendedChar(char ch) throw();
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak do przetestowania

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli znak jest rozszerzony, w przeciwnym razie zwraca wartość FALSE.

## <a name="qencode"></a>QEncode

Wywołaj tę funkcję, aby skonwertować dane przy użyciu kodowania „Q”.

```
inline BOOL QEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet,
   int* pnNumEncoded = NULL) throw();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
Bufor zawierający dane, które mają zostać zakodowane.

*nSrcLen*<br/>
Długość w bajtach danych, które mają zostać zakodowane.

*szDest*<br/>
Bufor przydzielony przez obiekt wywołujący, który ma odbierać zakodowane dane.

*pnDestLen*<br/>
Wskaźnik do zmiennej zawierającej długość w znakach *szDest*. Jeśli funkcja się powiedzie, zmienna otrzymuje liczbę znaków zapisywanych w buforze. Jeśli funkcja się nie powiedzie, zmienna otrzymuje wymaganą długość w znakach bufora.

*pszCharSet*<br/>
Zestaw znaków do użycia podczas konwersji.

*pnNumEncoded*<br/>
Wskaźnik do zmiennej, która zwraca, zawiera liczbę niebezpiecznych znaków, które musiały zostać przekonwertowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Schemat kodowania "Q" został opisany w dokumencie RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)).

## <a name="qencodegetrequiredlength"></a>QEncodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.

```
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba bajtów danych do zakodowania.

*nCharsetLen*<br/>
Długość w znakach zestawu znaków, który ma zostać użyty do konwersji.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków wymagana dla buforu, który może przechowywać zakodowane dane z *nSrcLen* bajtów.

### <a name="remarks"></a>Uwagi

Schemat kodowania "Q" został opisany w dokumencie RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)).

## <a name="qpdecode"></a>QPDecode

Dekoduje ciąg danych, który został zakodowany w formacie do drukowania w cudzysłowie, na przykład przez poprzednie wywołanie do [QPEncode](#qpencode).

```
inline BOOL QPDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
podczas Bufor zawierający dane, które mają zostać zdekodowane.

*nSrcLen*<br/>
podczas Długość w bajtach *pbSrcData*.

*szDest*<br/>
określoną Bufor przydzielony przez obiekt wywołujący, który odbiera zdekodowane dane.

*pnDestLen*<br/>
określoną Wskaźnik do zmiennej zawierającej długość w bajtach *szDest*. Jeśli funkcja się powiedzie, zmienna otrzymuje liczbę bajtów zapisywanych w buforze. Jeśli funkcja się nie powiedzie, zmienna otrzymuje wymaganą długość w bajtach buforu.

*flagiDW*<br/>
podczas ATLSMTP_QPENCODE flagi opisujące, jak ma zostać wykonana konwersja.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Schemat kodowania do drukowania w cudzysłowach został opisany w dokumencie RFC 2045[https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)().

## <a name="qpdecodegetrequiredlength"></a>QPDecodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego w quoted-printable o określonej długości.

```
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba znaków w zakodowanym ciągu.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów wymagana dla buforu, który może zawierać zdekodowany ciąg znaków *nSrcLen* .

### <a name="remarks"></a>Uwagi

Schemat kodowania do drukowania w cudzysłowach został opisany w dokumencie RFC 2045[https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)().

## <a name="qpencode"></a>QPEncode

Wywołaj tę funkcję, aby zakodować dane w formacie quoted-printable.

```
inline BOOL QPEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
Bufor zawierający dane, które mają zostać zakodowane.

*nSrcLen*<br/>
Długość w bajtach danych, które mają zostać zakodowane.

*szDest*<br/>
Bufor przydzielony przez obiekt wywołujący, który ma odbierać zakodowane dane.

*pnDestLen*<br/>
Wskaźnik do zmiennej zawierającej długość w znakach *szDest*. Jeśli funkcja się powiedzie, zmienna otrzymuje liczbę znaków zapisywanych w buforze. Jeśli funkcja się nie powiedzie, zmienna otrzymuje wymaganą długość w znakach bufora.

*flagiDW*<br/>
ATLSMTP_QPENCODE flagi opisujące, jak ma zostać wykonana konwersja.

- ATLSMTP_QPENCODE_DOT Jeśli kropka pojawia się na początku wiersza, jest dodawana do danych wyjściowych, a także kodowanych.

- ATLSMTP_QPENCODE_TRAILING_SOFT dołącza `=\r\n` do zakodowanego ciągu.

Schemat kodowania do drukowania w cudzysłowach został opisany w [dokumencie RFC 2045](https://www.ietf.org/rfc/rfc2045.txt).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Schemat kodowania do drukowania w cudzysłowach został opisany w dokumencie RFC 2045[https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)().

## <a name="qpencodegetrequiredlength"></a>QPEncodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.

```
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba bajtów danych do zakodowania.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków wymagana dla buforu, który może przechowywać zakodowane dane z *nSrcLen* bajtów.

### <a name="remarks"></a>Uwagi

Schemat kodowania do drukowania w cudzysłowach został opisany w dokumencie RFC 2045[https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)().

## <a name="uudecode"></a>UUDecode

Dekoduje ciąg danych, który został wystawiony na przykład przez poprzednie wywołanie do [UUENCODE](#uuencode).

```
inline BOOL UUDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   BYTE* pbDest,
   int* pnDestLen) throw ();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
Ciąg zawierający dane, które mają zostać zdekodowane.

*nSrcLen*<br/>
Długość w bajtach *pbSrcData*.

*pbDest*<br/>
Bufor przydzielony przez obiekt wywołujący, który odbiera zdekodowane dane.

*pnDestLen*<br/>
Wskaźnik do zmiennej zawierającej długość w bajtach *pbDest*. Jeśli funkcja się powiedzie, zmienna otrzymuje liczbę bajtów zapisywanych w buforze. Jeśli funkcja się nie powiedzie, zmienna otrzymuje wymaganą długość w bajtach buforu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Ta implementacja uuencoding jest zgodna ze specyfikacją POSIX P 1003.2 b/D11.

## <a name="uudecodegetrequiredlength"></a>UUDecodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego w uuencode o określonej długości.

```
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba znaków w zakodowanym ciągu.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów wymagana dla buforu, który może zawierać zdekodowany ciąg znaków *nSrcLen* .

### <a name="remarks"></a>Uwagi

Ta implementacja uuencoding jest zgodna ze specyfikacją POSIX P 1003.2 b/D11.

## <a name="uuencode"></a>UUEncode

Wywołaj tę funkcję, aby zakodować dane w uuencode.

```
inline BOOL UUEncode(
   const BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCTSTR lpszFile = _T("file"),
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
Bufor zawierający dane, które mają zostać zakodowane.

*nSrcLen*<br/>
Długość w bajtach danych, które mają zostać zakodowane.

*szDest*<br/>
Bufor przydzielony przez obiekt wywołujący, który ma odbierać zakodowane dane.

*pnDestLen*<br/>
Wskaźnik do zmiennej zawierającej długość w znakach *szDest*. Jeśli funkcja się powiedzie, zmienna otrzymuje liczbę znaków zapisywanych w buforze. Jeśli funkcja się nie powiedzie, zmienna otrzymuje wymaganą długość w znakach bufora.

*lpszFile*<br/>
Plik, który ma zostać dodany do nagłówka, gdy ATLSMTP_UUENCODE_HEADER jest określony w *flagiDW*.

*flagiDW*<br/>
Flagi kontrolujące zachowanie tej funkcji.

- ATLSMTP_UUENCODE_HEADE nagłówek zostanie zakodowany.

- ATLSMTP_UUENCODE_END końcowy zostanie zakodowany.

- ATLSMTP_UUENCODE_DOT dane zostaną wykonane.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Ta implementacja uuencoding jest zgodna ze specyfikacją POSIX P 1003.2 b/D11.

## <a name="uuencodegetrequiredlength"></a>UUEncodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.

```
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba bajtów danych do zakodowania.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków wymagana dla buforu, który może przechowywać zakodowane dane z *nSrcLen* bajtów.

### <a name="remarks"></a>Uwagi

Ta implementacja uuencoding jest zgodna ze specyfikacją POSIX P 1003.2 b/D11.

## <a name="see-also"></a>Zobacz także

[Pojęcia](../active-template-library-atl-concepts.md)<br/>
[Składniki ATL COM pulpitu](../atl-com-desktop-components.md)
