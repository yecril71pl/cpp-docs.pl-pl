---
title: _endthread, _endthreadex
ms.date: 11/04/2016
apiname:
- _endthread
- _endthreadex
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _endthread
- endthreadex
- _endthreadex
- endthread
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
ms.openlocfilehash: 48a2ce90b6bc90d40f6071898e1e5182502e938f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597486"
---
# <a name="endthread-endthreadex"></a>_endthread, _endthreadex

Kończy działanie wątku; **_endthread** kończy działanie wątku, który jest tworzony przez **_beginthread** i **_endthreadex** kończy działanie wątku, który jest tworzony przez **_beginthreadex**.

## <a name="syntax"></a>Składnia

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>Parametry

*retval*<br/>
Wątek kod zakończenia.

## <a name="remarks"></a>Uwagi

Możesz wywołać **_endthread** lub **_endthreadex** jawnie, aby zakończyć wątek; jednak **_endthread** lub **_endthreadex** nosi nazwę automatycznie kiedy wątek wraca z przekazany jako parametr do **_beginthread** lub **_beginthreadex**. Zakończenie wątku z wywołaniem **endthread —** lub **_endthreadex** pomaga zapewnić właściwe odzyskiwania zasobów przydzielonych wątku.

> [!NOTE]
> Dla pliku wykonywalnego połączonego z Libcmt.lib Nie wywołuj Win32 [ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread) interfejsu API, uniemożliwia to systemowi środowiska wykonawczego odzyskiwanie przydzielone zasoby. **_endthread** i **_endthreadex** odzyskiwania zasobów przydzielonych wątku, a następnie wywołać **ExitThread**.

**_endthread** automatycznie zamyka uchwyt do wątku. (To zachowanie różni się od Win32 **ExitThread** interfejsu API.) W związku z tym, kiedy używasz **_beginthread** i **_endthread**, nie zamykaj jawnie uchwytu wątku poprzez wywołanie Win32 [funkcja CloseHandle](https://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) interfejsu API.

Win32, takich jak **ExitThread** interfejsu API, **_endthreadex** nie zamyka dojście wątku. W związku z tym, kiedy używasz **_beginthreadex** i **_endthreadex**, należy zamknąć uchwytu wątku poprzez wywołanie Win32 **funkcja CloseHandle** interfejsu API.

> [!NOTE]
> **_endthread** i **_endthreadex** spowodować, że destruktory C++ do czasu w wątku nie ma zostać wywołana.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_endthread**|\<process.h >|
|**_endthreadex**|\<process.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wielowątkowe wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Zobacz przykład [_beginthread](beginthread-beginthreadex.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
