---
title: vfscanf_s, vfwscanf_s | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- vfscanf_s
- vfwscanf_s
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
- vfscanf_s
- vfwscanf_s
- _vftscanf_s
dev_langs: C++
ms.assetid: 9b0133f0-9a18-4581-b24b-3b72683ad432
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c1012a87cd2f5b73818000877216839f881c309c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="vfscanfs-vfwscanfs"></a>vfscanf_s, vfwscanf_s
Odczyty sformatowanych danych ze strumienia. Te wersje vfscanf vfwscanf zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
int vfscanf_s(   
   FILE *stream,  
   const char *format,  
   va_list arglist  
);  
int vfwscanf_s(   
   FILE *stream,  
   const wchar_t *format,  
   va_list arglist  
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
 Każda z tych funkcji zwraca liczbę pól, które pomyślnie przekonwertowany i przypisane; wartość zwrotna nie zawiera pola, które zostały do odczytu, ale nie są przypisane. Wartość zwracana 0 wskazuje, że nie ma pól zostały przypisane. Jeśli wystąpi błąd, lub czy osiągnięto koniec strumienia pliku przed pierwszym konwersji, jest zwracana wartość `EOF` dla `vfscanf_s` i `vfwscanf_s`.  
  
 Te funkcje walidację ich parametrów. Jeśli `stream` wskaźnika nieprawidłowy plik lub `format` jest wskaźnika o wartości null, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `EOF` i ustaw `errno` do `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 `vfscanf_s` Funkcja odczytuje dane z bieżącej pozycji `stream` w lokalizacjach, które są podane przez `arglist` listy argumentów (jeśli istnieje). Każdy argument na liście musi być wskaźnikiem do zmiennej typu, który odpowiada specyfikatorowi typu w `format`. `format`Formanty interpretacji dane wejściowe pola i ma tę samą tworzą i działać jako `format` argument `scanf_s`; zobacz [pola specyfikacji formatu: funkcji wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md) opis `format`. `vfwscanf_s`jest to wersja znaków dwubajtowych `vfscanf_s`; argument formatu `vfwscanf_s` jest ciągiem znaków dwubajtowych. Te funkcje zachowują się tak samo, jakby strumień jest otwarty w trybie ANSI. `vfscanf_s`obecnie nie obsługuje dane wejściowe ze strumienia UNICODE.  
  
 Główną różnicą między bardziej bezpieczne funkcje (które mają `_s` sufiks) i innych wersji jest, że bezpieczniejsze funkcji wymaga rozmiar w znakach każdego `c`, `C`, `s`, `S`, i `[` pola typu przekazywany jako argument bezpośrednio po zmiennej. Aby uzyskać więcej informacji, zobacz [scanf_s —, _scanf_s_l —, wscanf_s —, _wscanf_s_l —](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) i [scanf — specyfikacje szerokości](../../c-runtime-library/scanf-width-specification.md).  
  
> [!NOTE]
>  Parametr rozmiaru jest typu `unsigned`, a nie `size_t`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vftscanf_s`|`vfscanf_s`|`vfscanf_s`|`vfwscanf_s`|  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`vfscanf_s`|\<stdio.h >|  
|`vfwscanf_s`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_vfscanf_s.c  
// compile with: /W3  
// This program writes formatted  
// data to a file. It then uses vfscanf_s to  
// read the various data back from the file.  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int call_vfscanf_s(FILE * istream, char * format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vfscanf_s(istream, format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main(void)  
{  
    long l;  
    float fp;  
    char s[81];  
    char c;  
  
    if (fopen_s(&stream, "vfscanf_s.out", "w+") != 0)  
    {  
        printf("The file vfscanf_s.out was not opened\n");  
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
        call_vfscanf_s(stream, "%s %ld %f%c", s, _countof(s), &l, &fp, &c, 1);  
  
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
 [_cscanf_s —, _cscanf_s_l —, _cwscanf_s — _cwscanf_s_l —](../../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)   
 [fprintf_s —, _fprintf_s_l —, fwprintf_s — _fwprintf_s_l —](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [scanf_s —, _scanf_s_l —, wscanf_s — _wscanf_s_l —](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [sscanf_s —, _sscanf_s_l —, swscanf_s — _swscanf_s_l —](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)   
 [fscanf —, _fscanf_l —, fwscanf — _fwscanf_l —](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [vfscanf, vfwscanf](../../c-runtime-library/reference/vfscanf-vfwscanf.md)