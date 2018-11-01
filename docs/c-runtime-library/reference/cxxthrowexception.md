---
title: _CxxThrowException
ms.date: 11/04/2016
apiname:
- _CxxThrowException
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
- CxxThrowException
- _CxxThrowException
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
ms.openlocfilehash: 925b72a120b31029b76fa38bee73eea003511cd2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550336"
---
# <a name="cxxthrowexception"></a>_CxxThrowException

Tworzy rekord wyjątku i wywołuje środowisko uruchomieniowe do rozpoczęcia przetwarzania wyjątku.

## <a name="syntax"></a>Składnia

```C
extern "C" void __stdcall _CxxThrowException(
   void* pExceptionObject
   _ThrowInfo* pThrowInfo
);
```

### <a name="parameters"></a>Parametry

*pExceptionObject*<br/>
Obiekt, który wygenerował wyjątek.

*pThrowInfo*<br/>
Informacje wymagane do przetwarzania wyjątku.

## <a name="remarks"></a>Uwagi

Ta metoda znajduje się w pliku tylko do kompilatora, której kompilator używa do przetwarzania wyjątków. Nie wywołuj metody bezpośrednio w kodzie.

## <a name="requirements"></a>Wymagania

**Źródło:** Throw.cpp

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
