---
title: _putenv, _wputenv
ms.date: 11/04/2016
api_name:
- _putenv
- _wputenv
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
ms.openlocfilehash: 8fe699a476ea1dd09a6ce9922294bce398df16b2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949885"
---
# <a name="_putenv-_wputenv"></a>_putenv, _wputenv

Tworzy, modyfikuje lub usuwa zmienne środowiskowe. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

Zwróć wartość 0, jeśli w przypadku błędu wystąpi sukces lub-1.

## <a name="remarks"></a>Uwagi

Funkcja **_putenv** dodaje nowe zmienne środowiskowe lub modyfikuje wartości istniejących zmiennych środowiskowych. Zmienne środowiskowe definiują środowisko, w którym jest wykonywany proces (na przykład domyślną ścieżkę wyszukiwania dla bibliotek, które mają być połączone z programem). **_wputenv** to dwubajtowa wersja **_putenv**; argument *envstring* **_wputenv** jest ciągiem znaków dwubajtowych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

Argument *envstring* musi być wskaźnikiem do ciągu w postaci *nazwa_zmiennej*=*value_string*, gdzie *nazwa_zmiennej* to nazwa zmiennej środowiskowej, która ma zostać dodana lub zmodyfikowana, a *value_string* to zmienna wartościami. Jeśli *nazwa_zmiennej* jest już częścią środowiska, jej wartość jest zastępowana przez *value_string*; w przeciwnym razie Nowa zmienna *nazwa_zmiennej* i jej wartość *value_string* są dodawane do środowiska. Możesz usunąć zmienną ze środowiska, określając pustą *value_string*lub innymi słowy, określając tylko wartość *nazwa_zmiennej*=.

**_putenv** i **_wputenv** mają wpływ tylko na środowisko, które jest lokalne dla bieżącego procesu; nie można ich używać do modyfikowania środowiska poziomu polecenia. Oznacza to, że funkcje te działają tylko na strukturach danych dostępnych dla biblioteki wykonawczej, a nie w segmencie środowiska utworzonym dla procesu przez system operacyjny. Gdy bieżący proces zakończy działanie, środowisko powraca do poziomu procesu wywołującego (w większości przypadków jest to poziom systemu operacyjnego). Zmodyfikowane środowisko może być jednak przesyłane do każdego nowego procesu utworzonego przez **_spawn**, **_exec**lub **system**, a te nowe procesy uzyskują nowe elementy dodane przez **_putenv** i **_wputenv**.

Nie zmieniaj bezpośrednio wpisu środowiska: zamiast tego należy użyć **_putenv** lub **_wputenv** , aby go zmienić. W szczególności bezpośrednie zwalnianie elementów tablicy globalnej **_environ []** może prowadzić do nieprawidłowej ilości pamięci.

**getenv** i **_putenv** używają zmiennej globalnej **_environ** , aby uzyskać dostęp do tabeli środowiskowej. **_wgetenv** i **_wputenv** używają **_wenviron**. **_putenv** i **_wputenv** mogą zmienić wartość **_environ** i **_wenviron**, w ten sposób unieważnienie argumentu **_envp** do **głównego** i argumentu **_wenvp** do **wmain**. W związku z tym można bezpiecznie używać **_environ** lub **_wenviron** do uzyskiwania dostępu do informacji o środowisku. Aby uzyskać więcej informacji na temat relacji **_putenv** i **_wputenv** na zmienne globalne, zobacz [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Rodziny **_putenv** i **_getenv** funkcji nie są bezpieczne wątkowo. **_getenv** może zwrócić wskaźnik ciągu, podczas gdy **_putenv** modyfikuje ciąg, powodując błędy losowe. Upewnij się, że wywołania tych funkcji są zsynchronizowane.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<STDLIB. h > lub \<WCHAR. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem sposobu korzystania z **_putenv**, zobacz [getenv, _wgetenv](getenv-wgetenv.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
