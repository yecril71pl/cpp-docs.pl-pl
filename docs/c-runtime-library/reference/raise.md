---
title: wywołaj
ms.date: 01/02/2018
api_name:
- raise
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- Raise
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.openlocfilehash: bed377bb46abac252381344f0b1cf4339815a16e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949682"
---
# <a name="raise"></a>wywołaj

Wysyła sygnał do programu wykonującego.

> [!NOTE]
> Nie należy używać tej metody do zamykania aplikacji Microsoft Store, z wyjątkiem scenariuszy testowania lub debugowania. Sposób programistyczny lub interfejs użytkownika służący do zamykania aplikacji ze sklepu nie są dozwolone zgodnie z [zasadami Microsoft Storeymi](/legal/windows/agreements/store-policies). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Składnia

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>Parametry

*SIG*<br/>
Sygnał, który ma zostać wywołany.

## <a name="return-value"></a>Wartość zwracana

Jeśli **to się** powiedzie, funkcja Return zwraca wartość 0. W przeciwnym razie zwraca wartość różną od zera.

## <a name="remarks"></a>Uwagi

Funkcja **podniesienia** wysyła *podpis* do programu wykonującego. Jeśli poprzednie wywołanie do **sygnału** zainstalowało funkcję obsługi sygnałów dla *SIG*, **Podnieś** wartość wykonuje tę funkcję. Jeśli nie zainstalowano żadnej funkcji programu obsługi, zostanie utworzona domyślna akcja skojarzona z wartością sygnału *SIG* , jak pokazano poniżej.

|wysłać|Znaczenie|Domyślny|
|------------|-------------|-------------|
|**SIGABRT**|Nietypowe zakończenie|Kończy program wywołujący z kodem zakończenia 3|
|**SIGFPE**|Błąd zmiennoprzecinkowy|Kończy program wywołujący|
|**SIGILL**|Niedozwolona instrukcja|Kończy program wywołujący|
|**SIGINT**|Przerwanie CTRL + C|Kończy program wywołujący|
|**SIGSEGV**|Niedozwolony dostęp do magazynu|Kończy program wywołujący|
|**SIGTERM**|Żądanie zakończenia wysłane do programu|Ignoruje sygnał|

Jeśli argument nie jest prawidłowym sygnałem, jak określono powyżej, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli nie obsłużono, funkcja ustawia **errno** na **EINVAL** i zwraca wartość różną od zera.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**raise**|\<signal.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[signal](signal.md)<br/>
