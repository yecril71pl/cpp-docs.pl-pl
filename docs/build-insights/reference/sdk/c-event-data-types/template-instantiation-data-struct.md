---
title: struktura TEMPLATE_INSTANTIATION_DATA
description: C++ Build Insights SDK TEMPLATE_INSTANTIATION_DATA odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a38d19368e7c0a9912907f1da6e7a2e31ffe8d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325333"
---
# <a name="template_instantiation_data-structure"></a>struktura TEMPLATE_INSTANTIATION_DATA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `TEMPLATE_INSTANTIATION_DATA` opisuje wystąpienie szablonu.

## <a name="syntax"></a>Składnia

```cpp
typedef struct TEMPLATE_INSTANTIATION_DATA_TAG
{
    unsigned long long  SpecializationSymbolKey;
    unsigned long long  PrimaryTemplateSymbolKey;
    int                 KindCode;

} TEMPLATE_INSTANTIATION_DATA;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `SpecializationSymbolKey` | Klucz dla typu specjalizacji szablonu. Ta wartość jest unikatowa w analizowanym śladzie. |
| `PrimaryTemplateSymbolKey` | Klucz dla typu szablonu podstawowego, który był wyspecjalizowany. Ta wartość jest unikatowa w analizowanym śladzie. |
| `KindCode` | Typ wystąpienia szablonu. Aby uzyskać więcej informacji, zobacz [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md). |

## <a name="remarks"></a>Uwagi

Klucze w `TEMPLATE_INSTANTIATION_DATA` strukturze są unikatowe w analizowanym śladzie. Jednak dwa różne klucze pochodzące z różnych kompilatora przepustek front-end może wskazywać na dwa identyczne typy. Podczas korzystania `TEMPLATE_INSTANTIATION_DATA` z informacji z wielu kompilatora frontonu przechodzi, użyj [SYMBOL_NAME](../event-table.md#symbol-name) zdarzeń, aby określić, czy dwa typy są takie same. `SymbolName`zdarzenia są emitowane na końcu przebiegu front-end kompilatora, po wszystkie wystąpienia szablonu miały miejsce.

::: moniker-end
