---
title: _putenv_s, _wputenv_s
ms.date: 11/04/2016
api_name:
- _wputenv_s
- _putenv_s
api_location:
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
ms.openlocfilehash: b2de609314a12f626a21680b470bc8831eada2cb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949904"
---
# <a name="_putenv_s-_wputenv_s"></a>_putenv_s, _wputenv_s

Tworzy, modyfikuje lub usuwa zmienne środowiskowe. Są to wersje [_putenv, _wputenv,](putenv-wputenv.md) ale mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
errno_t _putenv_s(
   const char *varname,
   const char *value_string
);
errno_t _wputenv_s(
   const wchar_t *varname,
   const wchar_t *value_string
);
```

### <a name="parameters"></a>Parametry

*nazwa_zmiennej*<br/>
Nazwa zmiennej środowiskowej.

*value_string*<br/>
Wartość, dla której ma zostać ustawiona zmienna środowiskowa.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli powodzenie lub kod błędu.

### <a name="error-conditions"></a>Warunki błędów

|*nazwa_zmiennej*|*value_string*|Wartość zwracana|
|------------|-------------|------------------|
|**NULL**|Ile|**EINVAL**|
|Ile|**NULL**|**EINVAL**|

Jeśli wystąpi jeden z warunków błędów, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EINVAL** i ustawiają **errno** na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_putenv_s** dodaje nowe zmienne środowiskowe lub modyfikuje wartości istniejących zmiennych środowiskowych. Zmienne środowiskowe definiują środowisko, w którym jest wykonywany proces (na przykład domyślną ścieżkę wyszukiwania dla bibliotek, które mają być połączone z programem). **_wputenv_s** to dwubajtowa wersja **_putenv_s**; argument *envstring* **_wputenv_s** jest ciągiem znaków dwubajtowych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*nazwa_zmiennej* to nazwa zmiennej środowiskowej, która ma zostać dodana lub zmodyfikowana, a *value_string* to wartość zmiennej. Jeśli *nazwa_zmiennej* jest już częścią środowiska, jej wartość jest zastępowana przez *value_string*; w przeciwnym razie Nowa zmienna *nazwa_zmiennej* i jej *value_string* są dodawane do środowiska. Możesz usunąć zmienną ze środowiska, określając pusty ciąg (czyli "") dla *value_string*.

**_putenv_s** i **_wputenv_s** mają wpływ tylko na środowisko, które jest lokalne dla bieżącego procesu; nie można ich używać do modyfikowania środowiska poziomu polecenia. Funkcje te działają tylko na strukturach danych, które są dostępne dla biblioteki wykonawczej, a nie w środowisku "segment", który tworzy system operacyjny dla procesu. Po zakończeniu bieżącego procesu środowisko zostaje przywrócone do poziomu procesu wywołującego, co w większości przypadków jest poziomem systemu operacyjnego. Zmodyfikowane środowisko może być jednak przesyłane do każdego nowego procesu, który jest tworzony przez **_spawn**, **_exec**lub **system**, i te nowe procesy uzyskują nowe elementy, które są dodawane przez **_putenv_s** i **_wputenv_s**.

Nie zmieniaj bezpośrednio wpisu środowiska; Zamiast tego należy użyć **_putenv_s** lub **_wputenv_s** , aby go zmienić. W szczególności bezpośrednie zwalnianie elementów macierzy globalnej **_environ []** może spowodować nieprawidłową ilość pamięci.

**getenv** i **_putenv_s** używają zmiennej globalnej **_environ** , aby uzyskać dostęp do tabeli środowiskowej. **_wgetenv** i **_wputenv_s** używają **_wenviron**. **_putenv_s** i **_wputenv_s** mogą zmienić wartość **_environ** i **_wenviron**, a tym samym unieważnić argument *envp* do argumentu **Main** i **_wenvp** do **wmain**. W związku z tym można bezpiecznie używać **_environ** lub **_wenviron** do uzyskiwania dostępu do informacji o środowisku. Aby uzyskać więcej informacji na temat relacji **_putenv_s** i **_wputenv_s** ze zmiennymi globalnymi, zobacz [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Rodziny **_putenv_s** i **_getenv_s** funkcji nie są bezpieczne wątkowo. **_getenv_s** może zwrócić wskaźnik ciągu, podczas gdy **_putenv_s** modyfikuje ciąg i w związku z tym powoduje losowe błędy. Upewnij się, że wywołania tych funkcji są zsynchronizowane.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<STDLIB. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Aby uzyskać przykład, który pokazuje, jak używać **_putenv_s**, zobacz [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
