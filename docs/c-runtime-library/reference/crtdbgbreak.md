---
title: _CrtDbgBreak
ms.date: 11/04/2016
apiname:
- _CrtDbgBreak
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
- _CrtDbgBreak
- CrtDbgBreak
helpviewer_keywords:
- CrtDbgBreak function
- _CrtDbgBreak function
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
ms.openlocfilehash: 4cf64daaea3193f7cf6b3aaa0b1aab031f104704
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478305"
---
# <a name="crtdbgbreak"></a>_CrtDbgBreak

Ustawia punkt przerwania w określonej linii kodu. (Używane tylko w trybie debugowania).

## <a name="syntax"></a>Składnia

```C
void _CrtDbgBreak( void );
```

## <a name="return-value"></a>Wartość zwracana

Nie ma żadnej zwracanej wartości.

## <a name="remarks"></a>Uwagi

**_Crtdbgbreak —** funkcja ustawia punkt przerwania debugowania na określony wiersz kodu, gdzie znajduje się funkcja. Ta funkcja jest używana tylko w trybie debugowania i jest zależna od **_DEBUG** definiowanego wcześniej.

Aby uzyskać więcej informacji na temat korzystania innych funkcją podłączania funkcji wykonawczej i pisanie własnych zdefiniowaną przez klienta funkcje punktów zaczepienia, zobacz [pisania swój własny debugowanie funkcji punktów zaczepienia](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtDbgBreak**|\<CRTDBG.h>|

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[__debugbreak](../../intrinsics/debugbreak.md)<br/>
