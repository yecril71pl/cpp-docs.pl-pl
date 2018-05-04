---
title: _putenv_s —, _wputenv_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
dev_langs:
- C++
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e84d7a68530a748c9b1ad7c553fad80ed4e7c86b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="putenvs-wputenvs"></a>_putenv_s, _wputenv_s

Tworzy, modyfikuje lub usuwa zmienne środowiskowe. Są to wersje [_putenv —, _wputenv —](putenv-wputenv.md) , ale ma ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Wartość do ustawienia zmiennej środowiskowej.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0 w przypadku powodzenia lub kod błędu.

### <a name="error-conditions"></a>Warunki błędów

|*nazwa_zmiennej*|*value_string*|Wartość zwracana|
|------------|-------------|------------------|
|**NULL**|wszystkie|**EINVAL —**|
|wszystkie|**NULL**|**EINVAL —**|

Jeśli jeden z warunków błąd wystąpi, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają **einval —** i ustaw **errno** do **einval —**.

## <a name="remarks"></a>Uwagi

**_Putenv_s —** funkcja dodaje nowe zmienne środowiskowe lub modyfikuje wartości istniejących zmiennych środowiskowych. Zmienne środowiskowe definiują środowisko, w którym proces jest wykonywany (na przykład domyślna ścieżka wyszukiwania dla bibliotek, które mają być połączone z programem). **_wputenv_s —** jest wersja znaków dwubajtowych **_putenv_s —**; *envstring* argument **_wputenv_s —** jest ciągiem znaków dwubajtowych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*nazwa_zmiennej* to nazwa zmiennej środowiskowej, które mają być dodane lub zmodyfikowane i *value_string* jest wartość zmiennej. Jeśli *nazwa_zmiennej* jest już częścią środowiska, jego wartość jest zamieniana *value_string*; w przeciwnym razie nowy *nazwa_zmiennej* zmienną i jej *value_string*  zostaną dodane do środowiska. Można usunąć zmienną ze środowiska, określając ciąg pusty (to znaczy "") dla *value_string*.

**_putenv_s —** i **_wputenv_s —** wpływu na środowisko lokalne dla bieżącego procesu; nie można używać ich do zmodyfikowania polecenie poziomu środowiska. Funkcje te działają tylko dla struktury danych, które są dostępne do biblioteki czasu wykonywania, a nie na środowisko "segment", który system operacyjny tworzy dla procesu. Gdy zakończenie bieżącego procesu, środowisko wraca do poziomu procesu wywołującego, które w większości przypadków jest to poziom systemu operacyjnego. Jednak modyfikacji środowiska mogą zostać przekazane do nowych procesów, które są tworzone przez **_spawn**, **_exec —**, lub **systemu**, te nowe procesy i nowe elementy, które są dodane przez **_putenv_s —** i **_wputenv_s —**.

Nie należy zmieniać wpis środowiska bezpośrednio; Zamiast tego należy użyć **_putenv_s —** lub **_wputenv_s —** je zmienić. W szczególności bezpośrednio zwalnianie elementów **_environ — []** globalne tablicy może spowodować nieprawidłowe pamięci, należy się zająć.

**getenv —** i **_putenv_s —** użyj zmiennej globalnej **_environ —** dostępu do tabeli środowiska; **_wgetenv —** i **_wputenv_s —** użyj **_wenviron —**. **_putenv_s —** i **_wputenv_s —** może zmienić wartość **_environ —** i **_wenviron —**, a tym samym unieważnienie *envp —*argument **głównego** i **_wenvp** argument **wmain**. W związku z tym jest bezpieczniejsze w użyciu **_environ —** lub **_wenviron —** można uzyskać dostępu do informacji o środowisku. Aby uzyskać więcej informacji na temat relacji między **_putenv_s —** i **_wputenv_s —** do zmiennych globalnych, zobacz [_environ —, _wenviron —](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv_s —** i **_getenv_s** rodzin funkcje nie są wątkowo. **_getenv_s** może zwracać wskaźnik ciągu podczas **_putenv_s —** modyfikowanie ciągu i spowodować losowe awarie. Upewnij się, że wywołania te funkcje są zsynchronizowane.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Dla przykładu, który przedstawia sposób użycia **_putenv_s —**, zobacz [getenv_s —, _wgetenv_s —](getenv-s-wgetenv-s.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
