---
title: Funkcje pomocnicze ATL HTTP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 476ca29de5a44e8ebb20d53ec0b88834c7b03eea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="atl-http-utility-functions"></a>Funkcje pomocnicze HTTP ATL

Te funkcje obsługuje manipulowania adresów URL.

|||  
|-|-|  
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes adresu URL, który zawiera przekształcania znaki niebezpieczne i spacje w sekwencji ucieczki.|  
|[AtlCombineUrl](#atlcombineurl)|Łączy podstawowego adresu URL i względnym adresem URL w jednej, kanonicznej adresu URL.|  
|[AtlEscapeUrl](#atlescapeurl)|Konwertuje wszystkie znaki niebezpieczny sekwencji ucieczki.|  
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|Pobiera domyślny numer portu skojarzonego z konkretnym protokołu internetowego lub schemat.|  
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|Określa, czy znak jest bezpieczna do użycia w adresie URL.|  
|[AtlUnescapeUrl](#atlunescapeurl)|Konwertuje wyjściowym znaków do ich oryginalnych wartości.|  
|[RGBToHtml](#rgbtohtml)|Konwertuje [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość odpowiadającą tej wartości koloru tekstu w formacie HTML.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|Wywołaj tę funkcję, aby skonwertować czas systemowy na ciąg znaków w formacie odpowiednim do używania nagłówków HTTP.|

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlutil.h  

## <a name="atlcanonicalizeurl"></a> AtlCanonicalizeUrl
Wywołaj tę funkcję, aby nadać postać kanoniczną adresowi URL, co obejmuje konwersję niebezpiecznych znaków i spacji na sekwencje unikowe.  
  
```    
inline BOOL AtlCanonicalizeUrl(  
   LPCTSTR szUrl,  
   LPTSTR szCanonicalized,  
   DWORD* pdwMaxLength,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `szUrl`  
 Adres URL, który można w postaci kanonicznej.  
  
 `szCanonicalized`  
 Przydzielone przez obiekt wywołujący bufor odbioru adres URL w postaci kanonicznej.  
  
 `pdwMaxLength`  
 Wskaźnik do zmiennej, która zawiera długość w znakach `szCanonicalized`. Jeśli funkcja zakończy się powodzeniem, zmienna odbiera liczba znaków, zapisać w buforze, w tym znak końcowy null. W przypadku niepowodzenia funkcji zmiennej odbiera wymaganą długość w bajtach buforu, łącznie z miejsca na znak końcowy null.  
  
 `dwFlags`  
 ATL_URL flagi sterujące zachowaniem tej funkcji. 

- `ATL_URL_BROWSER_MODE` Nie kodowania i dekodowania znaków po "#" lub "?", a nie powoduje usunięcia końcu spację po "?". Jeśli ta wartość nie jest określona, cały adres URL jest zakodowany i usunięciu wiodących znaków odstępu.
- `ATL_URL_DECODE` Konwertuje wszystkie sekwencje XX % znaków, w tym sekwencji unikowych przed analizowania adresu URL.
- `ATL_URL_ENCODE_PERCENT` Koduje wszelkie znaki procentu napotkano. Domyślnie nie są kodowane procentu.
- `ATL_URL_ENCODE_SPACES_ONLY` Koduje tylko spacje.
- `ATL_URL_ESCAPE` Konwertuje wszystkie sekwencje unikowe (% XX) do ich odpowiednich znaków.
- `ATL_URL_NO_ENCODE` Nie konwertuje sekwencje specjalne znaków niebezpieczne.
- `ATL_URL_NO_META` Nie powoduje usunięcia meta sekwencje (takich jak "."i"..") z adresu URL. 
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Zachowuje się jak bieżąca wersja [InternetCanonicalizeUrl](http://msdn.microsoft.com/library/windows/desktop/aa384342) , ale nie wymaga WinInet lub program Internet Explorer do zainstalowania.  
  
### <a name="see-also"></a>Zobacz też  
 [InternetCanonicalizeUrl](http://msdn.microsoft.com/library/windows/desktop/aa384342)

 ## <a name="atlcombineurl"></a> AtlCombineUrl
 Wywołaj tę funkcję, aby połączyć podstawowy adres URL i względny adres URL w jeden kanoniczny adres URL.  
  
```    
inline BOOL AtlCombineUrl(  
   LPCTSTR szBaseUrl,  
   LPCTSTR szRelativeUrl,  
   LPTSTR szBuffer,  
   DWORD* pdwMaxLength,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *szBaseUrl*  
 Podstawowy adres URL.  
  
 *szRelativeUrl*  
 Adres URL względem podstawowego adresu URL.  
  
 `szBuffer`  
 Przydzielone przez obiekt wywołujący bufor odbioru adres URL w postaci kanonicznej.  
  
 `pdwMaxLength`  
 Wskaźnik do zmiennej, która zawiera długość w znakach `szBuffer`. Jeśli funkcja zakończy się powodzeniem, zmienna odbiera liczba znaków, zapisać w buforze, w tym znak końcowy null. W przypadku niepowodzenia funkcji zmiennej odbiera wymaganą długość w bajtach buforu, łącznie z miejsca na znak końcowy null.  
  
 `dwFlags`  
 Flagi sterujące zachowaniem tej funkcji. Zobacz [AtlCanonicalizeUrl](#atlcanonicalizeurl).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Zachowuje się jak bieżąca wersja [InternetCombineUrl](http://msdn.microsoft.com/library/windows/desktop/aa384355) , ale nie wymaga WinInet lub program Internet Explorer do zainstalowania.  
  
## <a name="atlescapeurl"></a> AtlEscapeUrl
 Wywołaj tę funkcję, aby skonwertować wszystkie niebezpieczne znaki na sekwencje ucieczki.  
  
```    
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
 `lpszStringIn`  
 Adres URL do skonwertowania.  
  
 `lpszStringOut`  
 Bufor przydzielone przez obiekt wywołujący, do której zostanie zapisany przekonwertowanego adresu URL.  
  
 `pdwStrLen`  
 Wskaźnik do zmiennej typu DWORD. Jeśli funkcja zakończy się powodzeniem, `pdwStrLen` odbiera liczba znaków, zapisać w buforze, w tym znak końcowy null. W przypadku niepowodzenia funkcji zmiennej odbiera wymaganą długość w bajtach buforu, łącznie z miejsca na znak końcowy null. Podczas używania wersji znaków typu wide tej metody `pdwStrLen` odbiera wymagana liczba znaków, nie liczba bajtów.  
  
 `dwMaxLength`  
 Rozmiar buforu `lpszStringOut`.  
  
 `dwFlags`  
 ATL_URL flagi sterujące zachowaniem tej funkcji. Zobacz [ATLCanonicalizeUrl](#atlcanonicalizeurl) prawidłowych wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
## <a name="atlgetdefaulturlport"></a> 
 Wywołaj tę funkcję, aby uzyskać domyślny numer portu skojarzony z określonym protokołem lub schematem internetowym.  
  
```  
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *m_nScheme*  
 [ATL_URL_SCHEME](atl-url-scheme-enum.md) wartość identyfikowanie schemat, dla którego chcesz uzyskać numer portu.  
  
### <a name="return-value"></a>Wartość zwracana  
 [ATL_URL_PORT](atl-typedefs.md#atl_url_port) skojarzonych z określony schemat lub ATL_URL_INVALID_PORT_NUMBER, jeśli schemat nie został rozpoznany.  

## <a name="atlisunsafeurlchar"></a> AtlIsUnsafeUrlChar
 Wywołaj tę funkcję, aby się dowiedzieć, czy użycie danego znaku w adresie URL jest bezpieczne.  
  
```  
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `chIn`  
 Znak, który ma być sprawdzane pod kątem bezpieczeństwa.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** gdy wprowadzany znak jest niebezpieczne, **FALSE** inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Znaki, które nie powinny być używane w adresach URL można przetestować przy użyciu tej funkcji i konwertowane przy użyciu [AtlCanonicalizeUrl](#atlcanonicalizeurl).  
  
## <a name="atlunescapeurl"></a> AtlUnescapeUrl
 Wywołaj tę funkcję, aby skonwertować znaki przetworzone przez sekwencje ucieczki z powrotem do ich oryginalnych wartości.  
  
```    
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
 `lpszStringIn`  
 Adres URL do skonwertowania.  
  
 `lpszStringOut`  
 Bufor przydzielone przez obiekt wywołujący, do której zostanie zapisany przekonwertowanego adresu URL.  
  
 `pdwStrLen`  
 Wskaźnik do zmiennej typu DWORD. Jeśli funkcja zakończy się powodzeniem, zmienna odbiera liczba znaków, zapisać w buforze, w tym znak końcowy null. W przypadku niepowodzenia funkcji zmiennej odbiera wymaganą długość w bajtach buforu, łącznie z miejsca na znak końcowy null.  
  
 `dwMaxLength`  
 Rozmiar buforu `lpszStringOut`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Odwraca proces konwersji stosowane przez [AtlEscapeUrl](#atlescapeurl).  
  
## <a name="rgbtohtml"></a> RGBToHtml
Konwertuje [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość odpowiadającą tej wartości koloru tekstu w formacie HTML.  
  
```  
bool inline RGBToHtml(  
   COLORREF color,  
   LPTSTR pbOut,  
   long nBuffer);  
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 Wartości kolorów RGB.  
  
 `pbOut`  
 Przydzielone przez obiekt wywołujący bufor odbioru tekstu dla wartości koloru HTML. Rozmiar buforu musi mieć miejsca na co najmniej 8 znaków, w tym miejsce terminatorem null).  
  
 *nBuffer*  
 Rozmiar w bajtach buforu (w tym miejsce terminatorem null).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wartość koloru HTML jest znakiem, następuje 6-cyfrowy wartość szesnastkowa cyfry 2 dla każdego składnika czerwony, zielonemu i niebieskiemu koloru (na przykład #FFFFFF jest białe).  
  
## <a name="systemtimetohttpdate"></a> SystemTimeToHttpDate
Wywołaj tę funkcję, aby skonwertować czas systemowy na ciąg znaków w formacie odpowiednim do używania nagłówków HTTP.  
  
```  
inline void SystemTimeToHttpDate( 
   const SYSTEMTIME& st,  
   CStringA& strTime);  
```  
  
### <a name="parameters"></a>Parametry  
 `st`  
 Czas systemowy, które mają zostać uzyskane w postaci ciągu formatu HTTP.  
  
 *strTime*  
 Odwołanie do zmiennej ciągu otrzymywać HTTP Data i godzina, zgodnie z definicją w dokumencie RFC 2616 ([http://www.ietf.org/rfc/rfc2616.txt](http://www.ietf.org/rfc/rfc2616.txt)) i RFC 1123 ([http://www.ietf.org/rfc/rfc1123.txt](http://www.ietf.org/rfc/rfc1123.txt)).  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../../atl/active-template-library-atl-concepts.md)   
 [Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)   

