---
title: wywołaj
ms.date: 1/02/2018
apiname:
- raise
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- Raise
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.openlocfilehash: 68d1cc653b955e607648e4d30562d2b77e3520e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358063"
---
# <a name="raise"></a>wywołaj

Wysyła sygnał do wykonywania programu.

> [!NOTE]
> Nie należy używać tej metody do zamykania aplikacji Microsoft Store, z wyjątkiem testowania i debugowania scenariuszy. Sposoby Programmatic lub interfejs użytkownika, zamknąć Store app nie są dozwolone zgodnie z opisem w [zasady Microsoft Store](/legal/windows/agreements/store-policies). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Składnia

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>Parametry

*sig*<br/>
Sygnał należy podnieść.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **podnieść** zwraca wartość 0. W przeciwnym razie zwraca wartość różną od zera.

## <a name="remarks"></a>Uwagi

**Podnieść** funkcji wysyła *sig* do wykonywania programu. Jeśli poprzednie wywołanie **sygnału** zainstalowano funkcję obsługi sygnałów dla *sig*, **podnieść** wykonuje tę funkcję. Brak obsługi funkcji po zainstalowaniu, akcja domyślna skojarzona z wartością sygnału *sig* jest pobierana w następujący sposób.

|Sygnał|Znaczenie|Domyślny|
|------------|-------------|-------------|
|**SIGABRT**|Nienormalne zakończenie|Kończy program wywołujący kodem zakończenia 3|
|**SIGFPE**|Błąd wartości zmiennoprzecinkowej|Kończy program wywołujący|
|**SIGILL**|Niedozwolona instrukcja|Kończy program wywołujący|
|**SIGINT**|CTRL + C przerywa|Kończy program wywołujący|
|**SIGSEGV**|Niedozwolony dostęp do magazynu|Kończy program wywołujący|
|**SIGTERM**|Zakończenie żądania wysłanego do programu|Ignoruje sygnał|

Jeśli argument nie jest prawidłowym sygnałem, jak określono powyżej, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli nie jest obsługiwana, funkcja ustawia **errno** do **EINVAL** i zwraca wartość różną od zera.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**raise**|\<signal.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[signal](signal.md)<br/>
