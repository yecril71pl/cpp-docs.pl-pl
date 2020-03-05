---
title: FILE_TYPE_CODE Wyliczenie
description: Zestaw C++ SDK usługi Build insights FILE_TYPE_CODE Wyliczenie.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e64f9315c62ce40c436032d6c96fdfa725847a7f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333721"
---
# <a name="file_type_code-enum"></a>FILE_TYPE_CODE Wyliczenie

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Wyliczenie `FILE_TYPE_CODE` opisuje typ pliku.

## <a name="members"></a>Elementy członkowskie

| Nazwa | Wartość | Opis |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 (0x00000000) | Typ pliku niewymieniony w tym wyliczeniu. |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | Plik obiektu (\*. obj). |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 (0x00000002) | Plik wykonywalny (\*. exe) lub biblioteka DLL (\*. dll). |
| `FILE_TYPE_CODE_LIB` | 3 (0x00000003) | Plik biblioteki statycznej (*. lib). |
| `FILE_TYPE_CODE_IMP_LIB` | 4 (0x00000004) | Biblioteka importu (*. lib) |
| `FILE_TYPE_CODE_EXP` | 5 (0x00000005) | Plik eksportu (*. EXP). |

## <a name="remarks"></a>Uwagi

::: moniker-end
