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
ms.openlocfilehash: a5384966ff96c4e4831ba06f7c67467156a9ecd2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170075"
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
Typ statyczny obiektu wskazywany przez parametr `inptr`.

*Typ*<br/>
Zamierzony wynik rzutowania.

*isReference*<br/>
**prawda** , jeśli dane wejściowe są odwołaniami; **Fałsz** , jeśli dane wejściowe są wskaźnikiem.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do odpowiedniego obiektu podrzędnego, jeśli powodzenie; w przeciwnym razie **wartość null**.

## <a name="exceptions"></a>Wyjątki

`bad_cast()`, jeśli dane wejściowe do `dynamic_cast<>` są odwołania, a rzutowanie nie powiedzie się.

## <a name="remarks"></a>Uwagi

Konwertuje `inptr` do obiektu typu `TargetType`. Typ `inptr` musi być wskaźnikiem, jeśli `TargetType` jest wskaźnikiem lub l-wartością, jeśli `TargetType` jest odwołaniem. `TargetType` musi być wskaźnikiem lub odwołaniem do wcześniej zdefiniowanego typu klasy lub wskaźnikiem do wartości void.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__RTDynamicCast|RTTI. h|
