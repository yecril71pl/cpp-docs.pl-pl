---
title: srand — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- srand
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- srand
dev_langs:
- C++
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7972ddfe6ae9c1d591bdbd4cc5e208d78e826037
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107557"
---
# <a name="srand"></a>srand

Ustawia wartość początkową inicjatora generator liczb pseudolosowych, używane przez **rand** funkcji.

## <a name="syntax"></a>Składnia

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Parametry

*Inicjator*<br/>
Początkowy dla Generowanie liczb pseudolosowych

## <a name="remarks"></a>Uwagi

**Srand —** funkcja ustawia punkt początkowy dla generowania szereg pseudolosowych liczb całkowitych w bieżącym wątku. Aby ponownie zainicjować generatora Aby utworzyć taką samą sekwencję wyniki, należy wywołać **srand —** działać, a następnie używać tego samego *inicjatora* argument ponownie. Dowolna inna wartość, aby uzyskać *inicjatora* ustawia generator do innego punktu wyjścia w sekwencji pseudolosowych. **RAND** pobiera liczb pseudolosowych, które są generowane. Wywoływanie **rand** przed wywołaniem dowolnej **srand —** generuje tę samą sekwencję co wywołanie metody **srand —** z *inicjatora* przekazywane jako 1.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [rand](rand.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
