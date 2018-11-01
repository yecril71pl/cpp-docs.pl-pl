---
title: __security_init_cookie
ms.date: 11/04/2016
apiname:
- __security_init_cookie
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
- security_init_cookie
- __security_init_cookie
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
ms.openlocfilehash: c7b25e05b4574a7b397cd07d55000a5e53db58f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573618"
---
# <a name="securityinitcookie"></a>__security_init_cookie

Inicjuje plik cookie zabezpieczeń globalnych.

## <a name="syntax"></a>Składnia

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>Uwagi

Plik cookie zabezpieczeń globalnych służy do ochrony przepełnienie buforu w kodzie skompilowanym z [/GS (Sprawdzanie zabezpieczeń bufora)](../../build/reference/gs-buffer-security-check.md) i w kodzie, używającej obsługi wyjątków. Przy wejściu do funkcji chronionych przekroczenie plik cookie jest umieszczany na stosie, a przy zamykaniu, wartość na stosie jest porównywany z globalnego pliku cookie. Wszelkie różnice między nimi wskazuje, że przepełnienie buforu wystąpił i powoduje natychmiastowe przerwanie działania programu.

Zwykle **__security_init_cookie** jest wywoływana przez CRT, po jego zainicjowaniu. Jeśli pominąć Inicjalizacja CRT — na przykład, jeśli używasz [/Entry](../../build/reference/entry-entry-point-symbol.md) do określonego punktu wejścia — należy wywołać **__security_init_cookie** samodzielnie. Jeśli **__security_init_cookie** nie jest wywoływana, jest globalna plik cookie zabezpieczeń jest ustawiony na wartość domyślną i zostanie naruszony ochrony przepełnienia buforu. Ponieważ osoba atakująca może wykorzystać tę wartość pliku cookie domyślną do pokonania sprawdzanie przepełnienia buforu, firma Microsoft zaleca, aby zawsze wywołania **__security_init_cookie** podczas definiowania punktem wejścia.

Wywołanie **__security_init_cookie** musi nastąpić przed każdą chronione przekroczenie wprowadzeniem funkcji; w przeciwnym razie zostanie wykryty przepełnienie buforu fałszywe. Aby uzyskać więcej informacji, zobacz [R6035 błąd środowiska uruchomieniowego C](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="example"></a>Przykład

Zobacz przykłady w [R6035 błąd środowiska uruchomieniowego C](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h >|

**__security_init_cookie** jest rozszerzeniem Microsoft standardowej biblioteki C w czasie wykonywania. Aby uzyskać informacje o zgodności – zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Microsoft Security Response Center](https://www.microsoft.com/msrc?rtc=1)
