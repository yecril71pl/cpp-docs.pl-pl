---
title: Struktura TEMPLATE_INSTANTIATION_DATA
description: Zestaw C++ SDK usługi Build insights TEMPLATE_INSTANTIATION_DATA odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa669d715dbe56ce7e889330f46f307f520710f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333623"
---
# <a name="template_instantiation_data-structure"></a>Struktura TEMPLATE_INSTANTIATION_DATA

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `TEMPLATE_INSTANTIATION_DATA` opisuje Tworzenie wystąpienia szablonu.

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
| `SpecializationSymbolKey` | Klucz typu specjalizacji szablonu. Ta wartość jest unikatowa w obrębie analizowanego śledzenia. |
| `PrimaryTemplateSymbolKey` | Klucz dla podstawowego typu szablonu, który był wyspecjalizowany. Ta wartość jest unikatowa w obrębie analizowanego śledzenia. |
| `KindCode` | Typ tworzenia wystąpienia szablonu. Aby uzyskać więcej informacji, zobacz [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md). |

## <a name="remarks"></a>Uwagi

Klucze w strukturze `TEMPLATE_INSTANTIATION_DATA` są unikatowe w obrębie analizowanego śledzenia. Jednak dwa różne klucze pochodzące z różnych passów frontonu kompilatora mogą wskazywać na dwa identyczne typy. Podczas konsumowania `TEMPLATE_INSTANTIATION_DATA` informacji z wielu zakończonych powodzeniem kompilatorów należy użyć zdarzeń [SYMBOL_NAME](../event-table.md#symbol-name) , aby określić, czy dwa typy są takie same. zdarzenia `SymbolName` są emitowane na końcu przejścia frontonu kompilatora, po wykonaniu wszystkich wystąpień szablonu.

::: moniker-end
