---
title: "Mapowania zwykłego tekstu w pliku Tchar.h | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 405e95e9eb8fb760e2688e164178cf9270f31877
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="generic-text-mappings-in-tcharh"></a>Mapowania typ ogólny-tekst w pliku Tchar.h
Aby uprościć transportowania kodu do użytku międzynarodowego [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] zapewnia biblioteki czasu wykonywania [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)]-określonego mapowania zwykłego tekstu dla wielu typów danych, procedury i innych obiektów. Można użyć tych mapowania, które są zdefiniowane w pliku Tchar.h do pisania kodu ogólnego, który może zostać skompilowany dla jednobajtowe, wielobajtowe, lub [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] znak zestawów, w zależności od manifestu stałą, której można zdefiniować przy użyciu `#define` instrukcji. Mapowania zwykłego tekstu są [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] rozszerzeń, które nie są [!INCLUDE[vcpransi](../atl-mfc-shared/reference/includes/vcpransi_md.md)] zgodne.  
  
 Przy użyciu Tchar.h, można tworzyć jednobajtowe, wielobajtowe znak Ustaw (MBCS), i [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] aplikacji z tego samego źródła. Tchar.h definiuje makra (które mają prefiks `_tcs`), który z prawidłowe definicje preprocesora, mapowanie na `str`, `_mbs`, lub `wcs` funkcje, zależnie od potrzeb. Aby utworzyć MBCS, zdefiniuj symbol `_MBCS`. Aby utworzyć [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)], zdefiniuj symbol `_UNICODE`. Aby utworzyć aplikację jednobajtowe, zdefiniuj ani (ustawienie domyślne). Domyślnie `_MBCS` jest zdefiniowany dla aplikacji MFC.  
  
 `_TCHAR` Warunkowo zdefiniowany typ danych w pliku Tchar.h. Jeśli symbolu `_UNICODE` jest zdefiniowany dla kompilacji, `_TCHAR` jest zdefiniowany jako `wchar_t`; w przeciwnym razie jednobajtowe i MBCS kompilacji jest zdefiniowany jako `char`. (`wchar_t`, podstawowy typ danych znaków dwubajtowych Unicode jest odpowiednikiem 16-bitowych do 8-bitowej podpisanej `char`.) Aplikacje międzynarodowe, można użyć `_tcs` rodziny funkcji, które działają w `_TCHAR` jednostki, nie w bajtach. Na przykład `_tcsncpy` kopie `n` `_TCHARs`, a nie `n` bajtów.  
  
 Ponieważ podjęcia (ze znakiem) funkcje obsługi ciągów niektórych pojedynczy bajt znak Ustaw (SBCS) `char*` parametrów, wyników ostrzeżenia kompilatora niezgodność typów podczas `_MBCS` jest zdefiniowany. Istnieją trzy sposoby, aby uniknąć tego ostrzeżenia:  
  
1.  Użyj osadzeń funkcja bezpieczny wbudowany w pliku Tchar.h. Jest to zachowanie domyślne.  
  
2.  Użyj makra bezpośrednio w pliku Tchar.h, definiując `_MB_MAP_DIRECT` w wierszu polecenia. Jeśli to zrobisz, musisz ręcznie dopasować typów. To jest najszybszy sposób, ale nie jest bezpieczne.  
  
3.  Użyj osadzeń funkcja bezpieczny statycznie połączone biblioteki w pliku Tchar.h. Aby to zrobić, należy zdefiniować stała `_NO_INLINING` w wierszu polecenia. Jest to metoda najwolniejsze, ale najbardziej bezpieczne.  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>Dyrektywy preprocesora do mapowania zwykłego tekstu  
  
|Zdefiniuj #|Skompilowanej wersji|Przykład|  
|---------------|----------------------|-------------|  
|`_UNICODE`|[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)](znaków dwubajtowych)|`_tcsrev`mapuje`_wcsrev`|  
|`_MBCS`|Znaków wielobajtowych|`_tcsrev`mapuje`_mbsrev`|  
|Brak (domyślnie nie ma `_UNICODE` ani `_MBCS` zdefiniowana)|SBCS ([!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)])|`_tcsrev`mapuje`strrev`|  
  
 Na przykład funkcja zwykłego tekstu `_tcsrev`, która jest zdefiniowana w pliku Tchar.h, mapuje `_mbsrev` Jeśli zdefiniowano `_MBCS` w programie lub do `_wcsrev` Jeśli zdefiniowano `_UNICODE`. W przeciwnym razie `_tcsrev` mapuje `strrev`. Inne mapowanie typu danych znajdują się w pliku Tchar.h w celu ułatwienia programowania, ale `_TCHAR` jest najbardziej przydatna.  
  
### <a name="generic-text-data-type-mappings"></a>Mapowanie typu danych — zwykły tekst  
  
|Zwykły tekst<br /><br /> Nazwa typu danych|_UNICODE — &<br /><br /> Nie zdefiniowano _MBCS|_MBCS<br /><br /> Definicja|_UNICODE —<br /><br /> Definicja|  
|--------------------------------------|----------------------------------------|------------------------|---------------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`unsigned int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T`lub`_TEXT`|Żadnego skutku (usuwane przez preprocesora)|Żadnego skutku (usuwane przez preprocesora)|`L`(konwertuje następujący znak lub ciąg do jego [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] odpowiednikiem)|  
  
 Aby uzyskać listę mapowania zwykłego tekstu, procedury, zmienne i inne obiekty, zobacz [mapowania zwykłego tekstu](../c-runtime-library/generic-text-mappings.md) w odwołaniu biblioteki czasu wykonywania.  
  
> [!NOTE]
>  Nie używaj `str` rodziny funkcji z ciągów Unicode, które mogą zawierać osadzonych bajty zerowe. Podobnie, nie używaj `wcs` rodziny funkcji z ciągami MBCS (lub SBCS).  
  
 Poniższe fragmenty kodu przedstawiają stosowania `_TCHAR` i `_tcsrev` do mapowania do MBCS, [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]i SBCS modeli.  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 Jeśli `_MBCS` została zdefiniowana, preprocesora mapuje ten fragment ten kod:  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 Jeśli `_UNICODE` została zdefiniowana, preprocesora mapuje ten fragment ten kod:  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 Jeśli żadna `_MBCS` ani `_UNICODE` zostały zdefiniowane, preprocesora mapuje fragment jednobajtowe [!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)] kodu, w następujący sposób:  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 W związku z tym można zapisać, obsługa i skompiluj plik kodu źródłowego pojedynczego, aby uruchamiać z procedury, które są specyficzne dla żadnego z trzech rodzajów zestawów znaków.  
  
## <a name="see-also"></a>Zobacz też  
 [Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)   
 [Używanie typów danych TCHAR.H z kodem _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)