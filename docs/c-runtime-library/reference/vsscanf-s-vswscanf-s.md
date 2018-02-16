---
title: vsscanf_s, vswscanf_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- vswscanf_s
- vsscanf_s
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
- vsscanf_s
- vswscanf_s
- _vstscanf_s
dev_langs:
- C++
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f956e20ecfd694666cacd1eae2071526cf71ec50
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="vsscanfs-vswscanfs"></a>vsscanf_s, vswscanf_s
Odczyty sformatowane dane z ciągu. Te wersje programu [vsscanf —, vswscanf —](../../c-runtime-library/reference/vsscanf-vswscanf.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
int vsscanf_s(  
   const char *buffer,  
   const char *format,  
   va_list argptr  
);   
int vswscanf_s(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   va_list arglist  
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Przechowywanych danych  
  
 `format`  
 Ciąg kontroli formatu. Aby uzyskać więcej informacji, zobacz [pola specyfikacji formatu: funkcji wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
 `arglist`  
 Listy zmiennych argumentów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca liczbę pól, które pomyślnie przekonwertowany i przypisane; wartość zwrotna nie zawiera pola, które zostały do odczytu, ale nie są przypisane. Wartość zwracana 0 wskazuje, że nie ma pól zostały przypisane. Wartość zwracana jest `EOF` błędu lub po osiągnięciu końca ciągu przed pierwszym konwersji.  
  
 Jeśli `buffer` lub `format` jest `NULL` wskaźnika, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli wykonanie może kontynuować, następujące funkcje i ustaw `errno` do `EINVAL`  
  
 Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `vsscanf_s` Funkcja odczytywać dane z `buffer` w lokalizacjach, które są podane przez każdy argument `arglist` listy argumentów. Argumenty w liście argumentów określają wskaźniki do zmiennych, które mają typ, który odpowiada specyfikatorowi typu w `format`. W przeciwieństwie do wersji mniej bezpieczne `vsscanf`, parametr rozmiaru buforu jest wymagany, gdy używasz znaki pola typu `c`, `C`, `s`, `S`, lub ciągu sterowania zestawów, które są ujęte w `[]`. Rozmiar buforu w znaki muszą zostać dostarczone jako dodatkowy parametr natychmiast po każdego parametru buforu, który wymaga.  
  
 Rozmiar buforu obejmuje zakończenia wartości null. Pola specyfikacji szerokość może służyć do zapewnienia, że token, który jest odczytywany w zmieści się w buforze. Jeśli żadne pole Specyfikacja szerokości jest używany, a token odczytu w jest zbyt duży, aby zmieścić się w buforze, nic nie są zapisywane w tym buforu.  
  
 Aby uzyskać więcej informacji, zobacz [scanf_s —, _scanf_s_l —, wscanf_s —, _wscanf_s_l —](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) i [scanf — znaki pola typu](../../c-runtime-library/scanf-type-field-characters.md).  
  
> [!NOTE]
>  Parametr rozmiaru jest typu `unsigned`, a nie `size_t`.  
  
 `format` Formanty argument interpretacji dane wejściowe pola i ma tę samą tworzą i działać jako `format` argument `scanf_s` funkcji. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.  
  
 `vswscanf_s` jest to wersja znaków dwubajtowych `vsscanf_s`; argumenty `vswscanf_s` są ciągami znaków dwubajtowych. `vsscanf_s` nie obsługuje wielobajtowe znaków szesnastkowych. `vswscanf_s` nie obsługuje szesnastkowych pełnej szerokości Unicode lub znaków "strefy zgodności". W przeciwnym razie `vswscanf_s` i `vsscanf_s` zachowują się tak samo.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vstscanf_s`|`vsscanf_s`|`vsscanf_s`|`vswscanf_s`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`vsscanf_s`|\<stdio.h>|  
|`vswscanf_s`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_vsscanf_s.c  
// compile with: /W3  
// This program uses vsscanf_s to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <stdlib.h>  
  
int call_vsscanf_s(char *tokenstring, char *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vsscanf_s(tokenstring, format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main( void )  
{  
    char  tokenstring[] = "15 12 14...";  
    char  s[81];  
    char  c;  
    int   i;  
    float fp;  
  
    // Input various data from tokenstring:  
    // max 80 character string:  
    call_vsscanf_s(tokenstring, "%80s", s, _countof(s));  
    call_vsscanf_s(tokenstring, "%c", &c, sizeof(char));  
    call_vsscanf_s(tokenstring, "%d", &i);  
    call_vsscanf_s(tokenstring, "%f", &fp);  
  
    // Output the data read  
    printf("String    = %s\n", s);  
    printf("Character = %c\n", c);  
    printf("Integer:  = %d\n", i);  
    printf("Real:     = %f\n", fp);  
}  
```  
  
```Output  
String    = 15  
Character = 1  
Integer:  = 15  
Real:     = 15.000000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [scanf, _scanf_l —, wscanf — _wscanf_l —](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf —, _sscanf_l —, swscanf — _swscanf_l —](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)   
 [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vsscanf, vswscanf](../../c-runtime-library/reference/vsscanf-vswscanf.md)