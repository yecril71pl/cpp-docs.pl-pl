---
title: "Mapowania zwykłego tekstu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _UNICODE
dev_langs:
- C++
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- _UNICODE constant
- TXCHAR type
- generic-text mappings
- _TSCHAR type
- T type
- mappings, generic-text
- _TUCHAR type
- MBCS data type
- _MBCS data type
- _TEXT type
- UNICODE constant
- _T type
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d0049643ef7a3695eef8c3271e22586b5c7454d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-generic-text-mappings"></a>Mapowania zwykłego tekstu
**Dotyczące firmy Microsoft**  
  
 Aby ułatwić projektowanie kodu dla różnych międzynarodową, biblioteki wykonawczej firmy Microsoft zapewnia mapowania "zwykłego tekstu" specyficzne dla firmy Microsoft wiele typów danych, procedury i innych obiektów. Te mapowania są definiowane w tchar —. H. Te mapowania nazw służy do pisania kodu ogólnego, który może zostać skompilowany dla każdego z trzech typów zestawów znaków: ASCII (SBCS), MBCS lub Unicode, w zależności od stałą manifestu, można zdefiniować przy użyciu `#define` instrukcji. Mapowania zwykłego tekstu są rozszerzenia Microsoft, które nie są zgodne ANSI.  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>Dyrektywy preprocesora do mapowania zwykłego tekstu  
  
|#define|Skompilowanej wersji|Przykład|  
|--------------|----------------------|-------------|  
|`_UNICODE`|Unicode (znaków dwubajtowych)|`_tcsrev`mapuje`_wcsrev`|  
|`_MBCS`|Znaków wielobajtowych|`_tcsrev`mapuje`_mbsrev`|  
|Brak (wartość domyślna: ani `_UNICODE` ani `_MBCS` zdefiniowana)|SBCS (ASCII)|`_tcsrev`mapuje`strrev`|  
  
 Na przykład funkcja zwykłego tekstu `_tcsrev`zdefiniowanej w tchar —. Mapuje H, `mbsrev` Jeśli `MBCS` został zdefiniowany w programie lub do `_wcsrev` Jeśli `_UNICODE` została zdefiniowana. W przeciwnym razie `_tcsrev` mapuje `strrev`.  
  
 Typ danych — zwykły tekst `_TCHAR`również zdefiniowanej w tchar —. Mapuje H, wpisz `char` Jeśli `_MBCS` jest zdefiniowana na typ `wchar_t` Jeśli `_UNICODE` jest zdefiniowany i wpisz `char` Jeśli żadna stała jest zdefiniowany. Mapowania typ innych danych znajdują się w tchar —. H w celu ułatwienia programowania, ale `_TCHAR` jest typem, który jest najbardziej przydatna.  
  
### <a name="generic-text-data-type-mappings"></a>Mapowanie typu danych — zwykły tekst  
  
|Nazwa typu danych — zwykły tekst|SBCS (_unicode —, _MBCS nie jest zdefiniowana)|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|----------------------------------|--------------------------------------------|--------------------|-----------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T`lub`_TEXT`|Żadnego skutku (usuwane przez preprocesora)|Żadnego skutku (usuwane przez preprocesora)|`L`(konwertuje zgodnie z jego odpowiednikiem Unicode znak lub ciąg)|  
  
 Aby uzyskać pełną listę mapowania zwykłego tekstu, procedury, zmienne i inne obiekty, zobacz [mapowania zwykłego tekstu](../c-runtime-library/generic-text-mappings.md).  
  
 Poniższe fragmenty kodu przedstawiają stosowania `_TCHAR` i `_tcsrev` mapowania do MBCS, Unicode i SBCS modeli.  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 Jeśli `MBCS` została zdefiniowana, preprocesora mapuje poprzedniego fragmentu poniższy kod:  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 Jeśli `_UNICODE` została zdefiniowana, preprocesora mapuje tego samego fragmentu poniższy kod:  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 Jeśli żadna `_MBCS` ani `_UNICODE` została zdefiniowana, preprocesora mapuje fragment kodu ASCII jednobajtowe, w następujący sposób:  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 W związku z tym można pisać, obsługa i skompiluj plik kodu jednego źródła, aby uruchomić z procedury, które są specyficzne dla żadnego z trzech rodzajów zestawów znaków.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowania zwykłego tekstu](../c-runtime-library/generic-text-mappings.md)   
 [Mapowanie typu danych](../c-runtime-library/data-type-mappings.md)   
 [Mapowania zmiennych globalnych i stałych](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [Mapowanie procedur](../c-runtime-library/routine-mappings.md)   
 [Przykładowy ogólny program tekstowy](../c-runtime-library/a-sample-generic-text-program.md)