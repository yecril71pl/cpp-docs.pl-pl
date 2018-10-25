---
title: no_namespace | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_namespace
dev_langs:
- C++
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e84cfad5a11c0d691c56e6e7ddcca17ea87e3f02
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082926"
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