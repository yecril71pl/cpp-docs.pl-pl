---
title: __max — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __max
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
- max
- __max
dev_langs:
- C++
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d223f4288ccf40646e8f560cec7243b7e8f9f649
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="max"></a>__max

Makro preprocesora zwraca większy z dwóch wartości.

## <a name="syntax"></a>Składnia

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>Parametry

*a*, *b*<br/>
Wartości typu liczbowego do porównania.

## <a name="return-value"></a>Wartość zwracana

**__max —** zwraca większy z jego argumentów.

## <a name="remarks"></a>Uwagi

**__Max —** makro porównuje dwie wartości i zwraca wartość typu, który większy. Argumenty mogą być dowolnego liczbowego typu danych, podpisu lub bez znaku. Zarówno argumentów i zwracana wartość musi być tego samego typu danych.

Argument zwrócił jest oceniane dwukrotnie przez makra. Może to prowadzić do nieoczekiwanych wyników, jeśli wartością argumentu jest wyrażenie, które zmienia jego wartość, gdy wartość jest szacowana, takich jak `*p++`.

## <a name="requirements"></a>Wymagania

|Macro|Wymagany nagłówek|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz przykład [__min —](min.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>