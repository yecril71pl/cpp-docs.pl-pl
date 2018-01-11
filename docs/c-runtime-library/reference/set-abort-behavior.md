---
title: "_set_abort_behavior — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_abort_behavior
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
dev_langs: C++
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 965ff160fd8098c60f53f639cb95aedf890edd86
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="setabortbehavior"></a>_set_abort_behavior

Określa akcję do wykonania, kiedy program jest nieprawidłowo zakończone.

> [!NOTE]
> Nie używaj `abort` funkcji, aby zamknąć aplikację Microsoft Store, z wyjątkiem w testowania i debugowania scenariuszy. Programowe lub interfejsu użytkownika sposobów Zamknij aplikację sklepu nie są dozwolone zgodnie z [zasady Microsoft Store](http://go.microsoft.com/fwlink/?LinkId=865936). Aby uzyskać więcej informacji, zobacz [cykl życia aplikacji platformy uniwersalnej systemu Windows](http://go.microsoft.com/fwlink/p/?LinkId=865934).

## <a name="syntax"></a>Składnia

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Parametry

[in] _flagi_  
Nowa wartość `abort` flagi.

[in] _maska_  
Maski dla `abort` usługi bits można ustawić flagi.

## <a name="return-value"></a>Wartość zwracana

Stara wartość flagi.

## <a name="remarks"></a>Uwagi

Istnieją dwa `abort` flagi: `_WRITE_ABORT_MSG` i `_CALL_REPORTFAULT`. `_WRITE_ABORT_MSG`Określa, czy wiadomość SMS pomocne jest drukowane, gdy program jest nieprawidłowo zakończone. Komunikat, że aplikacja została wywołana `abort` funkcji. Domyślnym zachowaniem jest wydrukowanie wiadomości. `_CALL_REPORTFAULT`, jeśli ustawiona, określa, że zrzutu awaryjnego Watson jest generowana i zgłaszane, gdy `abort` jest wywoływana. Domyślnie zgłoszenie zrzutu awaryjnego jest włączone w kompilacjach bez debugowania.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_set_abort_behavior`|\<stdlib.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[abort](../../c-runtime-library/reference/abort.md)  
