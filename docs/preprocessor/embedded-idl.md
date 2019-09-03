---
title: embedded_idl — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: 01948b171b20ad0a3bf3e7a41047f1fe3df185b0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216326"
---
# <a name="embedded_idl-import-attribute"></a>embedded_idl — atrybut importowania

**C++Specjalne**

Określa, czy biblioteka typów jest zapisywana `.tlh` w pliku z zachowaniem kodu generowanego przez atrybut.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **embedded_idl** [ **(** { **"emitidl"**  |  **"no_emitidl"** } **)** ]

### <a name="parameters"></a>Parametry

**emitidl**\
Informacje o typie zaimportowane z *biblioteki typów* są obecne w IDL wygenerowanym dla projektu o atrybutach. To zachowanie jest domyślne i obowiązuje, jeśli nie określisz parametru do `embedded_idl`.

**"no_emitidl"** \
Informacje o typie zaimportowane z *biblioteki typów* nie są obecne w IDL wygenerowanym dla projektu o atrybutach.

## <a name="example"></a>Przykład

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
