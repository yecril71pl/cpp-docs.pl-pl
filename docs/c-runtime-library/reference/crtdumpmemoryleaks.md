---
title: _CrtDumpMemoryLeaks
ms.date: 11/04/2016
apiname:
- _CrtDumpMemoryLeaks
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
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
ms.openlocfilehash: baf4f8d8234ba744acda20541d37bbc3ed076678
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339458"
---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

Zrzuty całą pamięć zablokuje w stosie debugowania wystąpił wyciek pamięci (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>Wartość zwracana

**_CrtDumpMemoryLeaks** zwraca wartość PRAWDA, jeśli zostanie znaleziony przeciek pamięci. W przeciwnym razie funkcja zwraca wartość FALSE.

## <a name="remarks"></a>Uwagi

**_CrtDumpMemoryLeaks** funkcja określa, czy wystąpił przeciek pamięci, od momentu rozpoczęcia wykonywania programu. W przypadku odnalezienia przecieku informacji nagłówka debugowania dla wszystkich obiektów w stercie jest zrzucany w postaci czytelny dla użytkownika. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtDumpMemoryLeaks** są usuwane podczas przetwarzania wstępnego.

**_CrtDumpMemoryLeaks** często jest wywoływana po zakończeniu wykonywania programu, aby sprawdzić, czy całej pamięci przydzielonej przez aplikację, która została zwolniona. Funkcja może zostać wywołana automatycznie po zakończeniu program, włączając **_CRTDBG_LEAK_CHECK_DF** pola bitowego [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) Flaga przy użyciu [_CrtSetDbgFlag](crtsetdbgflag.md)funkcji.

**_CrtDumpMemoryLeaks** wywołania [_crtmemcheckpoint —](crtmemcheckpoint.md) uzyskać bieżący stan sterty, a następnie skanuje stanu dla bloków, które nie mają zostać zwolniony. Po napotkaniu blokiem niezwolnionych **_CrtDumpMemoryLeaks** wywołania [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) zrzutu informacji dla wszystkich obiektów, które są przydzielone w stosie, od czasu rozpoczęcia wykonywania programu.

Domyślnie wewnętrzne bloki wykonywania C (**_CRT_BLOCK**) nie są uwzględnione w operacji zrzutu pamięci. [_CrtSetDbgFlag](crtsetdbgflag.md) funkcja może służyć do włączyć **_CRTDBG_CHECK_CRT_DF** trochę **_crtDbgFlag** aby objąć te bloki w procesie wykrywania przecieków.

Aby uzyskać więcej informacji o funkcjach stanu sterty i **_CrtMemState** struktury, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji na temat sposobu bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Przykład sposobu użycia **_CrtDumpMemoryLeaks**, zobacz [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
