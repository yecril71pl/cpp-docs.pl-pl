---
title: "sprintf_s —, _sprintf_s_l —, swprintf_s —, _swprintf_s_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _swprintf_s_l
- _sprintf_s_l
- swprintf_s
- sprintf_s
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
- swprintf_s
- sprintf_s
- stdio/sprintf_s
- stdio/swprintf_s
- stdio/_sprintf_s_l
- stdio/_swprintf_s_l
- _sprintf_s_l
- _swprintf_s_l
dev_langs: C++
helpviewer_keywords:
- stprintf_s function
- stprintf_s_l function
- swprintf_s_l function
- sprintf_s function
- swprintf_s function
- _swprintf_s_l function
- sprintf_s_l function
- _stprintf_s_l function
- _stprintf_s function
- _sprintf_s_l function
- formatted text [C++]
ms.assetid: 424f0a29-22ef-40e8-b565-969f5f57782f
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 12b5799c9471ffaf8328d4f8aa6a994319e4f30f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="sprintfs-sprintfsl-swprintfs-swprintfsl"></a>sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l
Zapis sformatowane dane do ciągu. Są to wersje [sprintf, _sprintf_l —, swprintf —, _swprintf_l —, \__swprintf_l —](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
int sprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format,  
   ...   
);  
int _sprintf_s_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format,  
   locale_t locale,  
   ...   
);  
int swprintf_s(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format,  
   ...  
);  
int _swprintf_s_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format,  
   locale_t locale,  
   ...  
);  
template <size_t size>  
int sprintf_s(  
   char (&buffer)[size],  
   const char *format,  
   ...   
); // C++ only  
template <size_t size>  
int swprintf_s(  
   wchar_t (&buffer)[size],  
   const wchar_t *format,  
   ...  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Lokalizacja magazynu dla danych wyjściowych  
  
 `sizeOfBuffer`  
 Maksymalna liczba znaków do zapisania.  
  
 `format`  
 Ciąg formatu — formant  
  
 `...`  
 Argumenty opcjonalne formatowania  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
 Aby uzyskać więcej informacji, zobacz [specyfikacje formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba znaków zapisywane lub -1, jeśli wystąpił błąd. Jeśli `buffer` lub `format` wskaźnika o wartości null, jest `sprintf_s` i `swprintf_s` Zwróć -1 i ustaw `errno` do `EINVAL`.  
  
 `sprintf_s`Zwraca liczbę bajtów przechowywanych w `buffer`, nie licząc znak końcowy null. `swprintf_s`Zwraca liczbę znaki dwubajtowe są przechowywane w `buffer`, nie licząc zakończenia null znaków dwubajtowych.  
  
## <a name="remarks"></a>Uwagi  
 `sprintf_s` Funkcji formatuje i przechowuje serii znaków i wartościami `buffer`. Każdy `argument` (jeśli istnieje) jest konwertowana i dane wyjściowe według specyfikacji formatu w `format`. Format składa się ze znaków zwykłych i ma tę samą tworzą i działać jako `format` argument [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Znak null jest dołączany za ostatni znak zapisywane. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.  
  
 Co podstawowa różnica między `sprintf_s` i `sprintf` jest to, że `sprintf_s` sprawdza ciąg formatowania do prawidłowych znaków formatowania, podczas gdy `sprintf` tylko sprawdza, czy są formatu ciągu lub buforu `NULL` wskaźników. Jeśli zaznacz kończy się niepowodzeniem, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca wartość -1 i zestawy `errno` do `EINVAL`.  
  
 Główną różnicą między `sprintf_s` i `sprintf` jest to, że `sprintf_s` przyjmuje parametr długości określania rozmiaru buforu wyjściowego w znakach. Jeśli bufor jest za mała dla wartości tekst sformatowany, w tym zakończenia wartość null, a następnie bufor jest ustawiona na pusty ciąg umieszczając znak null w `buffer[0]`, i jest wywoływana przez program obsługi nieprawidłowych parametrów. W odróżnieniu od `_snprintf`, `sprintf_s` gwarantuje, że bufor będzie można zerem chyba, że rozmiar buforu jest równy zero.  
  
 `swprintf_s`jest to wersja znaków dwubajtowych `sprintf_s`; argumenty wskaźnika `swprintf_s` są ciągami znaków dwubajtowych. Wykrywanie błędów kodowania `swprintf_s` może się różnić od w `sprintf_s`. Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.  
  
 W języku C++ użycia tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można wnioskować o długości buforu automatycznie, co eliminuje konieczność określania argumentem rozmiaru i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
 Dostępne są wersje `sprintf_s` które oferuje dodatkową kontrolę nad co się stanie, jeśli bufor jest za mały. Aby uzyskać więcej informacji, zobacz [_snprintf_s —, _snprintf_s_l —, _snwprintf_s —, _snwprintf_s_l —](../../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_stprintf_s`|`sprintf_s`|`sprintf_s`|`swprintf_s`|  
|`_stprintf_s_l`|`_sprintf_s_l`|`_sprintf_s_l`|`_swprintf_s_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`sprintf_s`, `_sprintf_s_l`|C: \<stdio.h ><br /><br /> C++: \<cstdio — > lub \<stdio.h >|  
|`swprintf_s`, `_swprintf_s_l`|C: \<stdio.h > lub \<wchar.h ><br /><br /> C++: \<cstdio — >, \<cwchar — >, \<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_sprintf_s.c  
// This program uses sprintf_s to format various  
// data and place them in the string named buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   char  buffer[200], s[] = "computer", c = 'l';  
   int   i = 35, j;  
   float fp = 1.7320534f;  
  
   // Format and print various data:   
   j  = sprintf_s( buffer, 200,     "   String:    %s\n", s );  
   j += sprintf_s( buffer + j, 200 - j, "   Character: %c\n", c );  
   j += sprintf_s( buffer + j, 200 - j, "   Integer:   %d\n", i );  
   j += sprintf_s( buffer + j, 200 - j, "   Real:      %f\n", fp );  
  
   printf_s( "Output:\n%s\ncharacter count = %d\n", buffer, j );  
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
// crt_swprintf_s.c  
// wide character example  
// also demonstrates swprintf_s returning error code  
#include <stdio.h>  
  
int main( void )  
{  
   wchar_t buf[100];  
   int len = swprintf_s( buf, 100, L"%s", L"Hello world" );  
   printf( "wrote %d characters\n", len );  
   len = swprintf_s( buf, 100, L"%s", L"Hello\xffff world" );  
   // swprintf_s fails because string contains WEOF (\xffff)  
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
 [vprintf — funkcje](../../c-runtime-library/vprintf-functions.md)