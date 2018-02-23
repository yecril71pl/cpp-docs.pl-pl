---
title: strftime, wcsftime, _strftime_l, _wcsftime_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcsftime
- strftime
- wcsftime
dev_langs:
- C++
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 990dab2b4cedbdb464a2e546a4c83758cb46c89a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="strftime-wcsftime-strftimel-wcsftimel"></a>strftime, wcsftime, _strftime_l, _wcsftime_l
Format ciągu czasu.  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t strftime(  
   char *strDest,  
   size_t maxsize,  
   const char *format,  
   const struct tm *timeptr   
);  
size_t _strftime_l(  
   char *strDest,  
   size_t maxsize,  
   const char *format,  
   const struct tm *timeptr,  
   _locale_t locale  
);  
size_t wcsftime(  
   wchar_t *strDest,  
   size_t maxsize,  
   const wchar_t *format,  
   const struct tm *timeptr   
);  
size_t _wcsftime_l(  
   wchar_t *strDest,  
   size_t maxsize,  
   const wchar_t *format,  
   const struct tm *timeptr,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `strDest`  
 Ciąg w danych wyjściowych.  
  
 `maxsize`  
 Rozmiar `strDest` buforu, mierzony w znakach (`char` lub `wchart_t`).  
  
 `format`  
 Ciąg kontroli formatu.  
  
 `timeptr`  
 `tm` Struktura danych.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `strftime` Zwraca liczbę znaków, umieszczone w `strDest` i `wcsftime` zwraca odpowiednia liczba znaki dwubajtowe.  
  
 Jeśli całkowita liczba znaków, w tym zakończenia wartość null, jest więcej niż `maxsize`, oba `strftime` i `wcsftime` zwrócić 0 i zawartość `strDest` jest nieokreślony.  
  
 Liczba znaków w `strDest` jest równa liczbie znaków literału `format` oraz znaków, które mogą być dodawane do `format` za pośrednictwem kody formatowania. Trwa przerywanie działania null ciągu nie jest liczony w wartości zwracanej.  
  
## <a name="remarks"></a>Uwagi  
 `strftime` i `wcsftime` funkcji format `tm` wartości w czasie `timeptr` zgodnie z podane `format` argumentu i zapisać wynik w buforze `strDest`. Co najwyżej `maxsize` znaki są umieszczane w ciągu. Opis pól w `timeptr` struktury, zobacz [asctime —](../../c-runtime-library/reference/asctime-wasctime.md). `wcsftime` jest to równoważne znaków dwubajtowych `strftime`; jej argument ciągu wskaźnik wskazuje ciąg znaków dwubajtowych. Funkcje te działają tak samo w przeciwnym razie wartość.  
  
> [!NOTE]
>  W wersjach przed Visual C++ 2005, opisane dokumentacji `format` parametr `wcsftime` jako mający typ danych `const wchar_t *`, ale rzeczywistego wykonania `format` — typ danych został `const char *`. Implementacja `format` — typ danych została zaktualizowana w celu uwzględnienia w poprzednim i bieżącym dokumentacji, oznacza to, `const wchar_t *`.  
  
 Ta funkcja weryfikuje jego parametrów. Jeśli `strDest`, `format`, lub `timeptr` jest wskaźnika o wartości null, lub jeśli `tm` struktury danych opisany w `timeptr` jest nieprawidłowy (na przykład, jeśli zawiera ona poza zakresem wartości dla daty lub godziny), lub, jeśli `format` ciągu zawiera nieprawidłowy kod formatowania, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca wartość 0 i zestawy `errno` do `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsftime`|`strftime`|`strftime`|`wcsftime`|  
  
 `format` Argument składa się z jednego lub więcej kodów; ponieważ w `printf`, formatowania kody są poprzedzone znakiem procentu (`%`). Znaki, które nie rozpoczynają się `%` zostaną skopiowane bez zmian do `strDest`. `LC_TIME` Kategorii bieżące ustawienia regionalne wpływa na dane wyjściowe formatowanie `strftime`. (Aby uzyskać więcej informacji na temat `LC_TIME`, zobacz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).) Funkcje bez `_l` aktualnie ustawione używać sufiksu ustawień regionalnych. Wersje tych funkcji z `_l` sufiks są identyczne z tą różnicą, że zająć ustawień regionalnych jako parametr i używać go zamiast aktualnie ustawione ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Formatowanie kodów dla `strftime` wymienionych poniżej:  
  
 `%a`  
 Nazwa skrócona dnia tygodnia  
  
 `%A`  
 Pełna nazwa dnia tygodnia  
  
 `%b`  
 Skrócona nazwa miesiąca  
  
 `%B`  
 Pełna nazwa miesiąca  
  
 `%c`  
 Data i godzina reprezentacji odpowiednie dla ustawień regionalnych  
  
 `%d`  
 Dzień miesiąca jako liczbę dziesiętną (01-31)  
  
 `%H`  
 Godzina w formacie 24-godzinnym (00 - 23)  
  
 `%I`  
 Godzina w formacie 12-godzinnym (01-12)  
  
 `%j`  
 Dzień roku jako liczbę dziesiętną (001-366)  
  
 `%m`  
 Miesiąc jako liczbę dziesiętną (01-12)  
  
 `%M`  
 Minuta jako liczbę dziesiętną (00 - 59)  
  
 `%p`  
 Bieżące ustawienia regionalne godzinę. wskaźnik 12-godzinnym.  
  
 `%S`  
 Drugi jako liczbę dziesiętną (00 - 59)  
  
 `%U`  
 Tydzień roku jako liczbę dziesiętną niedziela pierwszy dzień tygodnia (00 – 53)  
  
 `%w`  
 Dzień tygodnia jako liczbę dziesiętną (0 – 6; Niedziela wynosi 0)  
  
 `%W`  
 Tydzień roku jako liczbę dziesiętną poniedziałek pierwszy dzień tygodnia (00 – 53)  
  
 `%x`  
 Data reprezentację bieżące ustawienia regionalne  
  
 `%X`  
 Czas reprezentację bieżące ustawienia regionalne  
  
 `%y`  
 Rok bez wieku jako liczbę dziesiętną (00 – 99)  
  
 `%Y`  
 Rok ze stuleciem jako liczbę dziesiętną  
  
 `%z, %Z`  
 Nazwa strefy czasowej albo skrót strefy czasowej, w zależności od ustawień rejestru; żadne znaki, jeśli strefa czasowa jest nieznany  
  
 `%%`  
 Znak procentu  
  
 Podobnie jak w `printf` funkcji `#` flagi może prefiksu formatowania kodu. W takim przypadku znaczenie formatowania kodu zostanie zmieniona w następujący sposób.  
  
|Formatowanie kodu|Znaczenie|  
|-----------------|-------------|  
|`%#a, %#A, %#b, %#B, %#p, %#X, %#z, %#Z, %#%`|`#` Flaga jest ignorowana.|  
|`%#c`|Long Data i godzina reprezentacji odpowiednie dla bieżących ustawień regionalnych. Na przykład: "Wtorek, marca 14, 1995 r., 12:41:29".|  
|`%#x`|Reprezentacja daty długiej odpowiednie do bieżących ustawień regionalnych. Na przykład: "Wtorek, 14 marca 1995".|  
|`%#d, %#H, %#I, %#j, %#m, %#M, %#S, %#U, %#w, %#W, %#y, %#Y`|Usuń zer (jeśli istnieje).|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`strftime`|\<time.h>|  
|`wcsftime`|\<Time.h > lub \<wchar.h >|  
|`_strftime_l`|\<time.h>|  
|`_wcsftime_l`|\<Time.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [czas](../../c-runtime-library/reference/time-time32-time64.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setLocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll — funkcje](../../c-runtime-library/strcoll-functions.md)   
 [strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)