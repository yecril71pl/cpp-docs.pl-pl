---
title: vfscanf, vfwscanf | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- vfwscanf
- vfscanf
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
- vfwscanf
- _vftscanf
- vfscanf
dev_langs: C++
ms.assetid: c06450ef-03f1-4d24-a8ac-d2dd98847918
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8abe9916aa7b64663edcf05a400dd5cb0107c482
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="vfscanf-vfwscanf"></a>vfscanf, vfwscanf
Odczyty sformatowanych danych ze strumienia. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [vfscanf_s, vfwscanf_s](../../c-runtime-library/reference/vfscanf-s-vfwscanf-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
int vfscanf(   
   FILE *stream,  
   const char *format,  
   va_list argptr   
);  
int vfwscanf(   
   FILE *stream,  
   const wchar_t *format,  
   va_list argptr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
 `format`  
 Ciąg kontroli formatu.  
  
 `arglist`  
 Listy zmiennych argumentów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca liczbę pól, które pomyślnie przekonwertowany i przypisane; wartość zwrotna nie zawiera pola, które są do odczytu, ale nie są przypisane. Wartość zwracana 0 wskazuje, że nie ma pól zostały przypisane. Jeśli wystąpi błąd, lub czy osiągnięto koniec strumienia pliku przed pierwszym konwersji, jest zwracana wartość `EOF` dla `vfscanf` i `vfwscanf`.  
  
 Te funkcje walidację ich parametrów. Jeśli `stream` lub `format` wskaźnika o wartości null, jest program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `EOF` i ustaw `errno` do `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 `vfscanf` Funkcja odczytuje dane z bieżącej pozycji `stream` w lokalizacjach, które są podane przez `arglist` listy argumentów. Każdy argument na liście musi być wskaźnikiem do zmiennej typu, który odpowiada specyfikatorowi typu w `format`. `format`Formanty interpretacji dane wejściowe pola i ma tę samą tworzą i działać jako `format` argument `scanf`; zobacz [scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) opis `format`.  
  
 `vfwscanf`jest to wersja znaków dwubajtowych `vfscanf`; argument formatu `vfwscanf` jest ciągiem znaków dwubajtowych. Te funkcje zachowują się tak samo tak samo, jakby strumień jest otwarty w trybie ANSI. `vfscanf`nie obsługuje dane wejściowe ze strumienia UNICODE.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vftscanf`|`vfscanf`|`vfscanf`|`vfwscanf`|  
  
 Aby uzyskać więcej informacji, zobacz [pola specyfikacji formatu: funkcji wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`vfscanf`|\<stdio.h >|  
|`vfwscanf`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_vfscanf.c  
// compile with: /W3  
// This program writes formatted  
// data to a file. It then uses vfscanf to  
// read the various data back from the file.  
  
#include <stdio.h>  
#include <stdarg.h>  
  
FILE *stream;  
  
int call_vfscanf(FILE * istream, char * format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vfscanf(istream, format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main(void)  
{  
    long l;  
    float fp;  
    char s[81];  
    char c;  
  
    if (fopen_s(&stream, "vfscanf.out", "w+") != 0)  
    {  
        printf("The file vfscanf.out was not opened\n");  
    }  
    else  
    {  
        fprintf(stream, "%s %ld %f%c", "a-string",  
            65000, 3.14159, 'x');  
        // Security caution!  
        // Beware loading data from a file without confirming its size,  
        // as it may lead to a buffer overrun situation.  
  
        // Set pointer to beginning of file:  
        fseek(stream, 0L, SEEK_SET);  
  
        // Read data back from file:  
        call_vfscanf(stream, "%s %ld %f%c", s, &l, &fp, &c);  
  
        // Output data read:   
        printf("%s\n", s);  
        printf("%ld\n", l);  
        printf("%f\n", fp);  
        printf("%c\n", c);  
  
        fclose(stream);  
    }  
}  
  
```  
  
```Output  
a-string  
65000  
3.141590  
x  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [_cscanf —, _cscanf_l —, _cwscanf — _cwscanf_l —](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf —, _fprintf_l —, fwprintf — _fwprintf_l —](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [scanf, _scanf_l —, wscanf — _wscanf_l —](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf —, _sscanf_l —, swscanf — _swscanf_l —](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [fscanf_s —, _fscanf_s_l —, fwscanf_s — _fwscanf_s_l —](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)   
 [vfscanf_s, vfwscanf_s](../../c-runtime-library/reference/vfscanf-s-vfwscanf-s.md)