---
title: Struktura SYMBOL_NAME_DATA
description: C++ Build Insights SDK SYMBOL_NAME_DATA odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1217572f20a772fde629533d6ab170c14dc5b5e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325337"
---
# <a name="symbol_name_data-structure"></a>Struktura SYMBOL_NAME_DATA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `SYMBOL_NAME_DATA` opisuje symbol front-end kompilatora.

## <a name="syntax"></a>Składnia

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `Key` | Klucz symbolu. Ta wartość jest unikatowa w analizowanym śladzie. |
| `Name` | Nazwa symbolu. |

## <a name="remarks"></a>Uwagi

Symbole pochodzące z dwóch różnych kompilatorów przechodzi front-end może mieć taką samą nazwę, ale inny klucz. W takim przypadku należy użyć nazw symboli, aby określić, czy dwa typy są takie same.

::: moniker-end
