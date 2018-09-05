---
title: wywoływanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1bc3f52b97159a9caba6f80b4798d9588ec341d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685911"
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

*SIG*<br/>
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
