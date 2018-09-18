---
title: _fmode | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- fmode
- _fmode
dev_langs:
- C++
helpviewer_keywords:
- file translation [C++], default mode
- fmode function
- _fmode function
ms.assetid: ac6df9eb-e5cc-4c54-aff3-373c21983118
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfc89eeda690632979521fa8a4e91c48c8b3c866
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080834"
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