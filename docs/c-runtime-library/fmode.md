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
ms.openlocfilehash: c462b8f848a34993e01232039d608b627c05961f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430540"
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

## <a name="see-also"></a>Zobacz też

[Zmienne globalne](../c-runtime-library/global-variables.md)<br/>
[_get_fmode](../c-runtime-library/reference/get-fmode.md)<br/>
[_set_fmode](../c-runtime-library/reference/set-fmode.md)