---
title: "vsnprintf_s —, _vsnprintf_s —, _vsnprintf_s_l —, _vsnwprintf_s —, _vsnwprintf_s_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
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
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
dev_langs: C++
helpviewer_keywords:
- vsnwprintf_s function
- _vsntprintf_s function
- _vsntprintf_s_l function
- vsntprintf_s function
- vsnwprintf_s_l function
- vsnprintf_s_l function
- vsntprintf_s_l function
- _vsnwprintf_s_l function
- _vsnprintf_s function
- vsnprintf_s function
- _vsnprintf_s_l function
- _vsnwprintf_s function
- formatted text [C++]
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8df40232ae7a6a92343e86fc00db5f4f0e571ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="vsnprintfs-vsnprintfs-vsnprintfsl-vsnwprintfs-vsnwprintfsl"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l
Zapisywanie sformatowanego danych wyjściowych przy użyciu wskaźnika do listy argumentów. Są to wersje [vsnprintf —, _vsnprintf —, _vsnprintf_l —, _vsnwprintf —, _vsnwprintf_l —](../../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
int vsnprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf_s_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vsnwprintf_s(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vsnwprintf_s_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
template <size_t size>  
int _vsnprintf_s(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnwprintf_s(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Lokalizacja magazynu dla danych wyjściowych.  
  
 `sizeOfBuffer`  
 Rozmiar `buffer` dla danych wyjściowych jako liczba znaków.  
  
 `count`  
 Maksymalna liczba znaków do zapisu (nie w tym zakończenia null), lub [_truncate —](../../c-runtime-library/truncate.md).  
  
 `format`  
 Definicja formatu.  
  
 `argptr`  
 Wskaźnik do listy argumentów.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
 Aby uzyskać więcej informacji, zobacz [specyfikacje formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 `vsnprintf_s`,`_vsnprintf_s` i `_vsnwprintf_s` zwraca liczbę znaków zapisane, nie tym zakończenia wartość null lub wartość ujemną, jeśli wystąpi błąd wyjścia. `vsnprintf_s`jest taka sama jak `_vsnprintf_s`. `vsnprintf_s`jest on dołączony do zgodności ze standardem ANSI. `_vnsprintf`została zachowana na potrzeby zgodności z poprzednimi wersjami.  
  
 Jeśli przekracza magazynu wymaganego do przechowywania danych i zakończenia null `sizeOfBuffer`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md), chyba że `count` jest [_truncate —](../../c-runtime-library/truncate.md), w którym to przypadku tyle ciągu jako zmieści się `buffer` są zapisywane i zwrócił wartość -1. Jeśli program obsługi nieprawidłowych parametrów wykonywania odtwarzanie jest kontynuowane, te funkcje ustawić `buffer` na pusty ciąg, ustaw `errno` do `ERANGE`i zwróć -1.  
  
 Jeśli `buffer` lub `format` jest `NULL` wskaźnika, lub jeśli `count` jest mniejsza lub równa zero, program obsługi nieprawidłowych parametrów jest wywoływany. Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwróć -1.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`Condition`|Zwraca|`errno`|  
|-----------------|------------|-------------|  
|`buffer`jest`NULL`|-1|`EINVAL`|  
|`format`jest`NULL`|-1|`EINVAL`|  
|`count` <= 0|-1|`EINVAL`|  
|`sizeOfBuffer`za mały (i `count` ! = `_TRUNCATE`)|-1 (i `buffer` ustawiony na pusty ciąg)|`ERANGE`|  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji przyjmuje wskaźnik do listy argumentów, a następnie formatuje i zapisuje do `count` znaki określone dane do pamięci wskazywanej przez `buffer` i dołącza zakończenia wartości null.  
  
 Jeśli `count` jest [_truncate —](../../c-runtime-library/truncate.md), a następnie zapisać te funkcje, jaka ciągu, ile zmieści się `buffer` pozostawiając miejsca do zakończenia wartości null. Jeśli cały ciąg (przy użyciu zakończenia wartości null) mieści się `buffer`, następnie funkcje zwracają liczbę znaków, zapisane (bez przerywania null); w przeciwnym razie Zwróć -1, aby wskazać, że obcięcie wystąpił, te funkcje.  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.  
  
> [!IMPORTANT]
>  Upewnij się, że `format` nie jest ciągiem zdefiniowane przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
> [!NOTE]
>  Aby upewnić się, czy jest miejsce na null Trwa przerywanie działania, upewnij się, że `count` jest ściśle mniejsza niż długość buforu, lub użyj `_TRUNCATE`.  
  
 W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vsntprintf_s`|`_vsnprintf_s`|`_vsnprintf_s`|`_vsnwprintf_s`|  
|`_vsntprintf_s_l`|`_vsnprintf_s_l`|`_vsnprintf_s_l`|`_vsnwprintf_s_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|----------------------|  
|`vsnprintf_s`|\<stdio.h > i \<stdarg.h >|\<VarArgs.h > *|  
|`_vsnprintf_s`, `_vsnprintf_s_l`|\<stdio.h > i \<stdarg.h >|\<VarArgs.h > *|  
|`_vsnwprintf_s`, `_vsnwprintf_s_l`|\<stdio.h > lub \<wchar.h >, a \<stdarg.h >|\<VarArgs.h > *|  
  
 \*Wymagany w przypadku zgodności UNIX V.  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_vsnprintf_s.cpp  
#include <stdio.h>  
#include <wtypes.h>  
  
void FormatOutput(LPCSTR formatstring, ...)   
{  
   int nSize = 0;  
   char buff[10];  
   memset(buff, 0, sizeof(buff));  
   va_list args;  
   va_start(args, formatstring);  
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);  
   printf("nSize: %d, buff: %s\n", nSize, buff); 
   va_end(args); 
}  
  
int main() {  
   FormatOutput("%s %s", "Hi", "there");  
   FormatOutput("%s %s", "Hi", "there!");  
   FormatOutput("%s %s", "Hi", "there!!");  
}  
```  
  
```Output  
nSize: 8, buff: Hi there  
nSize: 9, buff: Hi there!  
nSize: -1, buff: Hi there!  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [vprintf — funkcje](../../c-runtime-library/vprintf-functions.md)   
 [fprintf —, _fprintf_l —, fwprintf — _fwprintf_l —](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l —, wprintf, _wprintf_l —](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, _sprintf_l —, swprintf —, _swprintf_l —, \__swprintf_l —](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)