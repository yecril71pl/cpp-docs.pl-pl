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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b38a3430274b2324e345be30ce9e38f0c2749fa3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338265"
---
# <a name="raise"></a>wywołaj

Wysyła sygnał do programu wykonującego.

> [!NOTE]
> Nie należy używać tej metody do zamykania aplikacji Microsoft Store, z wyjątkiem scenariuszy testowania lub debugowania. Sposób zamykania aplikacji ze Sklepu jest zabroniony zgodnie z [zasadami sklepu Microsoft Store.](/legal/windows/agreements/store-policies) Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej](/windows/uwp/launch-resume/app-lifecycle)systemu .

## <a name="syntax"></a>Składnia

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>Parametry

*Sig*<br/>
Sygnał do podniesienia.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, **podnieś** zwraca 0. W przeciwnym razie zwraca wartość niezerową.

## <a name="remarks"></a>Uwagi

Funkcja **podnoszenia** wysyła *sig* do programu wykonującego. Jeśli poprzednie wywołanie **sygnału** zainstalowało funkcję obsługi sygnału dla *sig,* **podnieś** wykonuje tę funkcję. Jeśli nie zainstalowano żadnej funkcji obsługi, podejmowana jest domyślna akcja skojarzona z wartością sygnału *sig* w następujący sposób.

|Sygnału|Znaczenie|Domyślne|
|------------|-------------|-------------|
|**SIGABRT ( SIGABRT )**|Nieprawidłowe rozwiązanie umowy|Kończy program wywołujący kodem zakończenia 3|
|**SIGFPE ( SIGFPE )**|Błąd zmiennoprzecinowy|Kończy program wywołujący|
|**SIGILL ( SIGILL )**|Nielegalne instrukcje|Kończy program wywołujący|
|**SIGINT ( SIGINT )**|Przerwanie CTRL+C|Kończy program wywołujący|
|**SIGSEGV ( SIGSEGV )**|Nielegalny dostęp do magazynu|Kończy program wywołujący|
|**SIGTERM ( SIGTERM )**|Żądanie zakończenia wysłane do programu|Ignoruje sygnał|

Jeśli argument nie jest prawidłowym sygnałem, jak określono powyżej, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w polu [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli nie jest obsługiwany, funkcja ustawia **errno** na **EINVAL** i zwraca wartość niezerową.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wywołaj**|\<> signal.h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[Przerwać](abort.md)<br/>
[sygnał](signal.md)<br/>
