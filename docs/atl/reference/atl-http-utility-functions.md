---
title: Funkcje pomocnicze protokołu HTTP ATL
ms.date: 11/04/2016
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
ms.openlocfilehash: be38dc8b8547574ea47021f8b14f21060a0755f0
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849651"
---
# <a name="atl-http-utility-functions"></a>Funkcje pomocnicze protokołu HTTP ATL

Funkcje te obsługują manipulowania adresów URL.

|||
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes adresu URL, co obejmuje konwersję niebezpiecznych znaków i spacji na sekwencje unikowe.|
|[AtlCombineUrl](#atlcombineurl)|Scala podstawowy adres URL i względny adres URL w jeden Kanoniczny adres URL.|
|[AtlEscapeUrl](#atlescapeurl)|Konwertuje wszystkie niebezpieczne znaki na sekwencje ucieczki.|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|Pobiera domyślny numer portu skojarzony z określonym protokołem lub schematem internetowym.|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|Określa, czy znak jest bezpieczny dla adresu URL.|
|[AtlUnescapeUrl](#atlunescapeurl)|Konwertuje poprzedzone znakiem zmiany znaczenia znaków do ich oryginalnych wartości.|
|[RGBToHtml](#rgbtohtml)|Konwertuje [COLORREF](/windows/desktop/gdi/colorref) wartość na tekst HTML odpowiadający wartości tego koloru.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|Wywołaj tę funkcję, aby skonwertować czas systemowy na ciąg znaków w formacie odpowiednim do używania nagłówków HTTP.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="atlcanonicalizeurl"></a> AtlCanonicalizeUrl

Wywołaj tę funkcję, aby nadać postać kanoniczną adresowi URL, co obejmuje konwersję niebezpiecznych znaków i spacji na sekwencje unikowe.

```cpp
inline BOOL AtlCanonicalizeUrl(
   LPCTSTR szUrl,
   LPTSTR szCanonicalized,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*szUrl*<br/>
Adres URL, aby zostać skanonikalizowana.

*szCanonicalized*<br/>
Przydzielonej przez obiekt wywołujący bufor odbioru adres URL w postaci kanonicznej.

*pdwMaxLength*<br/>
Wskaźnik do zmiennej, która zawiera długość w znakach *szCanonicalized*. Jeśli funkcja się powiedzie, zmienna odbiera liczbę znaków zapisanych w buforze, w tym kończącego znaku null. Jeśli funkcja zawiedzie, zmienna odbiera wymaganą długość w bajtach rozmiar buforu, co obejmuje miejsce w przypadku końcowego znaku null.

*dwFlags*<br/>
Flagi ATL_URL sterowania zachowaniem tej funkcji.

- Nie ATL_URL_BROWSER_MODE kodowania lub dekodowania znaków po "#" lub "?", a nie powoduje usunięcia odstępu po "?". Jeśli ta wartość nie jest określona, cały adres URL jest zaszyfrowana i końcowe biały znak zostanie usunięta.

- ATL_URL_DECODE konwertuje wszystkie % XX sekwencje znaków, w tym sekwencje ucieczki, aby adres URL jest analizowany.

- Wszystkie znaki procentu koduje ATL_URL_ENCODE_PERCENT napotkał. Domyślnie nie są kodowane procentu.

- Koduje ATL_URL_ENCODE_SPACES_ONLY tylko spacje.

- Konwertuje ATL_URL_ESCAPE wszystkie sekwencje (% XX) escape, aby ich odpowiadające im znaki.

- ATL_URL_NO_ENCODE nie konwertuje niebezpieczne znaki na sekwencje ucieczki.

- ATL_URL_NO_META nie usuwa meta sekwencji (takie jak "."i"..") z adresu URL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Zachowuje się jak bieżąca wersja [InternetCanonicalizeUrl](/windows/desktop/api/wininet/nf-wininet-internetcanonicalizeurla) , ale nie wymaga WinInet lub Internet Explorer do zainstalowania.

## <a name="atlcombineurl"></a> AtlCombineUrl

Wywołaj tę funkcję, aby połączyć podstawowy adres URL i względny adres URL w jeden kanoniczny adres URL.

```cpp
inline BOOL AtlCombineUrl(
   LPCTSTR szBaseUrl,
   LPCTSTR szRelativeUrl,
   LPTSTR szBuffer,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*szBaseUrl*<br/>
Podstawowy adres URL.

*szRelativeUrl*<br/>
Adres URL, względem podstawowego adresu URL.

*szBuffer*<br/>
Przydzielonej przez obiekt wywołujący bufor odbioru adres URL w postaci kanonicznej.

*pdwMaxLength*<br/>
Wskaźnik do zmiennej, która zawiera długość w znakach *szBuffer*. Jeśli funkcja się powiedzie, zmienna odbiera liczbę znaków zapisanych w buforze, w tym kończącego znaku null. Jeśli funkcja zawiedzie, zmienna odbiera wymaganą długość w bajtach rozmiar buforu, co obejmuje miejsce w przypadku końcowego znaku null.

*dwFlags*<br/>
Flagi sterujące zachowaniem tej funkcji. Zobacz [AtlCanonicalizeUrl](#atlcanonicalizeurl).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Zachowuje się jak bieżąca wersja [InternetCombineUrl](/windows/desktop/api/wininet/nf-wininet-internetcombineurla) , ale nie wymaga WinInet lub Internet Explorer do zainstalowania.

## <a name="atlescapeurl"></a> AtlEscapeUrl

Wywołaj tę funkcję, aby skonwertować wszystkie niebezpieczne znaki na sekwencje ucieczki.

```cpp
inline BOOL AtlEscapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();

inline BOOL AtlEscapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*lpszStringIn*<br/>
Adres URL, który ma zostać przekonwertowany.

*lpszStringOut*<br/>
Bufor przydzielonej przez obiekt wywołujący, do której zostanie zapisany przekonwertowanego adresu URL.

*pdwStrLen*<br/>
Wskaźnik do zmiennej typu DWORD. Jeśli funkcja się powiedzie, *pdwStrLen* odbiera liczbę znaków zapisanych w buforze, w tym kończącego znaku null. Jeśli funkcja zawiedzie, zmienna odbiera wymaganą długość w bajtach rozmiar buforu, co obejmuje miejsce w przypadku końcowego znaku null. Korzystając z wersją znaków dwubajtowych tej metody *pdwStrLen* odbiera wymaganą liczbę znaków, nie liczbę bajtów.

*dwMaxLength*<br/>
Rozmiar buforu *lpszStringOut*.

*dwFlags*<br/>
Flagi ATL_URL sterowania zachowaniem tej funkcji. Zobacz [ATLCanonicalizeUrl](#atlcanonicalizeurl) uzyskać odpowiednie wartości.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

## <a name="atlgetdefaulturlport"></a> AtlGetDefaultUrlPort

Wywołaj tę funkcję, aby uzyskać domyślny numer portu skojarzony z określonym protokołem lub schematem internetowym.

```
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();
```

### <a name="parameters"></a>Parametry

*m_nScheme*<br/>
[ATL_URL_SCHEME](atl-url-scheme-enum.md) wartość identyfikowanie schemat, dla którego chcesz uzyskać numer portu.

### <a name="return-value"></a>Wartość zwracana

[ATL_URL_PORT](atl-typedefs.md#atl_url_port) skojarzone z określonego schematu lub ATL_URL_INVALID_PORT_NUMBER, jeśli schemat nie został rozpoznany.

## <a name="atlisunsafeurlchar"></a> AtlIsUnsafeUrlChar

Wywołaj tę funkcję, aby się dowiedzieć, czy użycie danego znaku w adresie URL jest bezpieczne.

```
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();
```

### <a name="parameters"></a>Parametry

*chIn*<br/>
Znak, który ma zostać przetestowana pod kątem bezpieczeństwa.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli wprowadzanych znaków jest niebezpieczne, wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Znaki, które nie powinny być używane w adresach URL mogą być testowane przy użyciu tej funkcji i konwertowane przy użyciu [AtlCanonicalizeUrl](#atlcanonicalizeurl).

## <a name="atlunescapeurl"></a> AtlUnescapeUrl

Wywołaj tę funkcję, aby skonwertować znaki przetworzone przez sekwencje ucieczki z powrotem do ich oryginalnych wartości.

```cpp
inline BOOL AtlUnescapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();

inline BOOL AtlUnescapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();
```

### <a name="parameters"></a>Parametry

*lpszStringIn*<br/>
Adres URL, który ma zostać przekonwertowany.

*lpszStringOut*<br/>
Bufor przydzielonej przez obiekt wywołujący, do której zostanie zapisany przekonwertowanego adresu URL.

*pdwStrLen*<br/>
Wskaźnik do zmiennej typu DWORD. Jeśli funkcja się powiedzie, zmienna odbiera liczbę znaków zapisanych w buforze, w tym kończącego znaku null. Jeśli funkcja zawiedzie, zmienna odbiera wymaganą długość w bajtach rozmiar buforu, co obejmuje miejsce w przypadku końcowego znaku null.

*dwMaxLength*<br/>
Rozmiar buforu *lpszStringOut*.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Odwraca proces konwersji stosowane przez [AtlEscapeUrl](#atlescapeurl).

## <a name="rgbtohtml"></a> RGBToHtml

Konwertuje [COLORREF](/windows/desktop/gdi/colorref) wartość na tekst HTML odpowiadający wartości tego koloru.

```cpp
bool inline RGBToHtml(
   COLORREF color,
   LPTSTR pbOut,
   long nBuffer);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
Wartość koloru RGB.

*pbOut*<br/>
Bufor przydzielonej przez obiekt wywołujący, aby otrzymać tekst HTML wartość koloru. Rozmiar buforu musi mieć miejsca dla co najmniej 8 znaków, w tym miejsce terminator o wartości null).

*nBuffer*<br/>
Rozmiar w bajtach rozmiar buforu (w tym miejsce terminator o wartości null).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wartość koloru HTML jest znak #, a następnie wartość szesnastkową 6-cyfrowy przy użyciu cyfr 2 dla poszczególnych składników czerwonego, zielonego i niebieskiego koloru (na przykład białe jest #FFFFFF).

## <a name="systemtimetohttpdate"></a> SystemTimeToHttpDate

Wywołaj tę funkcję, aby skonwertować czas systemowy na ciąg znaków w formacie odpowiednim do używania nagłówków HTTP.

```cpp
inline void SystemTimeToHttpDate(
   const SYSTEMTIME& st,
   CStringA& strTime);
```

### <a name="parameters"></a>Parametry

*st*<br/>
Czas systemowy, które mają zostać uzyskane w postaci ciągu formatu HTTP.

*strTime*<br/>
Odwołanie do zmiennej ciągu, aby otrzymać HTTP Data i godzina, zgodnie z definicją w dokumencie RFC 2616 ([http://www.ietf.org/rfc/rfc2616.txt](http://www.ietf.org/rfc/rfc2616.txt)) i RFC 1123 ([http://www.ietf.org/rfc/rfc1123.txt](http://www.ietf.org/rfc/rfc1123.txt)).

## <a name="see-also"></a>Zobacz też

[Pojęcia](../active-template-library-atl-concepts.md)<br/>
[Składniki ATL COM pulpitu](../atl-com-desktop-components.md)<br/>
[InternetCanonicalizeUrl](/windows/desktop/api/wininet/nf-wininet-internetcanonicalizeurla)
