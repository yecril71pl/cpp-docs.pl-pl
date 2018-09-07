---
title: _CrtMemDumpAllObjectsSince | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92d6148f6cbe49799a122d1745a6a6cde4c8be30
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100382"
---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

Zrzuca informacje o obiektach w stosie, od czasu rozpoczęcia wykonywania programu, lub ze stanu sterty określony (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
void _CrtMemDumpAllObjectsSince(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*state*<br/>
Wskaźnik do stanu sterty, aby rozpocząć zrzucanie z lub **NULL**.

## <a name="remarks"></a>Uwagi

**_CrtMemDumpAllObjectsSince** funkcja zrzuty informacji nagłówka debugowania obiekty przydzielone w stosie, w postaci czytelny dla użytkownika. Informacje o zrzucie może służyć przez aplikację do śledzenia alokacji i wykrycia problemów z pamięcią. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtMemDumpAllObjectsSince** są usuwane podczas przetwarzania wstępnego.

**_CrtMemDumpAllObjectsSince** używa wartości *stanu* parametru, aby ustalić, gdzie można zainicjować operacji zrzutu informacji. Umożliwiającą zrzucanie ze stanu sterty określonego *stanu* parametru musi być wskaźnikiem do **_CrtMemState** strukturę, która ma zostać wypełnione podczas [_crtmemcheckpoint —](crtmemcheckpoint.md) przed **_CrtMemDumpAllObjectsSince** została wywołana. Gdy *stanu* jest **NULL**, funkcja rozpoczyna się zrzut od czasu rozpoczęcia wykonywania programu.

Jeśli aplikacja została zainstalowana funkcja podłączania zrzutu, wywołując [_CrtSetDumpClient](crtsetdumpclient.md), a następnie za każdym razem, gdy **_CrtMemDumpAllObjectsSince** Zrzuca informacje o **_CLIENT_BLOCK** typ bloku, wywoływanych przez nią z funkcji zrzutu dostarczone przez aplikację. Domyślnie wewnętrzne bloki wykonywania C (**_CRT_BLOCK**) nie są uwzględnione w operacji zrzutu pamięci. [_CrtSetDbgFlag](crtsetdbgflag.md) funkcja może służyć do włączyć **_CRTDBG_CHECK_CRT_DF** trochę **_crtDbgFlag** aby objąć te bloki. Ponadto bloki oznaczone jako zwolniony, lub zignorować (**_FREE_BLOCK**, **_IGNORE_BLOCK**) nie są uwzględnione w zrzut pamięci.

Aby uzyskać więcej informacji o funkcjach stanu sterty i **_CrtMemState** struktury, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji na temat sposobu bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Przykład sposobu użycia **_CrtMemDumpAllObjectsSince**, zobacz [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
