---
title: _Cxxthrowexception — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7adf4c285646e6a3f4706a9a56995f4440cc1e8
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103818"
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
