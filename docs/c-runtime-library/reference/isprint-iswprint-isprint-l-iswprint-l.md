---
title: "isprint —, iswprint —, _isprint_l —, _iswprint_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- iswprint
- isprint
- _isprint_l
- _iswprint_l
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- iswprint
- _istprint
- isprint
dev_langs:
- C++
helpviewer_keywords:
- _istprint function
- iswprint function
- _iswprint_l function
- isprint_l function
- istprint function
- isprint function
- iswprint_l function
- _isprint_l function
ms.assetid: a8bbcdb0-e8d0-4d8c-ae4e-56d3bdee6ca3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 36d4c6fcc699392f32a45dfff6131a3b7b7e66ad
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="isprint-iswprint-isprintl-iswprintl"></a>isprint, iswprint, _isprint_l, _iswprint_l
Określa, czy liczba całkowita reprezentuje znaków drukowalnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
int isprint(  
   int c   
);  
int iswprint(  
   wint_t c   
);  
int _isprint_l(  
   int c,  
   _locale_t locale  
);  
int _iswprint_l(  
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Liczba całkowita do testowania.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każdy z tych procedur zwraca różną od zera, jeśli `c` jest reprezentację określonego obiektu znaków drukowalnych. `isprint` Zwraca wartość niezerową, jeśli `c` jest znaków drukowalnych — dotyczy to również znak spacji (0x20 - 0x7E). `iswprint` Zwraca wartość niezerową, jeśli `c` jest drukowalnych znaków dwubajtowych — dotyczy to również miejsce szerokość znaku. Każdy z tych procedur zwraca 0, jeśli `c` nie spełnia warunku.  
  
 Wynik warunku dla tych funkcji zależy od `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, które nie mają `_l` sufiks użyciem bieżących ustawień regionalnych wszystkie działania zależne od ustawień regionalnych; wersje, które mają `_l` sufiks są identyczne, z wyjątkiem tego, aby były używane ustawienia regionalne, który jest przekazywany w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Zachowanie `isprint` i `_isprint_l` jest niezdefiniowana, jeśli `c` nie jest EOF lub w zakresie od 0 do 0xFF włącznie. Gdy zostanie użyty bibliotek debugowania CRT i `c` nie jest jedną z tych wartości, zgłoś funkcje potwierdzenia.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_unicode — definicja|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|**_** `istprint`|`isprint`|[_ismbcprint](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswprint`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`isprint`|\<ctype.h>|  
|`iswprint`|\<CType.h > lub \<wchar.h >|  
|`_isprint_l`|\<ctype.h>|  
|`_iswprint_l`|\<CType.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja znaków](../../c-runtime-library/character-classification.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [is, isw, procedury](../../c-runtime-library/is-isw-routines.md)