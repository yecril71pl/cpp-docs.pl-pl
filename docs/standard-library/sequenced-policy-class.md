---
title: sequenced_policy klasy
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_policy
ms.openlocfilehash: 63be7166b84fa452f53baf6b6de16831eb657a23
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268112"
---
# <a name="sequencedpolicy-class"></a>sequenced_policy klasy

Używane jako typ unikatowy odróżnić przeciążenie algorytmu równoległego, i wymagają, że algorytmu równoległego wykonywania może nie być przetwarzane równolegle.

## <a name="syntax"></a>Składnia

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>Uwagi

Podczas wykonywania algorytmu równoległego za pomocą `execution::sequenced_policy` zasad, jeśli wywołanie funkcji dostępu do elementu kończy się za pośrednictwem nieprzechwycony wyjątek `terminate()` nosi nazwę.
