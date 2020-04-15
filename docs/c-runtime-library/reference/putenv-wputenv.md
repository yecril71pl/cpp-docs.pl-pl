---
title: _putenv, _wputenv
ms.date: 4/2/2020
api_name:
- _putenv
- _wputenv
- _o__putenv
- _o__wputenv
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
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
ms.openlocfilehash: 3e74959e6c6cdb2e27ce0d68ba40d02d64949904
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333039"
---
# <a name="_putenv-_wputenv"></a>_putenv, _wputenv

Tworzy, modyfikuje lub usuwa zmienne środowiskowe. Dostępne są bezpieczniejsze wersje tych funkcji; patrz [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _putenv(
   const char *envstring
);
int _wputenv(
   const wchar_t *envstring
);
```

### <a name="parameters"></a>Parametry

*envstring*<br/>
Definicja ciągu środowiska.

## <a name="return-value"></a>Wartość zwracana

Zwraca 0, jeśli zakończy się pomyślnie lub -1 w przypadku błędu.

## <a name="remarks"></a>Uwagi

Funkcja **_putenv** dodaje nowe zmienne środowiskowe lub modyfikuje wartości istniejących zmiennych środowiskowych. Zmienne środowiskowe definiują środowisko, w którym wykonywany jest proces (na przykład domyślna ścieżka wyszukiwania bibliotek połączonych z programem). **_wputenv** jest szerokoznakową wersją **_putenv**; *envstring* argument do **_wputenv** jest ciągiem znaków o szerokich znakach.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

*Envstring* argument musi być wskaźnikiem do ciągu *warname*=formularza*value_string*, gdzie *varname* jest nazwą zmiennej środowiskowej, która ma zostać dodana lub zmodyfikowana, a *value_string* jest wartością zmiennej. Jeśli *nazwa warname* jest już częścią środowiska, jego wartość jest zastępowana *przez value_string*; w przeciwnym razie nowa *zmienna warname* i jej *value_string* wartość są dodawane do środowiska. Zmienną ze środowiska można usunąć, określając pustą *value_string*lub innymi słowy, określając tylko *nazwę warname*=.

**_putenv** i **_wputenv** mieć wpływ tylko na środowisko, które jest lokalne dla bieżącego procesu; nie można ich używać do modyfikowania środowiska na poziomie polecenia. Oznacza to, że te funkcje działają tylko na strukturach danych dostępnych dla biblioteki w czasie wykonywania, a nie w segmencie środowiska utworzonym dla procesu przez system operacyjny. Po zakończeniu bieżącego procesu środowisko powraca do poziomu procesu wywołującego (w większości przypadków na poziomie systemu operacyjnego). Jednak zmodyfikowane środowisko może być przekazywane do wszystkich nowych procesów utworzonych przez **_spawn,** **_exec**lub **system**, a te nowe procesy otrzymują nowe elementy dodane przez **_putenv** i **_wputenv.**

Nie należy zmieniać wpisu środowiska bezpośrednio: zamiast tego użyj **_putenv** lub **_wputenv,** aby go zmienić. W szczególności bezpośrednie zwalnianie elementów **tablicy globalnej _environ[]** może prowadzić do rozwiązania nieprawidłowej pamięci.

**getenv** i **_putenv** korzystają z **globalnej** zmiennej _environ, aby uzyskać dostęp do tabeli środowiska; **_wgetenv** i **_wputenv** używają **_wenviron**. **_putenv** i **_wputenv** mogą zmienić wartość **_environ** i **_wenviron,** unieważniając w ten sposób argument **_envp** na **główny** i **argument _wenvp** na **wmain**. W związku z tym bezpieczniej jest używać **_environ** lub **_wenviron** dostępu do informacji o środowisku. Aby uzyskać więcej informacji na temat relacji **_putenv** i **_wputenv** ze zmiennymi globalnymi, zobacz [_environ _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_putenv** i **_getenv** rodzin funkcji nie są bezpieczne dla wątków. **_getenv** może zwrócić wskaźnik ciągu, podczas gdy **_putenv** modyfikuje ciąg, powodując losowe błędy. Upewnij się, że wywołania tych funkcji są synchronizowane.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putenv**|\<>|
|**_wputenv**|\<> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Aby uzyskać przykład użycia **_putenv**, zobacz [getenv, _wgetenv](getenv-wgetenv.md).

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
