---
title: Mapowania typ ogólny tekst w pliku Tchar.h | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- tchar.h
dev_langs:
- C++
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4fd66a0e2f45def3aa22342ca30eaa64846ebf4c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012013"
---
# <a name="generic-text-mappings-in-tcharh"></a>Mapowania typ ogólny-tekst w pliku Tchar.h
Aby uprościć transport kodu do użytku międzynarodowego [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] zawiera bibliotekę uruchomieniową [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)]-określonego mapowania zwykłego tekstu dla wielu typów danych, procedury i innych obiektów. Możesz użyć tych mapowań, które są zdefiniowane w pliku Tchar.h, aby napisać kod ogólny, który może być kompilowane dla pojedynczych bajtów, wielobajtowego, lub [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] zestawów, w zależności od stała manifestu, który zdefiniujesz przy użyciu znaków `#define` instrukcji. Mapowania zwykłego tekstu są [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] rozszerzeń, które nie są [!INCLUDE[vcpransi](../atl-mfc-shared/reference/includes/vcpransi_md.md)] zgodny.  
  
 Za pomocą Tchar.h, możesz tworzyć jednobajtowych, znaków wielobajtowych Character Set (MBCS), a [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] aplikacji z tego samego źródła. Tchar.h definiuje makra (które mają prefiks `_tcs`), za pomocą prawidłowe definicje preprocesora, mapowanie na `str`, `_mbs`, lub `wcs` funkcje, zgodnie z potrzebami. Aby skompilować MBCS, zdefiniuj symbol `_MBCS`. Tworzenie [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)], zdefiniuj symbol `_UNICODE`. Aby skompilować aplikację jednobajtowych, zdefiniuj ani (ustawienie domyślne). Domyślnie `_MBCS` jest zdefiniowana dla aplikacji MFC.  
  
 `_TCHAR` Typ danych jest zdefiniowany w pliku Tchar.h w warunkowo. Jeśli symbol `_UNICODE` jest zdefiniowany dla kompilacji, `_TCHAR` jest zdefiniowany jako **wchar_t**; w przeciwnym razie jednobajtowe i MBCS kompilacji jest zdefiniowana jako **char**. (**wchar_t**, podstawowy typ danych szerokich znaków Unicode jest odpowiednikiem 16-bitowych do 8-bitowej podpisanej **char**.) Aplikacje międzynarodowe, można użyć `_tcs` rodziny funkcji, które działają w `_TCHAR` jednostek, nie w bajtach. Na przykład `_tcsncpy` kopie `n` `_TCHARs`, a nie `n` bajtów.  
  
 Ponieważ niektóre ciąg jednego bajtu znaków Ustaw (SBCS) — Obsługa funkcji take (z podpisem) `char*` parametrów, typu spowoduje ostrzeżenia kompilatora niezgodność podczas `_MBCS` jest zdefiniowana. Istnieją trzy sposoby, aby uniknąć tego ostrzeżenia:  
  
1.  W pliku Tchar.h, należy użyć sekcje Thunk funkcji bezpiecznego typu wbudowanego. Jest to zachowanie domyślne.  
  
2.  Użyj makra bezpośrednie w pliku Tchar.h, definiując `_MB_MAP_DIRECT` w wierszu polecenia. Jeśli to zrobisz, musisz ręcznie dopasować typów. To najszybszy sposób, ale nie jest bezpieczny.  
  
3.  Użyj sekcje Thunk funkcji bezpiecznego typu statycznie połączoną bibliotekę, w pliku Tchar.h. Aby to zrobić, należy zdefiniować stałą `_NO_INLINING` w wierszu polecenia. Jest to metoda najwolniejsze, ale najbardziej bezpieczny.  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>Dyrektywy preprocesora do mapowania zwykłego tekstu  
  
|Zdefiniuj #|Skompilowanych wersji|Przykład|  
|---------------|----------------------|-------------|  
|`_UNICODE`|[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] (szerokich znaków)|`_tcsrev` Mapuje `_wcsrev`|  
|`_MBCS`|Znak wielobajtowy|`_tcsrev` Mapuje `_mbsrev`|  
|Brak (domyślnie nie ma `_UNICODE` ani `_MBCS` zdefiniowane)|SBCS ([!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)])|`_tcsrev` Mapuje `strrev`|  
  
 Na przykład funkcja generic tekst `_tcsrev`, która została zdefiniowana w Tchar.h, mapy do `_mbsrev` Jeśli zdefiniowano `_MBCS` w programie lub do `_wcsrev` Jeśli zdefiniowano `_UNICODE`. W przeciwnym razie `_tcsrev` mapuje `strrev`. Inne mapowanie typu danych znajdują się w pliku Tchar.h w celu ułatwienia programowania, ale `_TCHAR` jest najbardziej użyteczna.  
  
### <a name="generic-text-data-type-mappings"></a>Mapowanie typu danych — zwykły tekst  
  
|Zwykły tekst<br /><br /> Nazwa typu danych|_UNICODE &AMP;<br /><br /> _MBCS niezdefiniowane|_MBCS<br /><br /> Definicja|_UNICODE<br /><br /> Definicja|  
|--------------------------------------|----------------------------------------|------------------------|---------------------------|  
|`_TCHAR`|**char**|**char**|**wchar_t**|  
|`_TINT`|**int**|**unsigned int**|`wint_t`|  
|`_TSCHAR`|**podpisany char**|**podpisany char**|**wchar_t**|  
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|  
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|  
|`_T` lub `_TEXT`|Żadnego skutku (usuwane przez preprocesor)|Żadnego skutku (usuwane przez preprocesor)|`L` (konwertuje znak lub ciąg do następujących jego [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] odpowiednik)|  
  
 Aby uzyskać listę mapowania typ ogólny tekst procedury, zmienne i innych obiektów, zobacz [mapowania typ ogólny-tekst](../c-runtime-library/generic-text-mappings.md) w odwołaniu biblioteki wykonawczej.  
  
> [!NOTE]
>  Nie używaj `str` rodzinę funkcji z ciągów Unicode, które mogą zawierać osadzonych bajty o wartości null. Podobnie, nie używaj `wcs` rodziny funkcji z ciągami MBCS (lub SBCS).  
  
 Poniższe fragmenty kodu pokazują korzystanie z `_TCHAR` i `_tcsrev` do mapowania do MBCS, [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]i SBCS modeli.  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 Jeśli `_MBCS` została zdefiniowana, preprocesor mapuje ten fragment ten kod:  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 Jeśli `_UNICODE` została zdefiniowana, preprocesor mapuje ten fragment ten kod:  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 Jeśli żadna `_MBCS` ani `_UNICODE` zostały zdefiniowane, preprocesor mapuje fragment jednobajtowe [!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)] kodu w następujący sposób:  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 W związku z tym można napisać, obsługa i skompiluj plik kodu źródłowego dla pojedynczego, do uruchamiania przy użyciu procedur, które są specyficzne dla żadnego z trzech typów zestawów znaków.  
  
## <a name="see-also"></a>Zobacz też  
 [Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)   
 [Używanie typów danych TCHAR.H z kodem _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)