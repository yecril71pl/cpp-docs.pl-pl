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
ms.openlocfilehash: 13c521bae6790a030212c4a8edac460c960ecfc0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270835"
---
# <a name="atl-text-encoding-functions"></a>Funkcje kodowania tekstu ATL

Funkcje te obsługują tekstu, kodowania i dekodowania.

|||
|-|-|
|[AtlGetHexValue](#atlgethexvalue)|Wywołaj tę funkcję, aby uzyskać wartość liczbową z liczby szesnastkowej.|
|[AtlGetVersion](#atlgetversion)|Wywołaj tę funkcję, aby pobrać wersję biblioteki ATL, którego używasz.  |
|[AtlHexDecode](#atlhexdecode)|Dekoduje ciąg danych, który został zakodowany jako tekst szesnastkowy, np. przez poprzednie wywołanie [AtlHexEncode](#atlhexencode).|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego szesnastkowo o określonej długości.|
|[AtlHexEncode](#atlhexencode)|Wywołaj tę funkcję, aby zakodować dane jako ciąg tekstu szesnastkowego.|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.|
|[AtlHexValue](#atlhexvalue)|Wywołaj tę funkcję, aby uzyskać wartość liczbową z liczby szesnastkowej. |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|Wywołaj tę funkcję, aby przekonwertować ciąg Unicode na UTF-8. |
|[BEncode](#bencode)|Wywołaj tę funkcję, aby skonwertować dane przy użyciu kodowania „B”.|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.|
|[EscapeXML](#escapexml)|Wywołaj tę funkcję, aby skonwertować znaki niebezpieczne w XML na ich bezpieczne odpowiedniki.|
|[GetExtendedChars](#getextendedchars)|Wywołaj tę funkcję, aby uzyskać liczbę znaków rozszerzonych w ciągu.|
|[IsExtendedChar](#isextendedchar)|Wywołaj tę funkcję, aby się dowiedzieć, czy dany znak to znak rozszerzony (mniej niż 32, więcej niż 126 i nie znak tabulacji, znak nowego wiersza lub znak powrotu karetki)|
|[QEncode](#qencode)|Wywołaj tę funkcję, aby skonwertować dane przy użyciu kodowania „Q”.  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.|
|[QPDecode](#qpdecode)|Dekoduje ciąg danych, który został zakodowany w formacie quoted-printable, np. przez poprzednie wywołanie [QPEncode](#qpencode).|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego w quoted-printable o określonej długości.|
|[QPEncode](#qpencode)|Wywołaj tę funkcję, aby zakodować dane w formacie quoted-printable.|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.|
|[UUDecode](#uudecode)|Dekoduje ciąg danych, który został zakodowany w UUENCODE takich jak przez poprzednie wywołanie [UUEncode](#uuencode).|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego w uuencode o określonej długości.|
|[UUEncode](#uuencode)|Wywołaj tę funkcję, aby zakodować dane w uuencode. |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlenc.h

## <a name="atlgethexvalue"></a> AtlGetHexValue

Wywołaj tę funkcję, aby uzyskać wartość liczbową z liczby szesnastkowej.

```
inline char AtlGetHexValue(char chIn) throw();
```

### <a name="parameters"></a>Parametry

*chIn*<br/>
Znaków szesnastkowych "0" – "9", "A"-"F", lub od 'a'-'f'.

### <a name="return-value"></a>Wartość zwracana

Wartość liczbowa wprowadzanych znaków, które są interpretowane jako cyfry szesnastkowej. Na przykład dane wejściowe "0" zwraca wartość 0, a dane wejściowe "A" zwraca wartość 10. Jeśli znak wejściowy nie jest cyfrą szesnastkową, ta funkcja zwraca wartość -1.

## <a name="atlgetversion"></a> AtlGetVersion

Wywołaj tę funkcję, aby pobrać wersję biblioteki ATL, którego używasz.

```
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);
```

### <a name="parameters"></a>Parametry

*pReserved*<br/>
Wskaźnik zastrzeżone.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość całkowitą typu DWORD wersji biblioteki ATL, które podczas kompilowania lub.

## <a name="example"></a>Przykład

Funkcja powinna być wywoływana w następujący sposób.

[!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="atlhexdecode"></a> AtlHexDecode

Dekoduje ciąg danych, który został zakodowany jako tekst szesnastkowy, np. przez poprzednie wywołanie [AtlHexEncode](#atlhexencode).

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
Przydzielonej przez obiekt wywołujący bufor odbioru dekodowane dane.

*pnDestLen*<br/>
Wskaźnik do zmiennej, która zawiera długość w bajtach *pbDest*. Jeśli funkcja się powiedzie, zmienna odbiera liczba bajtów zapisanych w buforze. Jeśli funkcja zawiedzie, zmienna odbiera wymaganą długość w bajtach rozmiar buforu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

## <a name="atlhexdecodegetrequiredlength"></a> AtlHexDecodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego szesnastkowo o określonej długości.

```
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba znaków w ciąg zakodowany.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów potrzebnych dla buforu, który może przechowywać Dekodowany ciąg *nSrcLen* znaków.

## <a name="atlhexencode"></a> AtlHexEncode

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
Bufor zawierający dane do zakodowania.

*nSrcLen*<br/>
Długość w bajtach danych do zakodowania.

*szDest*<br/>
Przydzielonej przez obiekt wywołujący bufor odbioru dane zakodowane.

*pnDestLen*<br/>
Wskaźnik do zmiennej, która zawiera długość w znakach *szDest*. Jeśli funkcja się powiedzie, zmienna odbiera liczbę znaków zapisanych w buforze. Jeśli funkcja zawiedzie, zmienna odbiera wymaganą długość w znakach buforu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Poszczególne bajty dane źródłowe są kodowane jako 2 znaków szesnastkowych.

## <a name="atlhexencodegetrequiredlength"></a> AtlHexEncodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.

```
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba bajtów danych do zakodowania.

### <a name="return-value"></a>Wartość zwracana

Liczbę znaków wymaganą dla buforu, który może przechowywać dane zakodowane z *nSrcLen* bajtów.

## <a name="atlhexvalue"></a> AtlHexValue

Wywołaj tę funkcję, aby uzyskać wartość liczbową z liczby szesnastkowej.

```
inline short AtlHexValue(char chIn) throw();
```

### <a name="parameters"></a>Parametry

*chIn*<br/>
Znaków szesnastkowych "0" – "9", "A"-"F", lub od 'a'-'f'.

### <a name="return-value"></a>Wartość zwracana

Wartość liczbowa wprowadzanych znaków, które są interpretowane jako cyfry szesnastkowej. Na przykład dane wejściowe "0" zwraca wartość 0, a dane wejściowe "A" zwraca wartość 10. Jeśli znak wejściowy nie jest cyfrą szesnastkową, ta funkcja zwraca wartość -1.

## <a name="atlunicodetoutf8"></a> AtlUnicodeToUTF8

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
Ciąg Unicode, który ma zostać przekonwertowany

*nSrc*<br/>
Długość w znakach ciąg Unicode.

*szDest*<br/>
Przydzielonej przez obiekt wywołujący bufor odbioru przekonwertowany ciąg.

*nDest*<br/>
Długość w bajtach rozmiar buforu.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę znaków w ciągu przekonwertowanego.

### <a name="remarks"></a>Uwagi

Aby określić rozmiar buforu wymaganych do ciągu przekonwertowanego, należy wywołać tę funkcję, przekazując 0 *szDest* i *nDest*.

## <a name="bencode"></a> BEncode

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
Bufor zawierający dane do zakodowania.

*nSrcLen*<br/>
Długość w bajtach danych do zakodowania.

*szDest*<br/>
Przydzielonej przez obiekt wywołujący bufor odbioru dane zakodowane.

*pnDestLen*<br/>
Wskaźnik do zmiennej, która zawiera długość w znakach *szDest*. Jeśli funkcja się powiedzie, zmienna odbiera liczbę znaków zapisanych w buforze. Jeśli funkcja zawiedzie, zmienna odbiera wymaganą długość w znakach buforu.

*pszCharSet*<br/>
Zestaw znaków na potrzeby konwersji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Schemat kodowania "B" jest opisana w dokumencie RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).

## <a name="bencodegetrequiredlength"></a> BEncodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.

```
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba bajtów danych do zakodowania.

*nCharsetLen*<br/>
Długość w znakach zestawu na potrzeby konwersji znaków.

### <a name="return-value"></a>Wartość zwracana

Liczbę znaków wymaganą dla buforu, który może przechowywać dane zakodowane z *nSrcLen* bajtów.

### <a name="remarks"></a>Uwagi

Schemat kodowania "B" jest opisana w dokumencie RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).

## <a name="escapexml"></a> EscapeXML

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
Ciąg, który ma zostać przekonwertowany.

*nSrclen*<br/>
Długość w znakach ciąg do konwersji.

*szEsc*<br/>
Przydzielonej przez obiekt wywołujący bufor odbioru przekonwertowany ciąg.

*nDestLen*<br/>
Długość w znakach buforu przydzielonej przez obiekt wywołujący.

*dwFlags*<br/>
Flagi ATL_ESC opisujące, jak ma być wykonywane konwersji.

- ATL_ESC_FLAG_NONE domyślne zachowanie. Cudzysłów znaków i apostrofy nie są przekształcane.
- Znaki cudzysłowu ATL_ESC_FLAG_ATTR apostrofów i są konwertowane na `&quot;` i `&apos;` odpowiednio.

### <a name="return-value"></a>Wartość zwracana

Długość w znakach przekonwertowanego ciągu.

### <a name="remarks"></a>Uwagi

W tabeli przedstawiono możliwe konwersje wykonywane przez tę funkcję:

|Źródło|Miejsce docelowe|
|------------|-----------------|
|\<|&lt;|
|>|&gt;|
|&|&amp;|
|'|&apos;|
|"|&quot;|

## <a name="getextendedchars"></a> GetExtendedChars

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

Zwraca liczbę znaków rozszerzonych, można znaleźć w ciągu zgodnie z ustaleniami [IsExtendedChar](#isextendedchar).

## <a name="isextendedchar"></a> IsExtendedChar

Wywołaj tę funkcję, aby się dowiedzieć, czy dany znak to znak rozszerzony (mniej niż 32, więcej niż 126 i nie znak tabulacji, znak nowego wiersza lub znak powrotu karetki)

```
inline int IsExtendedChar(char ch) throw();
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak do zbadania

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli znak zostanie przedłużony, wartość FALSE w przeciwnym razie.

## <a name="qencode"></a> QEncode

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
Bufor zawierający dane do zakodowania.

*nSrcLen*<br/>
Długość w bajtach danych do zakodowania.

*szDest*<br/>
Przydzielonej przez obiekt wywołujący bufor odbioru dane zakodowane.

*pnDestLen*<br/>
Wskaźnik do zmiennej, która zawiera długość w znakach *szDest*. Jeśli funkcja się powiedzie, zmienna odbiera liczbę znaków zapisanych w buforze. Jeśli funkcja zawiedzie, zmienna odbiera wymaganą długość w znakach buforu.

*pszCharSet*<br/>
Zestaw znaków na potrzeby konwersji.

*pnNumEncoded*<br/>
Wskaźnik do zmiennej, która zawiera liczbę niebezpiecznych znaków, w których ma zostać przekonwertowany na zwrot.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Schemat kodowania "Q" jest opisana w dokumencie RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).

## <a name="qencodegetrequiredlength"></a> QEncodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.

```
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba bajtów danych do zakodowania.

*nCharsetLen*<br/>
Długość w znakach zestawu na potrzeby konwersji znaków.

### <a name="return-value"></a>Wartość zwracana

Liczbę znaków wymaganą dla buforu, który może przechowywać dane zakodowane z *nSrcLen* bajtów.

### <a name="remarks"></a>Uwagi

Schemat kodowania "Q" jest opisana w dokumencie RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).

## <a name="qpdecode"></a> QPDecode

Dekoduje ciąg danych, który został zakodowany w formacie quoted-printable, np. przez poprzednie wywołanie [QPEncode](#qpencode).

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
[in] Bufor zawierające dane, które mają zostać zdekodowane.

*nSrcLen*<br/>
[in] Długość w bajtach *pbSrcData*.

*szDest*<br/>
[out] Przydzielonej przez obiekt wywołujący bufor odbioru dekodowane dane.

*pnDestLen*<br/>
[out] Wskaźnik do zmiennej, która zawiera długość w bajtach *szDest*. Jeśli funkcja się powiedzie, zmienna odbiera liczba bajtów zapisanych w buforze. Jeśli funkcja zawiedzie, zmienna odbiera wymaganą długość w bajtach rozmiar buforu.

*dwFlags*<br/>
[in] Flagi ATLSMTP_QPENCODE opisujące, jak ma być wykonywane konwersji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Quoted-printable schemat kodowania jest opisana w dokumencie RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).

## <a name="qpdecodegetrequiredlength"></a> QPDecodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego w quoted-printable o określonej długości.

```
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba znaków w ciąg zakodowany.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów potrzebnych dla buforu, który może przechowywać Dekodowany ciąg *nSrcLen* znaków.

### <a name="remarks"></a>Uwagi

Quoted-printable schemat kodowania jest opisana w dokumencie RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).

## <a name="qpencode"></a> QPEncode

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
Bufor zawierający dane do zakodowania.

*nSrcLen*<br/>
Długość w bajtach danych do zakodowania.

*szDest*<br/>
Przydzielonej przez obiekt wywołujący bufor odbioru dane zakodowane.

*pnDestLen*<br/>
Wskaźnik do zmiennej, która zawiera długość w znakach *szDest*. Jeśli funkcja się powiedzie, zmienna odbiera liczbę znaków zapisanych w buforze. Jeśli funkcja zawiedzie, zmienna odbiera wymaganą długość w znakach buforu.

*dwFlags*<br/>
Flagi ATLSMTP_QPENCODE opisujące, jak ma być wykonywane konwersji.

- ATLSMTP_QPENCODE_DOT Jeśli okres pojawia się na początku wiersza, jego jest dodawane do wyników, a także zakodowany.

- Dołącza ATLSMTP_QPENCODE_TRAILING_SOFT `=\r\n` ciąg zakodowany.

Opisano w quoted-printable schemat kodowania [RFC 2045](http://www.ietf.org/rfc/rfc2045.txt).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Quoted-printable schemat kodowania jest opisana w dokumencie RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).

## <a name="qpencodegetrequiredlength"></a> QPEncodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.

```
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba bajtów danych do zakodowania.

### <a name="return-value"></a>Wartość zwracana

Liczbę znaków wymaganą dla buforu, który może przechowywać dane zakodowane z *nSrcLen* bajtów.

### <a name="remarks"></a>Uwagi

Quoted-printable schemat kodowania jest opisana w dokumencie RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).

## <a name="uudecode"></a> UUDecode

Dekoduje ciąg danych, który został zakodowany w UUENCODE takich jak przez poprzednie wywołanie [UUEncode](#uuencode).

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
Przydzielonej przez obiekt wywołujący bufor odbioru dekodowane dane.

*pnDestLen*<br/>
Wskaźnik do zmiennej, która zawiera długość w bajtach *pbDest*. Jeśli funkcja się powiedzie, zmienna odbiera liczba bajtów zapisanych w buforze. Jeśli funkcja zawiedzie, zmienna odbiera wymaganą długość w bajtach rozmiar buforu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta implementacja uuencoding zgodna ze specyfikacją modelu POSIX P1003.2b/D11.

## <a name="uudecodegetrequiredlength"></a> UUDecodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego w uuencode o określonej długości.

```
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba znaków w ciąg zakodowany.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów potrzebnych dla buforu, który może przechowywać Dekodowany ciąg *nSrcLen* znaków.

### <a name="remarks"></a>Uwagi

Ta implementacja uuencoding zgodna ze specyfikacją modelu POSIX P1003.2b/D11.

## <a name="uuencode"></a> UUEncode

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
Bufor zawierający dane do zakodowania.

*nSrcLen*<br/>
Długość w bajtach danych do zakodowania.

*szDest*<br/>
Przydzielonej przez obiekt wywołujący bufor odbioru dane zakodowane.

*pnDestLen*<br/>
Wskaźnik do zmiennej, która zawiera długość w znakach *szDest*. Jeśli funkcja się powiedzie, zmienna odbiera liczbę znaków zapisanych w buforze. Jeśli funkcja zawiedzie, zmienna odbiera wymaganą długość w znakach buforu.

*lpszFile*<br/>
Plik, który ma zostać dodany do nagłówka, gdy ATLSMTP_UUENCODE_HEADER jest określona w *Flagidw*.

*dwFlags*<br/>
Flagi sterujące zachowaniem tej funkcji.

- ATLSMTP_UUENCODE_HEADE nagłówek będzie zakodowany.

- ATLSMTP_UUENCODE_END koniec będzie zakodowany.

- Wypychania danych ATLSMTP_UUENCODE_DOT zostaną wykonane.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta implementacja uuencoding zgodna ze specyfikacją modelu POSIX P1003.2b/D11.

## <a name="uuencodegetrequiredlength"></a> UUEncodeGetRequiredLength

Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości.

```
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Liczba bajtów danych do zakodowania.

### <a name="return-value"></a>Wartość zwracana

Liczbę znaków wymaganą dla buforu, który może przechowywać dane zakodowane z *nSrcLen* bajtów.

### <a name="remarks"></a>Uwagi

Ta implementacja uuencoding zgodna ze specyfikacją modelu POSIX P1003.2b/D11.

## <a name="see-also"></a>Zobacz także

[Pojęcia](../active-template-library-atl-concepts.md)<br/>
[Składniki ATL COM pulpitu](../atl-com-desktop-components.md)
