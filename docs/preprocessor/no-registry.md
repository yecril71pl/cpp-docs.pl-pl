---
title: no_registry
ms.date: 10/18/2018
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: bd101f5ca1776518ff4c5092da99134110bbb0b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503028"
---
# <a name="noregistry"></a>no_registry

**no_registry** informuje kompilator, który nie należy przeszukiwać rejestru dla biblioteki typów, zaimportowane wraz z `#import`.

## <a name="syntax"></a>Składnia

```
#import filename no_registry
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Biblioteki typów.

## <a name="remarks"></a>Uwagi

Przywoływanej biblioteki typów nie zostanie znaleziony w katalogach include, kompilacja zakończy się niepowodzeniem, nawet jeśli biblioteki typów znajduje się w rejestrze.  **no_registry** propaguje do innych bibliotek typów niejawnie zaimportowane wraz z `auto_search`.

Kompilator wyszuka nigdy nie rejestru dla biblioteki typów, które są określone przez nazwę pliku i przekazywana bezpośrednio do `#import`.

Podczas `auto_search` jest określony, dodatkowy `#import`s zostanie wygenerowany za pomocą **no_registry** ustawienia wstępnego `#import` (jeśli początkowej `#import` dyrektywy **no_registry** , `auto_search`-generowane `#import` jest również **no_registry**.)

**no_registry** jest przydatne, jeśli chcesz zaimportować krzyżowe bibliotek typu odwołania, bez ryzyka stałego skanowania kompilatora znajdowanie starszej wersji pliku w rejestrze. **no_registry** jest również przydatne, jeśli biblioteka typów nie jest zarejestrowany.

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)