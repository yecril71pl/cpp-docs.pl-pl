---
title: "sprintf, _sprintf_l —, swprintf —, _swprintf_l —, __swprintf_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __swprintf_l
- sprintf
- _sprintf_l
- _swprintf_l
- swprintf
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
- ntdll.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _stprintf_l
- __swprintf_l
- sprintf_l
- swprintf
- _sprintf_l
- sprintf
- _stprintf
- stprintf_l
dev_langs: C++
helpviewer_keywords:
- _swprintf_l function
- _stprintf function
- __swprintf_l function
- stprintf function
- sprintf function
- _sprintf_l function
- _stprintf_l function
- swprintf function
- strings [C++], writing to
- _CRT_NON_CONFORMING_SWPRINTFS
- swprintf_l function
- stprintf_l function
- sprintf_l function
- formatted text [C++]
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
caps.latest.revision: "36"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f4b8b840e73665aa9c176daccf5c1bc712f4f2ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="sprintf-sprintfl-swprintf-swprintfl-swprintfl"></a>sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l
Zapis sformatowane dane do ciągu. Niektóre z tych funkcji bezpieczniejsze wersje są dostępne; zobacz [sprintf_s —, _sprintf_s_l —, swprintf_s —, _swprintf_s_l —](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md). Bezpieczne wersje `swprintf` i `_swprintf_l` nie przyjmują `count` parametru.  
  
## <a name="syntax"></a>Składnia  
  
```  
int sprintf(  
   char *buffer,  
   const char *format [,  
   argument] ...   
);  
int _sprintf_l(  
   char *buffer,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int swprintf(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format [,  
   argument]...  
);  
int _swprintf_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
int __swprintf_l(  
   wchar_t *buffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
template <size_t size>  
int sprintf(  
   char (&buffer)[size],  
   const char *format [,  
   argument] ...   
); // C++ only  
template <size_t size>  
int _sprintf_l(  
   char (&buffer)[size],  
   const char *format,  
   locale_t locale [,  
   argument] ...   
); // C++ only  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Lokalizacja magazynu dla danych wyjściowych  
  
 `count`  
 Maksymalna liczba znaków, które mają być przechowywane w wersji Unicode tej funkcji.  
  
 `format`  
 Ciąg formatu — formant  
  
 `argument`  
 Argumenty opcjonalne  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
 Aby uzyskać więcej informacji, zobacz [specyfikacje formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba znaków zapisywane lub -1, jeśli wystąpił błąd. Jeśli `buffer` lub `format` wskaźnika o wartości null, jest program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli wykonanie może kontynuować, następujące funkcje i ustaw `errno` do `EINVAL`.  
  
 `sprintf`Zwraca liczbę bajtów przechowywanych w `buffer`, nie licząc znak końcowy null. `swprintf`Zwraca liczbę znaki dwubajtowe są przechowywane w `buffer`, nie licząc zakończenia null znaków dwubajtowych.  
  
## <a name="remarks"></a>Uwagi  
 `sprintf` Funkcji formatuje i przechowuje serii znaków i wartościami `buffer`. Każdy `argument` (jeśli istnieje) jest konwertowana i dane wyjściowe według specyfikacji formatu w `format`. Format składa się ze znaków zwykłych i ma tę samą tworzą i działać jako `format` argument [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Znak null jest dołączany za ostatni znak zapisywane. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.  
  
> [!IMPORTANT]
>  Przy użyciu `sprintf`, nie istnieje sposób ograniczyć liczbę znaków zapisywane, co oznacza, że w kodzie za pomocą `sprintf` jest podatny na przepełnienia buforu. Należy wziąć pod uwagę przy użyciu powiązanych funkcji [_snprintf —](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), która określa maksymalną liczbę znaków do zapisania `buffer`, lub użyj [_scprintf —](../../c-runtime-library/reference/scprintf-scprintf-l-scwprintf-scwprintf-l.md) można określić wielkość bufora jest wymagana. Ponadto upewnij się, że `format` nie jest ciągiem zdefiniowane przez użytkownika.  
  
 `swprintf`jest to wersja znaków dwubajtowych `sprintf`; argumenty wskaźnika `swprintf` są ciągami znaków dwubajtowych. Wykrywanie błędów kodowania `swprintf` może się różnić od w `sprintf`. `swprintf`i `fwprintf` zachowują się tak samo, z wyjątkiem `swprintf` zapisuje dane wyjściowe z ciągiem, a nie do miejsca docelowego typu `FILE`, i `swprintf` wymaga `count` parametr, aby określić maksymalną liczbę znaków, które można zapisane. Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.  
  
 `swprintf`zgodne ze standardem C ISO, co wymaga drugiego parametru, `count`, typu `size_t`. Aby wymusić starego niestandardowe zachowanie, należy zdefiniować `_CRT_NON_CONFORMING_SWPRINTFS`. W przyszłych wersjach stare zachowanie mogą zostać usunięte, więc należy zmienić kod do użycia nowego zachowania zgodność.  
  
 W języku C++ te funkcje mają przeciążenia szablonu, które wywołują odpowiedników nowsza, bezpieczne tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_stprintf`|`sprintf`|`sprintf`|`_swprintf`|  
|`_stprintf_l`|`_sprintf_l`|`_sprintf_l`|`__swprintf_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`sprintf`, `_sprintf_l`|\<stdio.h >|  
|`swprintf`, `_swprintf_l`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_sprintf.c  
// compile with: /W3  
// This program uses sprintf to format various  
// data and place them in the string named buffer.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char  buffer[200], s[] = "computer", c = 'l';  
   int   i = 35, j;  
   float fp = 1.7320534f;  
  
   // Format and print various data:   
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996  
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996  
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996  
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996  
   // Note: sprintf is deprecated; consider using sprintf_s instead  
  
   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );  
}  
```  
  
```Output  
Output:  
   String:    computer  
   Character: l  
   Integer:   35  
   Real:      1.732053  
  
character count = 79  
```  
  
## <a name="example"></a>Przykład  
  
```  
// crt_swprintf.c  
// wide character example  
// also demonstrates swprintf returning error code  
#include <stdio.h>  
  
int main( void )  
{  
   wchar_t buf[100];  
   int len = swprintf( buf, 100, L"%s", L"Hello world" );  
   printf( "wrote %d characters\n", len );  
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );  
   // swprintf fails because string contains WEOF (\xffff)  
   printf( "wrote %d characters\n", len );  
}  
```  
  
```Output  
wrote 11 characters  
wrote -1 characters  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fprintf —, _fprintf_l —, fwprintf — _fwprintf_l —](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l —, wprintf, _wprintf_l —](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf, _scanf_l —, wscanf — _wscanf_l —](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf —, _sscanf_l —, swscanf — _swscanf_l —](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)