---
title: no_registry
ms.date: 10/18/2018
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: 2a0fd9a761f765aa9562ab18c095f683b80c7987
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411321"
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

## <a name="see-also"></a>Zobacz także

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import Directive](../preprocessor/hash-import-directive-cpp.md)