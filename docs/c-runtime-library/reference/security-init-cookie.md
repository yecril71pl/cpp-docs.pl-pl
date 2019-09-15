---
title: __security_init_cookie
ms.date: 11/04/2016
api_name:
- __security_init_cookie
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- security_init_cookie
- __security_init_cookie
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
ms.openlocfilehash: 9f7e9924f4a96803749418d777e5ee2020f9df78
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948719"
---
# <a name="__security_init_cookie"></a>__security_init_cookie

Inicjuje globalny plik cookie zabezpieczeń.

## <a name="syntax"></a>Składnia

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>Uwagi

Globalny plik cookie zabezpieczeń jest używany na potrzeby ochrony przepełnienia buforu w kodzie skompilowanym za pomocą [/GS (sprawdzanie zabezpieczeń bufora)](../../build/reference/gs-buffer-security-check.md) i w kodzie, który używa obsługi wyjątków. We wpisie do funkcji chronionej przez przepełnienie plik cookie jest umieszczany na stosie, a po zakończeniu wartość na stosie jest porównywana z globalnym plikiem cookie. Każda różnica między nimi wskazuje, że przepełnienie buforu nastąpiło i powoduje natychmiastowe zakończenie działania programu.

Zwykle **__security_init_cookie** jest wywoływany przez CRT, gdy zostanie zainicjowany. W przypadku obejścia inicjalizacji CRT — na przykład jeśli używasz [/entry](../../build/reference/entry-entry-point-symbol.md) do określenia punktu wejścia, należy wywołać **__security_init_cookie** samodzielnie. Jeśli **__security_init_cookie** nie jest wywoływana, plik cookie zabezpieczeń globalnych ma ustawioną wartość domyślną, a ochrona przed przepełnieniem buforu zostaje naruszona. Ponieważ osoba atakująca może wykorzystać tę domyślną wartość pliku cookie w celu wypróbowania kontroli przepełnienia buforu, zalecamy, aby zawsze wywoływał **__security_init_cookie** podczas definiowania własnego punktu wejścia.

Wywołanie **__security_init_cookie** musi zostać wykonane przed wprowadzeniem jakiejkolwiek funkcji chronionej przez przepełnienie; w przeciwnym razie zostanie wykryte przepełnienie buforu fałszywe. Aby uzyskać więcej informacji, zobacz [błąd środowiska uruchomieniowego C R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="example"></a>Przykład

Zobacz przykłady [błędów środowiska uruchomieniowego języka C R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h>|

**__security_init_cookie** to rozszerzenie firmy Microsoft do standardowej biblioteki środowiska uruchomieniowego C. Aby uzyskać informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Microsoft Security Response Center](https://www.microsoft.com/msrc?rtc=1)
