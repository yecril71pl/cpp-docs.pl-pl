---
title: setjmp | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- setjmp
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
- setjmp
dev_langs:
- C++
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc01f80aa4521ff3588cca14ceabbf5447338cca
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="setjmp"></a>setjmp

Zapisuje bieżący stan programu.

## <a name="syntax"></a>Składnia

```C
int setjmp(
   jmp_buf env
);
```

### <a name="parameters"></a>Parametry

*ENV*<br/>
Zmienna, w której jest przechowywany środowiska.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0 po zapisaniu środowiska stosu. Jeśli **setjmp** zwraca na **longjmp** wywołać, zwraca **wartość** argument **longjmp**, lub jeśli **wartość**  argument **longjmp** ma wartość 0, **setjmp** zwraca wartość 1. Nie ma żadnych zwracany błąd.

## <a name="remarks"></a>Uwagi

**Setjmp** funkcja zapisuje środowisku stosu, którego będzie można później przywrócić, za pomocą **longjmp**. Podczas łączenia **setjmp** i **longjmp** umożliwiają wykonanie innego niż lokalne **goto**. One są zwykle używane do przekazania Kontrola wykonywania kodu służącego do obsługi błędów lub odzyskiwania w wcześniej wywołana procedura bez użycia normalne wywołanie lub return Konwencji.

Wywołanie **setjmp** jest zapisywany w bieżącym środowisku stosu w *env*. Kolejne wywołania **longjmp** przywraca zapisanego środowiska i zwraca sterowania do punktu zaraz po odpowiadającego **setjmp** wywołania. Wszystkie zmienne (z wyjątkiem zmiennych rejestru) dostępny do procedury odbieranie kontroli zawierają wartości podczas obliczania miało **longjmp** została wywołana.

Nie jest możliwe użycie **setjmp** na przejście z kodu natywnego do zarządzanego kodu.

**Uwaga** **setjmp** i **longjmp** nie obsługują semantyki obiektu języka C++. W programach języka C++ użyj mechanizmu obsługi wyjątków C++.

Aby uzyskać więcej informacji, zobacz [przy użyciu setjmp i longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_fpreset —](fpreset.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)<br/>
[_setjmp3](../../c-runtime-library/setjmp3.md)<br/>
