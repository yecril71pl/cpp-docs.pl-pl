---
title: __security_init_cookie — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e6bfafa1322d9730923867c86f754153f641460
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="securityinitcookie"></a>__security_init_cookie

Inicjuje plik cookie zabezpieczeń globalnych.

## <a name="syntax"></a>Składnia

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>Uwagi

Plik cookie zabezpieczeń globalnych służy do ochrony przepełnienie buforu w kodzie skompilowanym z [/GS (Sprawdzanie zabezpieczeń bufora)](../../build/reference/gs-buffer-security-check.md) w kodu korzystającego z obsługi wyjątków. Przy wejściu do funkcji chronionych przekroczenie plik cookie jest umieszczany na stosie, a po zakończeniu wartości na stosie jest porównywana z globalnego pliku cookie. Różnicę między nimi wskazuje, czy nastąpiło przepełnienie buforu oraz powoduje natychmiastowe przerwanie działania programu.

Zwykle **__security_init_cookie —** jest wywoływana przez CRT podczas jego inicjowania. Jeśli obejścia Inicjalizacja CRT — na przykład, jeśli używasz [/Entry](../../build/reference/entry-entry-point-symbol.md) do określenia punktu wejścia — należy wywołać **__security_init_cookie —** samodzielnie. Jeśli **__security_init_cookie —** nie jest wywoływany, jest globalnym plik cookie zabezpieczeń ma ustawioną wartość domyślną i zostanie naruszony ochrony przepełnienie buforu. Osoba atakująca może wykorzystać tę wartość pliku cookie domyślną pokonanie kontroli przepełnienie buforu, dlatego zaleca się zawsze telefoniczne skontaktowanie się z **__security_init_cookie —** podczas definiowania punktu wejścia.

Wywołanie **__security_init_cookie —** musi być dokonana przed dowolnego chronionego przekroczenie funkcja została wprowadzona; w przeciwnym razie zostanie wykryty przepełnienie buforu fałszywe. Aby uzyskać więcej informacji, zobacz [po R6035 błąd środowiska uruchomieniowego C](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="example"></a>Przykład

Przykłady w [po R6035 błąd środowiska uruchomieniowego C](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h >|

**__security_init_cookie —** to rozszerzenie Microsoft standardowa biblioteka języka C w czasie wykonywania. Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Kontrole zabezpieczeń kompilatora szczegółowo](http://go.microsoft.com/fwlink/p/?linkid=7260)<br/>
