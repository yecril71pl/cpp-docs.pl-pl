---
title: _putenv, _wputenv
ms.date: 11/04/2016
apiname:
- _putenv
- _wputenv
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
ms.openlocfilehash: 952a4d62f6ceb6b689091ac09f6ca338d0b10864
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432516"
---
# <a name="putenv-wputenv"></a>_putenv, _wputenv

Tworzy, modyfikuje lub usuwa zmienne środowiskowe. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [_putenv_s, _wputenv_s —](putenv-s-wputenv-s.md).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

Zwraca 0 w przypadku powodzenia lub wartość -1 w przypadku błędu.

## <a name="remarks"></a>Uwagi

**_Putenv** funkcji dodaje nowe zmienne środowiskowe lub modyfikuje wartości istniejących zmiennych środowiskowych. Zmienne środowiskowe definiują środowisko, w którym proces działa (na przykład domyślna ścieżka wyszukiwania dla bibliotek musi być połączona z programem). **_wputenv —** to wersja znaku dwubajtowego **_putenv**; *envstring* argument **_wputenv —** jest ciągiem znaku dwubajtowego.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv —**|**_putenv**|**_putenv**|**_wputenv**|

*Envstring* argument musi być wskaźnikiem do ciągu w postaci *nazwa_zmiennej*=*value_string*, gdzie *nazwa_zmiennej* jest Nazwa zmiennej środowiskowej, aby być dodane lub zmodyfikowane i *value_string* jest wartość zmiennej. Jeśli *nazwa_zmiennej* jest już częścią środowiska, jej wartość jest zastępowana przez *value_string*; w przeciwnym razie nowy *nazwa_zmiennej* zmienna i jej *value_string*  wartości są dodawane do środowiska. Można usunąć zmienną ze środowiska przez określenie pustego *value_string*, lub innymi słowy, określając tylko *nazwa_zmiennej*=.

**_putenv** i **_wputenv —** wpływu na środowisko lokalne dla bieżącego procesu; nie można ich używać do modyfikowania środowiska poziomie polecenia. Oznacza to funkcje te działają tylko na dostęp do biblioteki wykonawczej struktury danych, a nie na segmencie środowiska dla procesu utworzonego przez system operacyjny. Gdy bieżący proces kończy działanie, środowiska powraca do poziomu procesu wywołującego (w większości przypadków, poziom systemu operacyjnego). Jednak zmodyfikowane środowisko może być przekazywany do dowolnego nowego procesu utworzonego przez **_spawn**, **_exec**, lub **systemu**, a te nowe procesy uzyskują wszystkie nowe elementy dodane przez **_putenv** i **_wputenv —**.

Nie zmieniaj bezpośrednio wpisu środowiska: Użyj **_putenv** lub **_wputenv —** je zmienić. W szczególności, bezpośrednie zwalnianie elementów **[] _environ** globalnej tablicy może doprowadzić do nieprawidłowej pamięci są rozwiązane.

**getenv** i **_putenv** używają zmiennej globalnej **_environ** dostępu do tabeli środowiska; **_wgetenv —** i **_wputenv —** użyj **_wenviron**. **_putenv** i **_wputenv —** może zmienić wartość **_environ** i **_wenviron**, tym samym unieważniając **_envp** argument **głównego** i **_wenvp** argument **wmain**. Dlatego jest bezpieczniejsze w użyciu **_environ** lub **_wenviron** dostęp do informacji o środowisku. Aby uzyskać więcej informacji na temat relacji **_putenv** i **_wputenv —** ze zmiennymi globalnymi, zobacz [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv** i **_getenv** rodziny funkcji nie są wątkowo. **_getenv** może zwracać wskaźnik ciągu podczas **_putenv** modyfikuje ciąg, powodując błędy losowe. Upewnij się, że wywołania tych funkcji są synchronizowane.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h > lub \<wchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Przykład sposobu użycia **_putenv**, zobacz [getenv, _wgetenv —](getenv-wgetenv.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
