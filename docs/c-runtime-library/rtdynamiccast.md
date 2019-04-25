---
title: __RTDynamicCast
ms.date: 11/04/2016
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
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
ms.openlocfilehash: f4bf4895af99b2d5c2d61e739c9d49d59cecb020
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184531"
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
**wartość true,** Jeśli dane wejściowe to odwołanie; **false** Jeśli danych wejściowych jest wskaźnikiem.

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