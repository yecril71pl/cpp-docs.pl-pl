---
title: "memcpy, wmemcpy — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- memcpy
- wmemcpy
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- wmemcpy
- memcpy
dev_langs: C++
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 38c00e7d7c5eb9f4a1076ae3814c17a8062fe322
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="memcpy-wmemcpy"></a>memcpy, wmemcpy
Kopie bajty pomiędzy buforów. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [memcpy_s —, wmemcpy_s —](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
void *memcpy(  
   void *dest,  
   const void *src,  
   size_t count   
);  
wchar_t *wmemcpy(  
   wchar_t *dest,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dest`  
 Bufor nowego.  
  
 `src`  
 Bufor do skopiowania.  
  
 `count`  
 Liczba znaków do skopiowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość `dest`.  
  
## <a name="remarks"></a>Uwagi  
 `memcpy`kopie `count` bajtów z `src` do `dest`; `wmemcpy` kopie `count` znaki dwubajtowe (dwa bajty). Jeśli na źródłowym i docelowym nakładają się, zachowanie `memcpy` jest niezdefiniowana. Użyj `memmove` do obsługi pokrywających się obszarów.  
  
> [!IMPORTANT]
>  Upewnij się, że bufor docelowy jest taki sam lub większy rozmiar niż bufor źródłowy. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
> [!IMPORTANT]
>  Ponieważ tyle przepełnienia buforu, a w związku z tym potencjalnych luk zabezpieczeń, mieć śledzone do niewłaściwe użycie `memcpy`, ta funkcja jest na liście "zabronione" funkcje przez Security Development Lifecycle (SDL).  Można zauważyć, że niektóre klasy biblioteki VC ++ w dalszym ciągu używać `memcpy`.  Ponadto można zauważyć, że optymalizator kompilatora VC ++ czasami emituje wywołania `memcpy`.  Produkt Visual C++ został utworzony zgodnie z procesem cyklu projektowania zabezpieczeń i w związku z tym użycie tej funkcji zabronione ściśle oszacowano.  W przypadku biblioteki z niej korzystać, wywołań ma dokładnie kontroli aby upewnić się, że przepełnienia buforu nie będzie można za pomocą tych wywołań.  W przypadku kompilatora, czasami pewnych wzorców kodu są rozpoznawane jako identyczne struktury `memcpy`i w związku z tym są zamieniane na wywołanie funkcji.  W takich przypadkach użycia `memcpy` jest niebezpieczne ma więcej niż oryginalna byłby instrukcje; ich po prostu zostały zoptymalizowane do wywołania wydajność dostosowana `memcpy` funkcji.  Podobnie jak użycie "bezpiecznej" funkcje CRT nie gwarantuje bezpieczeństwa (one tylko utrudnić jako niebezpieczny) Użyj funkcji "zabronione" nie gwarantuje zagrożenia (tylko potrzebują większej kontroli w celu zapewnienia bezpieczeństwa).  
>   
>  Ponieważ `memcpy` więc uważnie kontroli użycia VC ++ kompilatora i bibliotek, te wywołania są dozwolone w przeciwnym razie jest zgodne z SDL kodem.  `memcpy`wywołania wprowadzone w kodzie źródłowym aplikacji są zgodne z SDL tylko w przypadku, gdy używające zostały poddane analizie przez ekspertów zabezpieczeń.  
  
 `memcpy` i `wmemcpy` funkcje zostaną wycofane tylko, jeśli stała `_CRT_SECURE_DEPRECATE_MEMORY` jest zdefiniowana przed instrukcji włączenia w kolejności dla funkcji wycofane, takich jak pokazano w przykładzie poniżej:  
  
```  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <memory.h>  
```  
  
 lub  
  
```  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <wchar.h>  
```  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`memcpy`|\<Memory.h > lub \<string.h >|  
|`wmemcpy`|\<WChar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz [memmove —](../../c-runtime-library/reference/memmove-wmemmove.md) przykładowy sposób użycia `memcpy`.  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie buforem](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy —](../../c-runtime-library/reference/memccpy.md)   
 [memchr, wmemchr —](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [funkcji memcmp, wmemcmp —](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memmove —, wmemmove —](../../c-runtime-library/reference/memmove-wmemmove.md)   
 [memset —, wmemset —](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcpy_s —, wcscpy_s —, _mbscpy_s —](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)   
 [strncpy_s — _strncpy_s_l —, wcsncpy_s —, _wcsncpy_s_l —, _mbsncpy_s, _mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)