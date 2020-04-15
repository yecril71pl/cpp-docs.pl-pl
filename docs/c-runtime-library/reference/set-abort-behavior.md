---
title: _set_abort_behavior
ms.date: 4/2/2020
api_name:
- _set_abort_behavior
- _o__set_abort_behavior
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_abort_behavior
- set_abort_behavior
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.openlocfilehash: fd3a3c2f99d1702cdccf68328c2122b965b2d078
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337867"
---
# <a name="_set_abort_behavior"></a>_set_abort_behavior

Określa akcję, która ma zostać podjęta po nieprawidłowym zakończeniu programu.

> [!NOTE]
> Nie należy używać funkcji [przerwania,](abort.md) aby zamknąć aplikację Microsoft Store, z wyjątkiem scenariuszy testowania lub debugowania. Sposób zamykania aplikacji ze Sklepu jest zabroniony zgodnie z [zasadami sklepu Microsoft Store.](/legal/windows/agreements/store-policies) Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej](/windows/uwp/launch-resume/app-lifecycle)systemu .

## <a name="syntax"></a>Składnia

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Parametry

*flagi*<br/>
Nowa wartość flag [przerwania.](abort.md)

*maska*<br/>
Maska dla [bitów flag abort](abort.md) do ustawionego.

## <a name="return-value"></a>Wartość zwracana

Stara wartość flag.

## <a name="remarks"></a>Uwagi

Istnieją dwie flagi [przerwania:](abort.md) **_WRITE_ABORT_MSG** i **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** określa, czy pomocna wiadomość tekstowa jest drukowana, gdy program jest nieprawidłowo zakończony. Komunikat stwierdza, że aplikacja wywoływała funkcję [przerwania.](abort.md) Domyślnym zachowaniem jest wydrukowanie wiadomości. **_CALL_REPORTFAULT**, jeśli ustawiona, określa, że zrzut awaryjny programu Watson jest generowany i raportowy, gdy [wywołana](abort.md) jest przerwania. Domyślnie raportowanie zrzutu awaryjnego jest włączone w kompilacjach innych niż DEBUG.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_abort_behavior**|\<>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Przerwać](abort.md)<br/>
