---
title: snprintf —, _snprintf —, _snprintf_l —, _snwprintf —, _snwprintf_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _snwprintf
- _snprintf
- _snprintf_l
- _snwprintf_l
- snprintf
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _snprintf
- snprintf_l
- snwprintf_l
- sntprintf
- snprintf
- _sntprintf
- _sntprintf_l
- sntprintf_l
- snwprintf
- _snprintf_l
- _snwprintf
- _snwprintf_l
dev_langs:
- C++
helpviewer_keywords:
- snwprintf_l function
- sntprintf_l function
- snprintf_l function
- _snwprintf_l function
- _sntprintf_l function
- _snwprintf function
- _snprintf function
- _sntprintf function
- _snprintf_l function
- snwprintf function
- snprintf function
- sntprintf function
- formatted text [C++]
ms.assetid: 5976c9c8-876e-4ac9-a515-39f3f7fd0925
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90f931153b4328c404fa4a0e6be8f0c3548c4d95
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="snprintf-snprintf-snprintfl-snwprintf-snwprintfl"></a>snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l
Zapisuje sformatowane dane do ciągu. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_snprintf_s —, _snprintf_s_l —, _snwprintf_s —, _snwprintf_s_l —](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).

## <a name="syntax"></a>Składnia

```C
int snprintf(
   char *buffer,
   size_t count,
   const char *format [,
   argument] ...
);
int _snprintf(
   char *buffer,
   size_t count,
   const char *format [,
   argument] ...
);
int _snprintf_l(
   char *buffer,
   size_t count,
   const char *format,
   locale_t locale [,
   argument] ...
);
int _snwprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument] ...
);
int _snwprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int _snprintf(
   char (&buffer)[size],
   size_t count,
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _snprintf_l(
   char (&buffer)[size],
   size_t count,
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only
template <size_t size>
int _snwprintf(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format [,
   argument] ...
); // C++ only
template <size_t size>
int _snwprintf_l(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Lokalizacja w pamięci dla danych wyjściowych.

*Liczba*<br/>
Maksymalna liczba znaków do zapisania.

*Format*<br/>
Ciąg kontroli formatu.

*Argument*<br/>
Argumenty opcjonalne.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz [składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

Let **len** można długość ciągu formatowania danych, nie włączając zakończenia null. Zarówno **len** i *liczba* w bajtach dla **snprintf —** i **_snprintf —**, wielu znaków dla **_snwprintf —**.

Dla wszystkich funkcji Jeśli **len** < *liczba*, **len** znaków są przechowywane w *buforu*, dołączany terminatora wartości null i **len** jest zwracany.

**Snprintf —** Funkcja obcina dane wyjściowe podczas **len** jest większa niż lub równa *liczba*, umieszczając terminatora null w `buffer[count-1]`. Wartość zwracana jest **len**, liczba znaków, które byłyby dane wyjściowe Jeśli *liczba* był wystarczająco duży. **Snprintf —** funkcja zwraca wartość ujemną, jeśli wystąpi błąd kodowania.

Dla wszystkich funkcji innych niż **snprintf —**, jeśli **len** = *liczba*, **len** znaków są przechowywane w  *Bufor*, dołączany nie terminatorem null i **len** jest zwracany. Jeśli **len** > *liczba*, *liczba* znaków są przechowywane w *buforu*, nie terminatorem null jest dołączany, ujemna wartość jest zwracana.

Jeśli *buforu* wskaźnik null i *liczba* wynosi zero, **len** jest zwracana jako liczbę znaków wymaganą do formatowania danych wyjściowych, nie włączając zakończenia null. Aby pomyślnym nawiązaniu połączenia z tym samym *argument* i *ustawień regionalnych* parametrów, przydzielić buforu zawierający co najmniej **len** + 1 znaków.

Jeśli *buforu* wskaźnik null i *liczba* jest różna od zera, lub jeśli *format* wskaźnika o wartości null, jest program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [ Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli wykonanie może kontynuować, następujące funkcje i ustaw **errno** do **einval —**.

Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Snprintf —** funkcji i **_snprintf —** rodziny funkcji format i magazynu *liczba* lub mniej znaków w *buforu*. **Snprintf —** funkcja zawsze przechowuje znak końcowy null, obcinanie dane wyjściowe, jeśli to konieczne. **_Snprintf —** rodziny funkcji tylko dołącza znak końcowy null, jeśli długość ciągu sformatowaną jest ściśle mniejsza niż *liczba* znaków. Każdy *argument* (jeśli istnieje) jest konwertowany i dane wyjściowe według specyfikacji formatu w *format*. Format składa się ze znaków zwykłych i ma tę samą tworzą i działać jako *format* argument [printf](printf-printf-l-wprintf-wprintf-l.md). Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

> [!IMPORTANT]
> Upewnij się, że *format* nie jest ciągiem zdefiniowane przez użytkownika. Ponieważ **_snprintf —** funkcje gwarantuje zakończenia null — w szczególności, gdy wartość zwracana jest *liczba*— upewnij się, że zostały wykonane przez kod, który dodaje terminatorem null. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).

Począwszy od Biblioteka UCRT w programie Visual Studio 2015 i Windows 10 **snprintf —** nie jest już takie same jak **_snprintf —**. **Snprintf —** zachowanie funkcji jest teraz zgodne standard C99.

**_snwprintf —** jest wersja znaków dwubajtowych **_snprintf —**; argumenty wskaźnika **_snwprintf —** są ciągami znaków dwubajtowych. Wykrywanie błędów kodowania **_snwprintf —** może się różnić od w **_snprintf —**. **_snwprintf —**, tak jak **swprintf —**, zapisuje dane wyjściowe do ciągu zamiast docelowego typu **pliku**.

Wersje tych funkcji, które mają **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.

W C++ te funkcje mają przeciążenia szablonu, które wywołują ich nowsze, bezpieczniejsze odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntprintf —**|**_snprintf**|**_snprintf**|**_snwprintf**|
|**_sntprintf_l —**|**_snprintf_l**|**_snprintf_l**|**_snwprintf_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**snprintf —**, **_snprintf —**, **_snprintf_l —**|\<stdio.h>|
|**_snwprintf —**, **_snwprintf_l —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_snprintf.c
// compile with: /W3
#include <stdio.h>
#include <stdlib.h>

#if !defined(__cplusplus)
typedef int bool;
const bool true = 1;
const bool false = 0;
#endif

#define FAIL 0 // change to 1 and see what happens

int main(void)
{
   char buffer[200];
   const static char s[] = "computer"
#if FAIL
"computercomputercomputercomputercomputercomputercomputercomputer"
"computercomputercomputercomputercomputercomputercomputercomputer"
"computercomputercomputercomputercomputercomputercomputercomputer"
"computercomputercomputercomputercomputercomputercomputercomputer"
#endif
   ;
   const char c = 'l';
   const int i = 35;
#if FAIL
   const double fp = 1e300; // doesn't fit in the buffer
#else
   const double fp = 1.7320534;
#endif
   /* !subtract one to prevent "squeezing out" the terminal null! */
   const int bufferSize = sizeof(buffer)/sizeof(buffer[0]) - 1;
   int bufferUsed = 0;
   int bufferLeft = bufferSize - bufferUsed;
   bool bSuccess = true;
   buffer[0] = 0;

   /* Format and print various data: */

   if (bufferLeft > 0)
   {
      int perElementBufferUsed = _snprintf(&buffer[bufferUsed],
      bufferLeft, "   String: %s\n", s ); // C4996
      // Note: _snprintf is deprecated; consider _snprintf_s instead
      if (bSuccess = (perElementBufferUsed >= 0))
      {
         bufferUsed += perElementBufferUsed;
         bufferLeft -= perElementBufferUsed;
         if (bufferLeft > 0)
         {
            int perElementBufferUsed = _snprintf(&buffer[bufferUsed],
            bufferLeft, "   Character: %c\n", c ); // C4996
            if (bSuccess = (perElementBufferUsed >= 0))
            {
               bufferUsed += perElementBufferUsed;
               bufferLeft -= perElementBufferUsed;
               if (bufferLeft > 0)
               {
                  int perElementBufferUsed = _snprintf(&buffer
                  [bufferUsed], bufferLeft, "   Integer: %d\n", i ); // C4996
                  if (bSuccess = (perElementBufferUsed >= 0))
                  {
                     bufferUsed += perElementBufferUsed;
                     bufferLeft -= perElementBufferUsed;
                     if (bufferLeft > 0)
                     {
                        int perElementBufferUsed = _snprintf(&buffer
                        [bufferUsed], bufferLeft, "   Real: %f\n", fp ); // C4996
                        if (bSuccess = (perElementBufferUsed >= 0))
                        {
                           bufferUsed += perElementBufferUsed;
                        }
                     }
                  }
               }
            }
         }
      }
   }

   if (!bSuccess)
   {
      printf("%s\n", "failure");
   }
   else
   {
      /* !store null because _snprintf doesn't necessarily (if the string
       * fits without the terminal null, but not with it)!
       * bufferUsed might be as large as bufferSize, which normally is
       * like going one element beyond a buffer, but in this case
       * subtracted one from bufferSize, so we're ok.
       */
      buffer[bufferUsed] = 0;
      printf( "Output:\n%s\ncharacter count = %d\n", buffer, bufferUsed );
   }
   return EXIT_SUCCESS;
}
```

```Output
Output:
   String: computer
   Character: l
   Integer: 35
   Real: 1.732053

character count = 69
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
