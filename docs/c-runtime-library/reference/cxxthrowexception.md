---
title: _CxxThrowException
ms.date: 11/04/2016
api_name:
- _CxxThrowException
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
- CxxThrowException
- _CxxThrowException
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
ms.openlocfilehash: a5b614d25502ddd5a58aedcf2ec843b2b1ab9d47
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942041"
---
# <a name="_cxxthrowexception"></a>_CxxThrowException

Kompiluje rekord wyjątku i wywołuje środowisko uruchomieniowe w celu rozpoczęcia przetwarzania wyjątku.

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
Informacje wymagane do przetworzenia wyjątku.

## <a name="remarks"></a>Uwagi

Ta metoda jest uwzględniona w pliku tylko kompilatora, którego kompilator używa do przetwarzania wyjątków. Nie wywołuj metody bezpośrednio z poziomu kodu.

## <a name="requirements"></a>Wymagania

**Zewnętrz** Throw. cpp

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
