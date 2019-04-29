---
title: _fmode
ms.date: 11/04/2016
f1_keywords:
- fmode
- _fmode
helpviewer_keywords:
- file translation [C++], default mode
- fmode function
- _fmode function
ms.assetid: ac6df9eb-e5cc-4c54-aff3-373c21983118
ms.openlocfilehash: a41d665eab50203fc3bb176f8bb1bbc30737e844
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343891"
---
# <a name="fmode"></a>_fmode

`_fmode` Zmiennej ustawia domyślny tryb translacji plików tekstowych lub binarnych tłumaczenia. Ta zmienna globalna jest przestarzała dla bardziej bezpieczne wersje funkcjonalności [_get_fmode —](../c-runtime-library/reference/get-fmode.md) i [_set_fmode —](../c-runtime-library/reference/set-fmode.md), którego należy użyć zamiast zmiennej globalnej. Jest zadeklarowana w następujący sposób w Stdlib.h.

## <a name="syntax"></a>Składnia

```
extern int _fmode;
```

## <a name="remarks"></a>Uwagi

Domyślne ustawienie `_fmode` jest `_O_TEXT` tłumaczenia w trybie tekstowym. `_O_BINARY` jest to ustawienie w trybie binarnym.

Można zmienić wartość `_fmode` na trzy sposoby:

- Połącz z biblioteką Binmode.obj. Spowoduje to zmianę ustawienia początkowej `_fmode` do `_O_BINARY`, powodując wszystkich plików z wyjątkiem `stdin`, `stdout`, i `stderr` były otwierane w trybie binarnym.

- Wywołanie `_get_fmode` lub `_set_fmode` do pobierania lub ustawiania `_fmode` zmiennej globalnej, odpowiednio.

- Zmień wartość właściwości `_fmode` ustawiając go bezpośrednio w programie.

## <a name="see-also"></a>Zobacz także

[Zmienne globalne](../c-runtime-library/global-variables.md)<br/>
[_get_fmode](../c-runtime-library/reference/get-fmode.md)<br/>
[_set_fmode](../c-runtime-library/reference/set-fmode.md)
