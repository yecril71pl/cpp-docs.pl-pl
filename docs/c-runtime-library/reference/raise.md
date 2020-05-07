---
title: wywołaj
ms.date: 4/2/2020
api_name:
- raise
- _o_raise
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 81b92404603820948a384b6ad33421251a27c13c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919547"
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

|Wysłać|Znaczenie|Domyślny|
|------------|-------------|-------------|
|**SIGABRT**|Nietypowe zakończenie|Kończy program wywołujący z kodem zakończenia 3|
|**SIGFPE**|Błąd zmiennoprzecinkowy|Kończy program wywołujący|
|**SIGILL**|Niedozwolona instrukcja|Kończy program wywołujący|
|**SIGINT**|Przerwanie CTRL + C|Kończy program wywołujący|
|**SIGSEGV**|Niedozwolony dostęp do magazynu|Kończy program wywołujący|
|**SIGTERM**|Żądanie zakończenia wysłane do programu|Ignoruje sygnał|

Jeśli argument nie jest prawidłowym sygnałem, jak określono powyżej, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli nie obsłużono, funkcja ustawia **errno** na **EINVAL** i zwraca wartość różną od zera.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wywołaj**|\<sygnał. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Proces i kontrola środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[Anuluj](abort.md)<br/>
[sygnał](signal.md)<br/>
