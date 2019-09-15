---
title: __RTDynamicCast
ms.date: 11/04/2016
api_name:
- __RTDynamicCast
api_location:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __RTDynamicCast
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
ms.openlocfilehash: c4b0caadf20d6c5494acf47ee5a788b5ee009c47
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957340"
---
# <a name="__rtdynamiccast"></a>__RTDynamicCast

Implementacja operatora [dynamic_cast](../cpp/dynamic-cast-operator.md) w czasie wykonywania.

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
Wskaźnik do obiektu polimorficznego.

*VfDelta*<br/>
Przesunięcie wskaźnika funkcji wirtualnej w obiekcie.

*SrcType*<br/>
Typ statyczny obiektu wskazywanego przez `inptr` parametr.

*Typ*<br/>
Zamierzony wynik rzutowania.

*isReference*<br/>
**prawda** , jeśli dane wejściowe są odwołaniami; **Fałsz** , jeśli dane wejściowe są wskaźnikiem.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do odpowiedniego obiektu podrzędnego, jeśli powodzenie; w przeciwnym razie **wartość null**.

## <a name="exceptions"></a>Wyjątki

`bad_cast()`Jeśli dane wejściowe `dynamic_cast<>` to odwołanie, a rzutowanie nie powiedzie się.

## <a name="remarks"></a>Uwagi

Konwertuje `inptr` do obiektu typu `TargetType`. Typ elementu `inptr` musi być wskaźnikiem, jeśli `TargetType` jest wskaźnikiem lub l-wartością, jeśli `TargetType` jest odwołaniem. `TargetType`musi być wskaźnikiem lub odwołaniem do wcześniej zdefiniowanego typu klasy lub wskaźnikiem do wartości void.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__RTDynamicCast|RTTI. h|