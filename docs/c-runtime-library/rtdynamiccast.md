---
title: __RTDynamicCast | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __RTDynamicCast
apilocation:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- __RTDynamicCast
dev_langs:
- C++
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f94d60d4c6e804a9bd27293bb0eff67b29a1e8a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092066"
---
# <a name="rtdynamiccast"></a>__RTDynamicCast

Implementacja środowiska uruchomieniowego [dynamic_cast](../cpp/dynamic-cast-operator.md) operatora.

## <a name="syntax"></a>Składnia

```cpp
PVOID __RTDynamicCast (
   PVOID inptr,
   LONG VfDelta,
   PVOID SrcType,
   PVOID TargetType,
   BOOL isReference
   ) throw(...)
```

#### <a name="parameters"></a>Parametry

*inptr*<br/>
Wskaźnik do obiektu polimorficznych.

*VfDelta*<br/>
Przesunięcie wskaźnika funkcji wirtualnej w obiekcie.

*SrcType*<br/>
Typ statyczny obiekt wskazywany przez `inptr` parametru.

*TargetType*<br/>
Zamierzony wynik rzutowania.

*isReference*<br/>
`true` Jeśli dane wejściowe to odwołanie; `false` Jeśli danych wejściowych jest wskaźnikiem.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do odpowiedniego obiektu podrzędnego, jeśli to się powiedzie; w przeciwnym razie **NULL**.

## <a name="exceptions"></a>Wyjątki

`bad_cast()` Jeśli dane wejściowe `dynamic_cast<>` jest odwołaniem i rzutowania zakończy się niepowodzeniem.

## <a name="remarks"></a>Uwagi

Konwertuje `inptr` do obiektu typu `TargetType`. Typ `inptr` musi być wskaźnikiem, jeśli `TargetType` jest wskaźnikiem lub l wartością, jeśli `TargetType` to odwołanie. `TargetType` musi to być wskaźnik lub odwołanie do typu klasy uprzednio zdefiniowany lub wskaźnika do typu void.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__RTDynamicCast|rtti.h|