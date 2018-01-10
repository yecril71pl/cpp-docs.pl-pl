---
title: "Zgłoś | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: raise
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
f1_keywords: Raise
dev_langs: C++
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1b7ec6c886c96bae93f511e54119500d58d6fea5
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="raise"></a>wywołaj

Wysyła sygnał do wykonywania programu.

> [!NOTE]
> Nie należy używać tej metody można zamknąć aplikację Microsoft Store, z wyjątkiem w testowania i debugowania scenariuszy. Programowe lub interfejsu użytkownika sposobów Zamknij aplikację sklepu nie są dozwolone zgodnie z [zasady Microsoft Store](http://go.microsoft.com/fwlink/?LinkId=865936). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej systemu Windows](http://go.microsoft.com/fwlink/p/?LinkId=865934).

## <a name="syntax"></a>Składnia

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>Parametry

*SIG*  
Sygnał do wywołania.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **podnieść** zwraca wartość 0. W przeciwnym wypadku zwraca wartość różną od zera.

## <a name="remarks"></a>Uwagi

**Podnieść** funkcji wysyła *sig* do wykonywania programu. Jeśli poprzednie wywołanie **sygnału** została zainstalowana funkcja obsługi sygnału, dla *sig*, **podnieść** wykonuje tej funkcji. Nie funkcji obsługi po zainstalowaniu, domyślna akcja skojarzone z wartością sygnału *sig* jest pobierana w następujący sposób.

|Sygnał|Znaczenie|Domyślny|
|------------|-------------|-------------|
|`SIGABRT`|Przerwania pracy|Kończy program wywołujący z kodem zakończenia 3|
|`SIGFPE`|Błąd liczb zmiennoprzecinkowych|Kończy program wywołujący|
|`SIGILL`|Niedozwolona instrukcja|Kończy program wywołujący|
|`SIGINT`|CTRL + C przerwania|Kończy program wywołujący|
|`SIGSEGV`|Dostępu do magazynu niedozwolony|Kończy program wywołujący|
|`SIGTERM`|Zakończenie żądania wysyłane do programu|Ignoruje sygnału|

Jeśli argument nie jest prawidłową sygnału określonych powyżej, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli nie jest obsługiwane, funkcja ustawia `errno` do `EINVAL` i zwraca wartość różną od zera.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**raise**|\<Signal.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)  
[abort](../../c-runtime-library/reference/abort.md)  
[signal](../../c-runtime-library/reference/signal.md)  
