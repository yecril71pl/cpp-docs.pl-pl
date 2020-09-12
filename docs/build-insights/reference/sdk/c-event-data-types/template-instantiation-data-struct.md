---
title: Struktura TEMPLATE_INSTANTIATION_DATA
description: Informacje o strukturze TEMPLATE_INSTANTIATION_DATA zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 15bbb25c3abac339201179e763bffd916dba0480
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040876"
---
# <a name="template_instantiation_data-structure"></a>Struktura TEMPLATE_INSTANTIATION_DATA

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`TEMPLATE_INSTANTIATION_DATA`Struktura opisuje Tworzenie wystąpienia szablonu.

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

| Nazwa | Opis |
|--|--|
| `SpecializationSymbolKey` | Klucz typu specjalizacji szablonu. Ta wartość jest unikatowa w obrębie analizowanego śledzenia. |
| `PrimaryTemplateSymbolKey` | Klucz dla podstawowego typu szablonu, który był wyspecjalizowany. Ta wartość jest unikatowa w obrębie analizowanego śledzenia. |
| `KindCode` | Typ tworzenia wystąpienia szablonu. Aby uzyskać więcej informacji, zobacz [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md). |

## <a name="remarks"></a>Uwagi

Klucze w `TEMPLATE_INSTANTIATION_DATA` strukturze są unikatowe w obrębie analizowanego śledzenia. Jednak dwa różne klucze pochodzące z różnych passów frontonu kompilatora mogą wskazywać na dwa identyczne typy. W przypadku `TEMPLATE_INSTANTIATION_DATA` korzystania z informacji z wielu przebiegów frontonu kompilatora Użyj zdarzeń [SYMBOL_NAME](../event-table.md#symbol-name) , aby określić, czy dwa typy są takie same. `SymbolName` zdarzenia są emitowane na końcu przebiegu frontonu kompilatora, po wykonaniu wszystkich wystąpień szablonu.

::: moniker-end
