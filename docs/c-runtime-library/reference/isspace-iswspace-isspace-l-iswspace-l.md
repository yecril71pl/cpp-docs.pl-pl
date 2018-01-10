---
title: "isspace —, iswspace —, _isspace_l —, _iswspace_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- iswspace
- _isspace_l
- _iswspace_l
- isspace
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
- iswspace
- _istspace
- isspace
dev_langs: C++
helpviewer_keywords:
- iswspace function
- isspace function
- _iswspace_l function
- _isspace_l function
- iswspace_l function
- isspace_l function
- _istspace function
- istspace function
ms.assetid: b851e0c0-36bb-4dac-a1a3-533540939035
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 618ba621f385307d3609667c6df5cf56c91da2f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="isspace-iswspace-isspacel-iswspacel"></a>isspace, iswspace, _isspace_l, _iswspace_l
Określa, czy liczba całkowita reprezentuje znak odstępu.  
  
## <a name="syntax"></a>Składnia  
  
```  
int isspace(  
   int c   
);  
int iswspace(  
   wint_t c   
);  
int _isspace_l(  
   int c,  
   _locale_t locale  
);  
int _iswspace_l(  
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
 Każdy z tych procedur zwraca różną od zera, jeśli `c` jest reprezentację określonego znaku spacji. `isspace`Zwraca wartość niezerową, jeśli `c` jest biały znak (0x09-0x0D lub 0x20). Wynik testu warunku `isspace` zależy od funkcji `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, które nie mają `_l` sufiks użyciem bieżących ustawień regionalnych wszystkie działania zależne od ustawień regionalnych; wersje, które mają `_l` sufiks są identyczne, z wyjątkiem tego, aby były używane ustawienia regionalne, który jest przekazywany w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 `iswspace`Zwraca wartość niezerową, jeśli `c` jest znaków dwubajtowych, umożliwiająca standardowe biały znak.  
  
 Zachowanie `isspace` i `_isspace_l` jest niezdefiniowana, jeśli `c` nie jest EOF lub w zakresie od 0 do 0xFF włącznie. Gdy zostanie użyty bibliotek debugowania CRT i `c` nie jest jedną z tych wartości, zgłoś funkcje potwierdzenia.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|**_** `istspace`|`isspace`|[_ismbcspace —](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswspace`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`isspace`|\<CType.h >|  
|`iswspace`|\<CType.h > lub \<wchar.h >|  
|`_isspace_l`|\<CType.h >|  
|`_iswspace_l`|\<CType.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja znaków](../../c-runtime-library/character-classification.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [is, isw, procedury](../../c-runtime-library/is-isw-routines.md)