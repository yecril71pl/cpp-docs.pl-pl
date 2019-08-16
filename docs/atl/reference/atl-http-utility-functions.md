---
title: Funkcje narzędziowe HTTP ATL
ms.date: 11/04/2016
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
ms.openlocfilehash: ca6dfdfb02f5ef629c6eb523744260f177a3309b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497975"
---
# <a name="atl-http-utility-functions"></a>Funkcje narzędziowe HTTP ATL

Te funkcje obsługują manipulowanie adresami URL.

|||
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes adres URL, który obejmuje konwertowanie niebezpiecznych znaków i spacji na sekwencje unikowe.|
|[AtlCombineUrl](#atlcombineurl)|Łączy podstawowy adres URL i względny adres URL w postaci pojedynczego, kanonicznego adresu URL.|
|[AtlEscapeUrl](#atlescapeurl)|Konwertuje wszystkie niebezpieczne znaki na sekwencje ucieczki.|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|Pobiera domyślny numer portu skojarzony z określonym protokołem lub schematem internetowym.|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|Określa, czy znak jest bezpieczny do użycia w adresie URL.|
|[AtlUnescapeUrl](#atlunescapeurl)|Konwertuje znaki ucieczki z powrotem na oryginalne wartości.|
|[RGBToHtml](#rgbtohtml)|Konwertuje wartość [COLORREF](/windows/win32/gdi/colorref) na tekst HTML odpowiadający tej wartości koloru.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|Wywołaj tę funkcję, aby skonwertować czas systemowy na ciąg znaków w formacie odpowiednim do używania nagłówków HTTP.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil. h

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
Adres URL, który ma być kanoniczny.

*szCanonicalized*<br/>
Bufor przydzielony przez obiekt wywołujący w celu otrzymania kanonicznego adresu URL.

*pdwMaxLength*<br/>
Wskaźnik do zmiennej zawierającej długość w znakach *szCanonicalized*. Jeśli funkcja się powiedzie, zmienna otrzymuje liczbę znaków zapisywanych w buforze, w tym kończący znak null. Jeśli funkcja się nie powiedzie, zmienna otrzymuje wymaganą długość w bajtach bufora, w tym miejsce dla kończącego znaku null.

*flagiDW*<br/>
Flagi ATL_URL kontrolujące zachowanie tej funkcji.

- ATL_URL_BROWSER_MODE nie koduje ani nie dekoduje znaków po "#" lub "?" i nie usuwa końcowej spacji po "?". Jeśli ta wartość nie jest określona, cały adres URL jest zakodowany, a końcowy biały znak jest usuwany.

- ATL_URL_DECODE konwertuje wszystkie sekwencje% XX na znaki, w tym sekwencje ucieczki, przed przeanalizowanie adresu URL.

- ATL_URL_ENCODE_PERCENT koduje wszelkie napotkane znaki procentu. Domyślnie znaki procentowe nie są zakodowane.

- ATL_URL_ENCODE_SPACES_ONLY koduje tylko spacje.

- ATL_URL_ESCAPE konwertuje wszystkie sekwencje ucieczki (% XX) na odpowiadające im znaki.

- ATL_URL_NO_ENCODE nie konwertuje niebezpiecznych znaków na sekwencje ucieczki.

- ATL_URL_NO_META nie usuwa z adresu URL meta sekwencji (takich jak "." i "..").

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Zachowuje się jak w przypadku bieżącej wersji programu [InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw) , ale nie wymaga zainstalowania interfejsu WinINet ani programu Internet Explorer.

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
Adres URL względny dla podstawowego adresu URL.

*szBuffer*<br/>
Bufor przydzielony przez obiekt wywołujący w celu otrzymania kanonicznego adresu URL.

*pdwMaxLength*<br/>
Wskaźnik do zmiennej zawierającej długość w znakach *szBuffer*. Jeśli funkcja się powiedzie, zmienna otrzymuje liczbę znaków zapisywanych w buforze, w tym kończący znak null. Jeśli funkcja się nie powiedzie, zmienna otrzymuje wymaganą długość w bajtach bufora, w tym miejsce dla kończącego znaku null.

*flagiDW*<br/>
Flagi kontrolujące zachowanie tej funkcji. Zobacz [AtlCanonicalizeUrl](#atlcanonicalizeurl).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Zachowuje się jak w przypadku bieżącej wersji programu [InternetCombineUrl](/windows/win32/api/wininet/nf-wininet-internetcombineurlw) , ale nie wymaga zainstalowania interfejsu WinINet ani programu Internet Explorer.

## <a name="atlescapeurl"></a>AtlEscapeUrl

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
Adres URL do przekonwertowania.

*lpszStringOut*<br/>
Bufor przydzielony przez obiekt wywołujący, do którego zostanie zapisany przekonwertowany adres URL.

*pdwStrLen*<br/>
Wskaźnik na zmienną typu DWORD. Jeśli funkcja się powiedzie, *pdwStrLen* odbiera liczbę znaków zapisywanych w buforze, w tym kończący znak null. Jeśli funkcja się nie powiedzie, zmienna otrzymuje wymaganą długość w bajtach bufora, w tym miejsce dla kończącego znaku null. W przypadku korzystania z wersji o szerokim znaku tej metody *pdwStrLen* odbiera wymaganą liczbę znaków, a nie liczbę bajtów.

*dwMaxLength*<br/>
Rozmiar buforu *lpszStringOut*.

*flagiDW*<br/>
Flagi ATL_URL kontrolujące zachowanie tej funkcji. Zobacz [ATLCanonicalizeUrl](#atlcanonicalizeurl) , aby uzyskać możliwe wartości.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

## <a name="atlgetdefaulturlport"></a>AtlGetDefaultUrlPort

Wywołaj tę funkcję, aby uzyskać domyślny numer portu skojarzony z określonym protokołem lub schematem internetowym.

```
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();
```

### <a name="parameters"></a>Parametry

*m_nScheme*<br/>
Wartość [ATL_URL_SCHEME](atl-url-scheme-enum.md) identyfikująca schemat, dla którego chcesz uzyskać numer portu.

### <a name="return-value"></a>Wartość zwracana

[ATL_URL_PORT](atl-typedefs.md#atl_url_port) skojarzona z określonym schematem lub ATL_URL_INVALID_PORT_NUMBER, jeśli nie został rozpoznany schemat.

## <a name="atlisunsafeurlchar"></a>AtlIsUnsafeUrlChar

Wywołaj tę funkcję, aby się dowiedzieć, czy użycie danego znaku w adresie URL jest bezpieczne.

```
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();
```

### <a name="parameters"></a>Parametry

*chIn*<br/>
Znak, który ma być testowany pod kątem bezpieczeństwa.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli znak wejściowy jest niebezpieczny, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Znaki, które nie powinny być używane w adresach URL, mogą być testowane przy użyciu tej funkcji i konwertowane przy użyciu [AtlCanonicalizeUrl](#atlcanonicalizeurl).

## <a name="atlunescapeurl"></a>AtlUnescapeUrl

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
Adres URL do przekonwertowania.

*lpszStringOut*<br/>
Bufor przydzielony przez obiekt wywołujący, do którego zostanie zapisany przekonwertowany adres URL.

*pdwStrLen*<br/>
Wskaźnik na zmienną typu DWORD. Jeśli funkcja się powiedzie, zmienna otrzymuje liczbę znaków zapisywanych w buforze, w tym kończący znak null. Jeśli funkcja się nie powiedzie, zmienna otrzymuje wymaganą długość w bajtach bufora, w tym miejsce dla kończącego znaku null.

*dwMaxLength*<br/>
Rozmiar buforu *lpszStringOut*.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Odwraca proces konwersji stosowany przez [AtlEscapeUrl](#atlescapeurl).

## <a name="rgbtohtml"></a> RGBToHtml

Konwertuje wartość [COLORREF](/windows/win32/gdi/colorref) na tekst HTML odpowiadający tej wartości koloru.

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
Bufor przydzielony przez obiekt wywołujący, aby otrzymać tekst wartości koloru HTML. W buforze musi znajdować się spacja co najmniej 8 znaków, w tym miejsce dla terminatora o wartości null.

*nBuffer*<br/>
Rozmiar w bajtach buforu (łącznie z miejscem dla terminatora o wartości null).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Wartość koloru HTML jest znakiem krzyżyka, po którym następuje 6-cyfrowa wartość szesnastkowa, przy użyciu 2 cyfr dla każdego czerwonego, zielonego i niebieskiego składnika koloru (na przykład #FFFFFF jest biały).

## <a name="systemtimetohttpdate"></a> SystemTimeToHttpDate

Wywołaj tę funkcję, aby skonwertować czas systemowy na ciąg znaków w formacie odpowiednim do używania nagłówków HTTP.

```cpp
inline void SystemTimeToHttpDate(
   const SYSTEMTIME& st,
   CStringA& strTime);
```

### <a name="parameters"></a>Parametry

*krótkoterminow*<br/>
Czas systemowy, który ma zostać uzyskany jako ciąg formatu HTTP.

*strTime*<br/>
Odwołanie do zmiennej ciągu, aby otrzymać datę i godzinę http zgodnie z definicją w dokumencie RFC[https://www.ietf.org/rfc/rfc2616.txt](https://www.ietf.org/rfc/rfc2616.txt)2616 () i RFC[https://www.ietf.org/rfc/rfc1123.txt](https://www.ietf.org/rfc/rfc1123.txt)1123 ().

## <a name="see-also"></a>Zobacz także

[Pojęcia](../active-template-library-atl-concepts.md)<br/>
[Składniki ATL COM pulpitu](../atl-com-desktop-components.md)<br/>
[InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw)
