---
title: no_namespace
ms.date: 11/04/2016
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: b17bf5fb5f44d5453de29febe001f9e8737102b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540442"
---
# <a name="nonamespace"></a>no_namespace
**Określonego język C++**

Określa, że nazwa przestrzeni nazw nie są generowane przez kompilator.

## <a name="syntax"></a>Składnia

```
no_namespace
```

## <a name="remarks"></a>Uwagi

Biblioteka typów zawartości w `#import` pliku nagłówkowego zwykle są zdefiniowane w przestrzeni nazw. Nazwa przestrzeni nazw jest określona w `library` instrukcji, oryginalnym pliku IDL. Jeśli **no_namespace** atrybut jest określony, a następnie ta przestrzeń nazw nie jest generowany przez kompilator.

Jeśli chcesz użyć nazwy innej przestrzeni nazw, należy użyć [rename_namespace](../preprocessor/rename-namespace.md) zamiast tego atrybutu.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)