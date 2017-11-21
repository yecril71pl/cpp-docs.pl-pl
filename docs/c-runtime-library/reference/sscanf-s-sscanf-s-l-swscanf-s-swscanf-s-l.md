---
title: "sscanf_s —, _sscanf_s_l —, swscanf_s —, _swscanf_s_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _sscanf_s_l
- sscanf_s
- _swscanf_s_l
- swscanf_s
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
- _stscanf_s
- sscanf_s
- swscanf_s
- _swscanf_s_l
- _stscanf_s_l
- _sscanf_s_l
dev_langs: C++
helpviewer_keywords:
- stscanf_s_l function
- stscanf_s function
- swscanf_s function
- swscanf_s_l function
- sscanf_s_l function
- _stscanf_s_l function
- strings [C++], reading data from
- sscanf_s function
- _swscanf_s_l function
- _stscanf_s function
- reading data, strings
- strings [C++], reading
- _sscanf_s_l function
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 71c8f24aee70b91c45448654a8499d0f49a4a085
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="sscanfs-sscanfsl-swscanfs-swscanfsl"></a>sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l
Odczyty sformatowane dane z ciągu. Te wersje programu [sscanf —, _sscanf_l —, swscanf —, _swscanf_l —](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
int sscanf_s(  
   const char *buffer,  
   const char *format [,  
   argument ] ...  
);  
int _sscanf_s_l(  
   const char *buffer,  
   const char *format,  
   locale_t locale [,  
   argument ] ...  
);  
int swscanf_s(  
   const wchar_t *buffer,  
   const wchar_t *format [,  
   argument ] ...  
);  
int _swscanf_s_l(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ] ...  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Przechowywanych danych  
  
 `format`  
 Ciąg kontroli formatu. Aby uzyskać więcej informacji, zobacz [pola specyfikacji formatu: funkcji wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
 `argument`  
 Argumenty opcjonalne  
  
 `locale`  
 Ustawienia regionalne do użycia  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca liczbę pól, które pomyślnie przekonwertowany i przypisane; wartość zwrotna nie zawiera pola, które zostały do odczytu, ale nie są przypisane. Wartość zwracana 0 wskazuje, że nie ma pól zostały przypisane. Wartość zwracana jest `EOF` błędu lub po osiągnięciu końca ciągu przed pierwszym konwersji.  
  
 Jeśli `buffer` lub `format` jest `NULL` wskaźnika, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli wykonanie może kontynuować, następujące funkcje i ustaw `errno` do`EINVAL`  
  
 Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `sscanf_s` Funkcja odczytywać dane z `buffer` do lokalizacji, która jest określany przez każdy `argument`. Wskaźniki do zmiennych, które mają typ, który odpowiada specyfikatorowi typu w określić argumenty po ciągu formatu `format`. W przeciwieństwie do wersji mniej bezpieczne `sscanf`, parametr rozmiaru buforu jest wymagany, gdy używasz znaki pola typu `c`, `C`, `s`, `S`, lub string zestawów kontroli, które są ujęte w `[]`. Rozmiar buforu w znaki muszą zostać dostarczone jako dodatkowy parametr natychmiast po każdego parametru buforu, który wymaga. Na przykład podczas czytania na ciąg, rozmiar buforu dla ten ciąg jest przekazywany w następujący sposób:  
  
 `wchar_t ws[10];`  
  
 `swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9`  
  
 Rozmiar buforu obejmuje zakończenia wartości null. Pola specyfikacji szerokość może służyć do zapewnienia, że token, który jest odczytywany w zmieści się w buforze. Jeśli żadne pole Specyfikacja szerokości jest używany, a token odczytu w jest zbyt duży, aby zmieścić się w buforze, nic nie są zapisywane w tym buforu.  
  
 W przypadku znaków pojedynczy znak może wyglądać następująco:  
  
 `wchar_t wc;`  
  
 `swscanf_s(in_str, L"%c", &wc, 1);`  
  
 Ten przykład odczytuje jednego znaku w ciągu wejściowym, a następnie przechowuje je w buforze znaków dwubajtowych. Po przeczytaniu wielu znaków dla ciągów zakończone inną niż null liczb całkowitych bez znaku są używane jako specyfikacja szerokości i rozmiar buforu.  
  
 `char c[4];`  
  
 `sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated`  
  
 Aby uzyskać więcej informacji, zobacz [scanf_s —, _scanf_s_l —, wscanf_s —, _wscanf_s_l —](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) i [scanf — znaki pola typu](../../c-runtime-library/scanf-type-field-characters.md).  
  
> [!NOTE]
>  Parametr rozmiaru jest typu `unsigned`, a nie `size_t`. W przypadku kompilowania kodu 64-bitowych obiektów docelowych, użyj rzutowania statycznego do konwertowania `_countof` lub `sizeof` wyników do właściwego rozmiaru.  
  
 `format` Formanty argument interpretacji dane wejściowe pola i ma tę samą tworzą i działać jako `format` argument `scanf_s` funkcji. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.  
  
 `swscanf_s`jest to wersja znaków dwubajtowych `sscanf_s;` argumenty `swscanf_s` są ciągami znaków dwubajtowych. `sscanf_s`nie obsługuje wielobajtowe znaków szesnastkowych. `swscanf_s`nie obsługuje szesnastkowych pełnej szerokości Unicode lub znaków "strefy zgodności". W przeciwnym razie `swscanf_s` i `sscanf_s` zachowują się tak samo.  
  
 Wersje tych funkcji, które mają `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych, który jest przekazywany w zamiast bieżącego ustawienia regionalne wątku.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_stscanf_s`|`sscanf_s`|`sscanf_s`|`swscanf_s`|  
|`_stscanf_s_l`|`_sscanf_s_l`|`_sscanf_s_l`|`_swscanf_s_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`sscanf_s`, `_sscanf_s_l`|\<stdio.h >|  
|`swscanf_s`, `_swscanf_s_l`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_sscanf_s.c  
// This program uses sscanf_s to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char  tokenstring[] = "15 12 14...";  
   char  s[81];  
   char  c;  
   int   i;  
   float fp;  
  
   // Input various data from tokenstring:  
   // max 80 character string plus NULL terminator  
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );  
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );  
   sscanf_s( tokenstring, "%d", &i );  
   sscanf_s( tokenstring, "%f", &fp );  
  
   // Output the data read  
   printf_s( "String    = %s\n", s );  
   printf_s( "Character = %c\n", c );  
   printf_s( "Integer:  = %d\n", i );  
   printf_s( "Real:     = %f\n", fp );  
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
 [fscanf —, _fscanf_l —, fwscanf — _fwscanf_l —](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [scanf, _scanf_l —, wscanf — _wscanf_l —](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sprintf, _sprintf_l —, swprintf —, _swprintf_l —, \__swprintf_l —](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [snprintf — _snprintf —, _snprintf_l —, _snwprintf —, _snwprintf_l —](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)