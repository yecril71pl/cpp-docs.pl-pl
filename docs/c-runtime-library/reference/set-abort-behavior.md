---
title: _set_abort_behavior
ms.date: 1/02/2018
apiname:
- _set_abort_behavior
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
- _set_abort_behavior
- set_abort_behavior
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.openlocfilehash: 8b36a771a3694c6d01573d619990743c7ddc0f3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356696"
---
# <a name="setabortbehavior"></a>_set_abort_behavior

Określa akcję do wykonania, kiedy program zostanie nagle przerwany.

> [!NOTE]
> Nie używaj [przerwać](abort.md) funkcję, aby zamknąć aplikację Microsoft Store, z wyjątkiem testowania i debugowania scenariuszy. Sposoby Programmatic lub interfejs użytkownika, zamknąć Store app nie są dozwolone zgodnie z opisem w [zasady Microsoft Store](/legal/windows/agreements/store-policies). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Składnia

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Parametry

*flagi*<br/>
Nowa wartość [przerwać](abort.md) flag.

*Maska*<br/>
Maska dla [przerwać](abort.md) flaguje bity do ustawienia.

## <a name="return-value"></a>Wartość zwracana

Stara wartość flag.

## <a name="remarks"></a>Uwagi

Istnieją dwa [przerwać](abort.md) flagi: **_WRITE_ABORT_MSG** i **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** Określa, czy pomocny tekst komunikatu jest drukowany, gdy program zostanie nagle przerwany. Komunikat stwierdza, że aplikacja wywołała [przerwać](abort.md) funkcji. Zachowaniem domyślnym jest drukowanie wiadomości. **_CALL_REPORTFAULT**, jeśli ustawiona, określa, że zrzut awaryjny Watson jest generowany i zgłaszany podczas [przerwać](abort.md) jest wywoływana. Domyślnie zgłoszenie zrzutu awaryjnego jest włączona w kompilacjach nieprzeznaczonych do debugowania.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_set_abort_behavior.c
// compile with: /TC
#include <stdlib.h>

int main()
{
   printf("Suppressing the abort message. If successful, this message"
          " will be the only output.\n");
   // Suppress the abort message
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);
   abort();
}
```

```Output
Suppressing the abort message. If successful, this message will be the only output.
```

## <a name="see-also"></a>Zobacz także

[abort](abort.md)<br/>
