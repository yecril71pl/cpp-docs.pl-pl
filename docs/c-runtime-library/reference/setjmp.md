---
title: setjmp | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/14/2018
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bd7d57d0678744243356a0565e10cbe4065f8d3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032545"
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

*środowisko*<br/>
Zmienna, w którym znajduje się środowisko.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0 po zapisaniu środowiska stosu. Jeśli **setjmp** zwraca na `longjmp` wywołanie, zwraca *wartość* argument `longjmp`, lub jeśli *wartość* argument `longjmp` ma wartość 0, **setjmp** zwraca wartość 1. Nie będzie zwrotu błędu.

## <a name="remarks"></a>Uwagi

**Setjmp** funkcji zapisuje w środowisku stosu, który można później przywrócić, przy użyciu `longjmp`. Gdy jest używana razem **setjmp** i `longjmp` zapewniają sposób wykonania nielokalnych **goto**. One są zwykle używane do przekazywania formantów wykonywania do kodu obsługi błędów lub odzyskiwania w poprzednio wywołanej procedurze bez użycia normalne wywołania lub Konwencji zwracania.

Wywołanie **setjmp** zapisuje bieżące środowisko stosu w *env*. Kolejne wywołanie `longjmp` przywraca zapisane środowisko i zwraca kontrolę do punktu, zaraz po odpowiednich **setjmp** wywołania. Wszystkie zmienne (z wyjątkiem zmienne rejestru) dostępne dla procedury odbieranie kontroli zawierają wartości, kiedy miało `longjmp` została wywołana.

Nie jest możliwe użycie **setjmp** przejść z natywnego do zarządzanego kodu.

**Microsoft Specific**

W przypadku kodu C++ firmy Microsoft w Windows **longjmp** używa tej samej semantyki odwracania stosu jako kod obsługi wyjątków. Jest bezpieczne do użycia w tych samych miejsc wygenerowany wyjątki C++. Jednak to użycie nie jest przenośny i dołączono niektóre ważne zastrzeżenia. Aby uzyskać więcej informacji, zobacz [longjmp](longjmp.md).

**END specyficzny dla Microsoft**

> [!NOTE]
> W przypadku przenośnego kodu C++, nie można zakładać, `setjmp` i `longjmp` obsługują semantyki obiektów języka C++. W szczególności `setjmp` / `longjmp` wywołanie pary ma niezdefiniowane zachowanie, jeśli zastąpienie `setjmp` i `longjmp` przez **catch** i **throw** powodowałoby wywołanie pliku wykonywalnego wszelkie nietrywialnymi destruktory dla obiektów automatycznych. W programach języka C++ zalecane jest używanie mechanizmu obsługi wyjątków C++.

Aby uzyskać więcej informacji, zobacz [przy użyciu funkcji setjmp i longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_fpreset —](fpreset.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)
