---
title: _putenv —, _wputenv — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc7841963584bef19faf60de0112eeea25cb7ffd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403976"
---
# <a name="putenv-wputenv"></a>_putenv, _wputenv

Tworzy, modyfikuje lub usuwa zmienne środowiskowe. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_putenv_s —, _wputenv_s —](putenv-s-wputenv-s.md).

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

**_Putenv —** funkcja dodaje nowe zmienne środowiskowe lub modyfikuje wartości istniejących zmiennych środowiskowych. Zmienne środowiskowe definiują środowisko, w którym proces jest wykonywany (na przykład domyślna ścieżka wyszukiwania dla bibliotek, które mają być połączone z programem). **_wputenv —** jest wersja znaków dwubajtowych **_putenv —**; *envstring* argument **_wputenv —** jest ciągiem znaków dwubajtowych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv —**|**_putenv**|**_putenv**|**_wputenv**|

*Envstring* argument musi być wskaźnikiem do ciągu w postaci *nazwa_zmiennej*=*value_string*, gdzie *nazwa_zmiennej* jest Nazwa zmiennej środowiskowej, które mają być dodane lub zmodyfikowane i *value_string* jest wartość zmiennej. Jeśli *nazwa_zmiennej* jest już częścią środowiska, jego wartość jest zamieniana *value_string*; w przeciwnym razie nowy *nazwa_zmiennej* zmienną i jej *value_string*  wartości zostaną dodane do środowiska. Można usunąć zmienną ze środowiska, określając pustą *value_string*, lub innymi słowy, określając tylko *nazwa_zmiennej*=.

**_putenv —** i **_wputenv —** wpływu na środowisko lokalne dla bieżącego procesu; nie można używać ich do zmodyfikowania polecenie poziomu środowiska. Oznacza to, że funkcje te działają tylko na dostęp do biblioteki wykonawczej struktury danych, a nie na segment środowiska tworzone przez system operacyjny dla procesu. Gdy zakończenie bieżącego procesu, środowisko wraca do poziomu procesu wywołującego (w większości przypadków poziomu systemu operacyjnego). Jednak modyfikacji środowiska mogą być przekazywane wszystkie nowe procesy utworzone przez **_spawn**, **_exec —**, lub **systemu**, te nowe procesy i wszelkie nowe elementy dodane przez **_putenv —** i **_wputenv —**.

Nie należy zmieniać wpis środowiska bezpośrednio: Użyj **_putenv —** lub **_wputenv —** je zmienić. W szczególności zwalnianie bezpośrednie elementy **_environ — []** globalne tablicy może doprowadzić do nieprawidłowej pamięci adresowane.

**getenv —** i **_putenv —** użyj zmiennej globalnej **_environ —** dostępu do tabeli środowiska; **_wgetenv —** i **_wputenv —** użyj **_wenviron —**. **_putenv —** i **_wputenv —** może zmieniać wartość **_environ —** i **_wenviron —**, w związku z tym unieważnienia **_envp** argument **głównego** i **_wenvp** argument **wmain**. W związku z tym jest bezpieczniejsze w użyciu **_environ —** lub **_wenviron —** można uzyskać dostępu do informacji o środowisku. Aby uzyskać więcej informacji na temat relacji programu **_putenv —** i **_wputenv —** do zmiennych globalnych, zobacz [_environ —, _wenviron —](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv —** i **_getenv** rodzin funkcje nie są wątkowo. **_getenv** może zwracać wskaźnik ciągu podczas **_putenv —** modyfikuje ciągu znaków powoduje losowe awarie. Upewnij się, że wywołania te funkcje są zsynchronizowane.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Przykładowe zastosowania **_putenv —**, zobacz [getenv —, _wgetenv —](getenv-wgetenv.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
