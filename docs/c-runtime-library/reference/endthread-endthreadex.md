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
ms.openlocfilehash: 5afbc907356d4c5b14b749de5de0c8d36280891e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499962"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

Kończy wątek; **_endthread** kończy wątek, który jest tworzony przez **_beginthread** i **_endthreadex** kończy wątek tworzony przez **_beginthreadex**.

## <a name="syntax"></a>Składnia

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>Parametry

*retval*<br/>
Kod zakończenia wątku.

## <a name="remarks"></a>Uwagi

Aby przerwać wątek, można jawnie wywołać **_endthread** lub **_endthreadex** . jednak **_endthread** lub **_endthreadex** jest wywoływana automatycznie, gdy wątek zwraca z procedury przekazywanej jako parametr do **_beginthread** lub **_beginthreadex**. Zakończenie wątku z wywołaniem metody **endthread** lub **_endthreadex** pomaga zapewnić odpowiednie odzyskiwanie zasobów przyznanych dla wątku.

> [!NOTE]
> Dla pliku wykonywalnego połączonego z libcmt. lib nie wywołuj interfejsu API Win32 [ExitThread —](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) ; Zapobiega to odzyskiwaniu przyznanych zasobów przez system czasu wykonywania. **_endthread** i **_endthreadex** Odbierz przydzieloną zasoby wątków, a następnie Wywołaj **ExitThread —** .

**_endthread** automatycznie zamyka dojście wątku. (To zachowanie różni się od interfejsu API Win32 **ExitThread —** ). W związku z tym, jeśli używasz **_beginthread** i **_endthread**, nie zamykaj jawnie uchwytu wątku, wywołując interfejs API [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) Win32.

Podobnie jak w przypadku interfejsu API Win32 **ExitThread —** , **_endthreadex** nie zamyka dojścia wątku. W związku z tym, jeśli używasz **_beginthreadex** i **_endthreadex**, musisz zamknąć uchwyt wątku, wywołując interfejs API **CloseHandle** środowiska Win32.

> [!NOTE]
> **_endthread** i **_endthreadex** powodują C++ , że destruktory oczekujące w wątku nie mają być wywoływane.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wielowątkowe wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Przykład

Zobacz przykład dla [_beginthread](beginthread-beginthreadex.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
