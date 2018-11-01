---
title: _putenv_s, _wputenv_s
ms.date: 11/04/2016
apiname:
- _wputenv_s
- _putenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: f675c2c0a2b12db3cce841dd0db9fa722393f1b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558954"
---
# <a name="putenvs-wputenvs"></a>_putenv_s, _wputenv_s

Tworzy, modyfikuje lub usuwa zmienne środowiskowe. Są to wersje [_putenv, _wputenv —](putenv-wputenv.md) , ale mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Nazwa zmiennej*<br/>
Nazwa zmiennej środowiskowej.

*value_string*<br/>
Wartość do ustawienia zmiennej środowiskowej.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli kończy się pomyślnie, lub kod błędu.

### <a name="error-conditions"></a>Warunki błędów

|*Nazwa zmiennej*|*value_string*|Wartość zwracana|
|------------|-------------|------------------|
|**NULL**|Wszystkie|**EINVAL**|
|Wszystkie|**NULL**|**EINVAL**|

Jeśli jeden z warunków błąd wystąpi, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EINVAL** i ustaw **errno** do **EINVAL**.

## <a name="remarks"></a>Uwagi

**_Putenv_s** funkcji dodaje nowe zmienne środowiskowe lub modyfikuje wartości istniejących zmiennych środowiskowych. Zmienne środowiskowe definiują środowisko, w którym proces działa (na przykład domyślna ścieżka wyszukiwania dla bibliotek musi być połączona z programem). **_wputenv_s —** to wersja znaku dwubajtowego **_putenv_s**; *envstring* argument **_wputenv_s —** jest ciągiem znaku dwubajtowego.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*nazwa_zmiennej* to nazwa zmiennej środowiskowej, aby być dodane lub zmodyfikowane i *value_string* jest wartość zmiennej. Jeśli *nazwa_zmiennej* jest już częścią środowiska, jej wartość jest zastępowana przez *value_string*; w przeciwnym razie nowy *nazwa_zmiennej* zmienna i jej *value_string*  są dodawane do środowiska. Można usunąć zmienną ze środowiska przez określenie pustego ciągu (czyli "") dla *value_string*.

**_putenv_s** i **_wputenv_s —** wpływu na środowisko lokalne dla bieżącego procesu; nie można ich używać do modyfikowania środowiska poziomie polecenia. Funkcje te działają tylko na struktur danych, które są dostępne dla biblioteki wykonawczej a nie na środowisko "segment", który system operacyjny tworzy proces. Gdy bieżący proces kończy działanie, środowiska powraca do poziomu procesu wywołującego, które w większości przypadków jest to poziom systemu operacyjnego. Jednak zmodyfikowane środowisko może być przekazywany w taki sposób, aby nowe procesy, które są tworzone przez **_spawn**, **_exec**, lub **systemu**, a te nowe procesy uzyskują wszystkie nowe elementy, które są dodane przez **_putenv_s** i **_wputenv_s —**.

Nie zmieniaj wpisu środowiska bezpośrednio; Zamiast tego należy użyć **_putenv_s** lub **_wputenv_s —** je zmienić. W szczególności, bezpośrednie zwalnianie elementów **[] _environ** globalnej tablicy może spowodować nieprawidłowe pamięci, należy się zająć.

**getenv** i **_putenv_s** używają zmiennej globalnej **_environ** dostępu do tabeli środowiska; **_wgetenv —** i **_wputenv_s —** użyj **_wenviron**. **_putenv_s** i **_wputenv_s —** może zmienić wartość **_environ** i **_wenviron**i tym samym unieważnić *envp*argument **głównego** i **_wenvp** argument **wmain**. Dlatego jest bezpieczniejsze w użyciu **_environ** lub **_wenviron** dostęp do informacji o środowisku. Aby uzyskać więcej informacji na temat relacji między **_putenv_s** i **_wputenv_s —** ze zmiennymi globalnymi, zobacz [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv_s** i **_getenv_s** rodziny funkcji nie są wątkowo. **_getenv_s** może zwracać wskaźnik ciągu podczas **_putenv_s** jest modyfikuje ciąg, a także spowodować błędy losowe. Upewnij się, że wywołania tych funkcji są synchronizowane.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Dla przykładu, który pokazuje, jak używać **_putenv_s**, zobacz [getenv_s —, _wgetenv_s —](getenv-s-wgetenv-s.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
