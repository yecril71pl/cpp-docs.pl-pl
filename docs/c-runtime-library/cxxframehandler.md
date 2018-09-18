---
title: __CxxFrameHandler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __CxxFrameHandler
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __CxxFrameHandler
dev_langs:
- C++
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a4141d932cfad78ca9c563334ebbe51f711153e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088725"
---
# <a name="cxxframehandler"></a>__CxxFrameHandler

Wewnętrzny funkcji CRT. Używane przez CRT, do obsługi wyjątków strukturalnych ramek.

## <a name="syntax"></a>Składnia

```cpp
EXCEPTION_DISPOSITION __CxxFrameHandler(
      EHExceptionRecord  *pExcept,
      EHRegistrationNode *pRN,
      void               *pContext,
      DispatcherContext  *pDC
   )
```

#### <a name="parameters"></a>Parametry

*pExcept*<br/>
Rekordu wyjątku, który jest przekazywany do możliwe `catch` instrukcji.

*PRN*<br/>
Dynamiczne informacje na temat ramką stosu, która jest używana do obsługi wyjątków. Aby uzyskać więcej informacji zobacz ehdata.h.

*pContext*<br/>
Kontekst. (Nie używane na procesorach Intel).

*podstawowego kontrolera domeny*<br/>
Dodatkowe informacje na temat funkcji wejścia i stosu ramki.

## <a name="return-value"></a>Wartość zwracana

Jedną z *wyrażenie filtru* wartości używane przez [spróbuj-except, instrukcja](../cpp/try-except-statement.md).

## <a name="remarks"></a>Uwagi

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__CxxFrameHandler|excpt.h, ehdata.h|