---
title: _putenv_s, _wputenv_s
ms.date: 4/2/2020
api_name:
- _wputenv_s
- _putenv_s
- _o__putenv_s
- _o__wputenv_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: f0164feed05b409ba29ca713f11f4f3323dbaac3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338389"
---
# <a name="_putenv_s-_wputenv_s"></a>_putenv_s, _wputenv_s

Tworzy, modyfikuje lub usuwa zmienne środowiskowe. Są to wersje [_putenv, _wputenv](putenv-wputenv.md) ale mają ulepszenia zabezpieczeń, zgodnie z opisem w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Varname*<br/>
Nazwa zmiennej środowiskowej.

*value_string*<br/>
Wartość, na która ma być ustawiona zmienna środowiskowa.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli się powiedzie, lub kod błędu.

### <a name="error-conditions"></a>Warunki błędu

|*Varname*|*value_string*|Wartość zwracana|
|------------|-------------|------------------|
|**Null**|Wszelki|**Einval**|
|Wszelki|**Null**|**Einval**|

Jeśli wystąpi jeden z warunków błędu, te funkcje wywołać nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, funkcje te zwracają **EINVAL** i ustawić **errno** do **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_putenv_s** dodaje nowe zmienne środowiskowe lub modyfikuje wartości istniejących zmiennych środowiskowych. Zmienne środowiskowe definiują środowisko, w którym wykonywany jest proces (na przykład domyślna ścieżka wyszukiwania bibliotek połączonych z programem). **_wputenv_s** jest szerokoznakową wersją **_putenv_s**; *envstring* argument do **_wputenv_s** jest ciągiem znaków o szerokich znakach.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*varname* jest nazwą zmiennej środowiskowej, która ma zostać dodana lub zmodyfikowana, a *value_string* jest wartością zmiennej. Jeśli *nazwa warname* jest już częścią środowiska, jego wartość jest zastępowana *przez value_string*; w przeciwnym razie nowa *zmienna warname* i jej *value_string* są dodawane do środowiska. Zmienną ze środowiska można usunąć, określając pusty ciąg (czyli "") dla *value_string*.

**_putenv_s** i **_wputenv_s** mieć wpływ tylko na środowisko, które jest lokalne dla bieżącego procesu; nie można ich używać do modyfikowania środowiska na poziomie polecenia. Te funkcje działają tylko na strukturach danych, które są dostępne dla biblioteki w czasie wykonywania, a nie w środowisku "segment", który system operacyjny tworzy dla procesu. Po zakończeniu bieżącego procesu środowisko powraca do poziomu procesu wywołującego, który w większości przypadków jest na poziomie systemu operacyjnego. Jednak zmodyfikowane środowisko może być przekazywane do wszystkich nowych procesów, które są tworzone przez **_spawn** **, _exec**lub **system**, a te nowe procesy uzyskać wszelkie nowe elementy, które są dodawane przez **_putenv_s** i **_wputenv_s**.

Nie należy zmieniać wpisu środowiska bezpośrednio; zamiast tego użyj **_putenv_s** lub **_wputenv_s,** aby go zmienić. W szczególności bezpośrednie zwalnianie elementów **tablicy globalnej _environ[]** może spowodować, że zostanie rozwiązana nieprawidłowa pamięć.

**getenv** i **_putenv_s** korzystają z globalnej zmiennej **_environ,** aby uzyskać dostęp do tabeli środowiska; **_wgetenv** i **_wputenv_s** używają **_wenviron**. **_putenv_s** i **_wputenv_s** mogą zmienić wartość **_environ** i **_wenviron,** a tym samym unieważnić argument *envp* do **głównego** i **argumentu _wenvp** **wmain**. W związku z tym bezpieczniej jest używać **_environ** lub **_wenviron** dostępu do informacji o środowisku. Aby uzyskać więcej informacji na temat relacji **_putenv_s** i **_wputenv_s** ze zmiennymi globalnymi, zobacz [_environ _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_putenv_s** i **_getenv_s** rodzin funkcji nie są bezpieczne dla wątków. **_getenv_s** może zwrócić wskaźnik ciągu, podczas gdy **_putenv_s** modyfikuje ciąg, a tym samym powodować losowe błędy. Upewnij się, że wywołania tych funkcji są synchronizowane.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putenv_s**|\<>|
|**_wputenv_s**|\<> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Aby uzyskać przykład, który pokazuje, jak używać **_putenv_s**, zobacz [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
