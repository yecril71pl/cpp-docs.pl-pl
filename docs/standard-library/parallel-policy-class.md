---
title: parallel_policy klasy
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_policy
ms.openlocfilehash: 7bb2b095a50e664dfc585e0bd4aaa608a6ad8e95
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268043"
---
# <a name="parallelpolicy-class"></a>parallel_policy klasy

Używany jako unikatowy typ, do odróżniania przeciążenie algorytmu równoległego i wskazują, że wykonywanie algorytmu równoległego może odbywać się równolegle.

## <a name="syntax"></a>Składnia

```cpp
class execution::parallel_policy;
```

## <a name="remarks"></a>Uwagi

Podczas wykonywania algorytmu równoległego za pomocą `execution::parallel_policy` zasad, jeśli wywołanie funkcji dostępu do elementu kończy się za pośrednictwem nieprzechwycony wyjątek `terminate()` nosi nazwę.
