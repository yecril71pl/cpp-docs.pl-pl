---
title: no_registry — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: 7c81cc2f570cb9ac4e977dac6d55cb69e491d3b2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220726"
---
# <a name="no_registry-import-attribute"></a>no_registry — atrybut importowania

**no_registry** instruuje kompilator, aby nie przeszukiwać rejestru dla bibliotek typów importowanych z `#import`.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **no_registry**

### <a name="parameters"></a>Parametry

*Biblioteka typów*\
Biblioteka typów.

## <a name="remarks"></a>Uwagi

Jeśli przywoływana biblioteka typów nie została znaleziona w katalogach dołączanych, kompilacja kończy się niepowodzeniem, nawet jeśli biblioteka typów znajduje się w rejestrze.  **no_registry** propaguje do innych bibliotek typów niejawnie zaimportowanych przy użyciu `auto_search`.

Kompilator nigdy nie przeszukuje rejestru dla bibliotek typów, które są określone przez nazwę pliku i są przesyłane `#import`bezpośrednio do.

Gdy `auto_search` jest określony, dodatkowe `#import` dyrektywy są generowane przy użyciu ustawienia **no_registry** początkowego `#import`. Jeśli wstępna `#import` `auto_search`dyrektywa została **no_registry**, wygenerowana `#import` jest również **no_registry**.

**no_registry** jest przydatne, jeśli chcesz zaimportować biblioteki typów, do których istnieją odwołania. Uniemożliwia ona kompilatorowi znalezienie starszej wersji pliku w rejestrze. **no_registry** jest również przydatna, jeśli biblioteka typów nie jest zarejestrowana.

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
