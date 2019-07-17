---
title: parallel_unsequenced_policy klasy
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_unsequenced_policy
ms.openlocfilehash: 92b4e3ce3743fdd3d5ba112a333b2306829b95d4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267989"
---
# <a name="parallelunsequencedpolicy-class"></a>parallel_unsequenced_policy klasy

Używany jako unikatowy typ, do odróżniania przeciążenie algorytmu równoległego i wskazywać, że algorytmu równoległego wykonywania może być zrównoleglona i zwektoryzowana.

## <a name="syntax"></a>Składnia

```cpp
class execution::parallel_unsequenced_policy;
```

## <a name="remarks"></a>Uwagi

Podczas wykonywania algorytmu równoległego za pomocą `execution::parallel_unsequenced_policy` zasad, jeśli wywołanie funkcji dostępu do elementu kończy się za pośrednictwem nieprzechwycony wyjątek `terminate()` nosi nazwę.
