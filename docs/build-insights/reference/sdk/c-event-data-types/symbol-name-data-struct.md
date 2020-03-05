---
title: Struktura SYMBOL_NAME_DATA
description: Zestaw C++ SDK usługi Build insights SYMBOL_NAME_DATA odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 618e84f198c20aa089dc7e06e1e6c09b96b6d273
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333637"
---
# <a name="symbol_name_data-structure"></a>Struktura SYMBOL_NAME_DATA

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `SYMBOL_NAME_DATA` opisuje symbol frontonu kompilatora.

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
| `Key` | Klucz symbolu. Ta wartość jest unikatowa w obrębie analizowanego śledzenia. |
| `Name` | Nazwa symbolu. |

## <a name="remarks"></a>Uwagi

Symbole pochodzące z dwóch różnych przebiegów frontonu kompilatora mogą mieć taką samą nazwę, ale inny klucz. W takim przypadku należy użyć nazw symboli, aby określić, czy dwa typy są takie same.

::: moniker-end
