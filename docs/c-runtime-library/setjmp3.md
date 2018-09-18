---
title: _setjmp3 — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22416f4036d79f9e9b7c95f1cf9098e450533f39
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054275"
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

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[setjmp](../c-runtime-library/reference/setjmp.md)