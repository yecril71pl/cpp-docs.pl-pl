---
title: embedded_idl
ms.date: 10/18/2018
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: c46924d2757d01a934c21a70f23e6556f6a10fd3
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034092"
---
# <a name="embeddedidl"></a>embedded_idl

**Określonego język C++**

Określa, czy biblioteki typów są zapisywane do pliku .tlh, z zachowanym kodem generowanych atrybutów.

## <a name="syntax"></a>Składnia

```
embedded_idl[("param")]
```

### <a name="parameters"></a>Parametry

*param*<br/>
Może być jedną z dwóch wartości:

- **emitidl**: Informacje o typie zaimportowany z biblioteki typów będą znajdować się we IDL wygenerowany w projekcie z atrybutami.  To jest ustawieniem domyślnym i będą obowiązywać w przypadku nieokreślenia parametru, aby `embedded_idl`.

- **no_emitidl**: Informacje o typie zaimportowany z biblioteki typów nie będą obecne w pliku IDL wygenerowany w projekcie z atrybutami.

## <a name="example"></a>Przykład

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

## <a name="remarks"></a>Uwagi

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)