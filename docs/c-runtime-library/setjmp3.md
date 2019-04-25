---
title: _setjmp3
ms.date: 11/04/2016
apiname:
- _setjmp3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- setjmp3
- _setjmp3
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
ms.openlocfilehash: e2c89acf1de88b831d70a0f438cdf14148a48632
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268801"
---
# <a name="setjmp3"></a>_setjmp3

Wewnętrzny funkcji CRT. Nową metodę implementacji `setjmp` funkcji.

## <a name="syntax"></a>Składnia

```
int _setjmp3(
   OUT jmp_buf env,
   int count,
   (optional parameters)
);
```

#### <a name="parameters"></a>Parametry

*środowisko*<br/>
[out] Adres buforu do przechowywania informacji o stanie.

*Liczba*<br/>
[in] Liczba dodatkowych `DWORD`s informacje, które są przechowywane w `optional parameters`.

*Następujące parametry opcjonalne*<br/>
[in] Dodatkowe dane przekazywany przez `setjmp` wewnętrzne. Pierwszy `DWORD` jest używany do operacji unwind dodatkowe dane, a następnie wróć do nieulotnej wskaźnika funkcji rejestrowania stanu. Drugi `DWORD` jest poziom spróbuj przywrócić. Wszelkie dalsze dane są zapisywane w tablicy danych typu ogólnego `jmp_buf`.

## <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość 0.

## <a name="remarks"></a>Uwagi

Nie należy używać tej funkcji w programie C++. Jest wewnętrzna funkcja, która nie obsługuje języka C++. Aby uzyskać więcej informacji o sposobie używania `setjmp`, zobacz [użycie funkcji setjmp/longjmp](../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Wymagania

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[setjmp](../c-runtime-library/reference/setjmp.md)
