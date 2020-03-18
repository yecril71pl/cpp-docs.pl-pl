---
title: Klasa sequenced_policy
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::sequenced_policy
ms.openlocfilehash: 5647f20b560828016231a9bbd38977c51211e6bb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444917"
---
# <a name="sequenced_policy-class"></a>Klasa sequenced_policy

Używany jako unikatowy typ odróżnienia przeciążenia algorytmu równoległego i wymaganie, aby wykonywanie algorytmu równoległego mogło nie być równoległe.

## <a name="syntax"></a>Składnia

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>Uwagi

W trakcie wykonywania algorytmu równoległego przy użyciu zasad `execution::sequenced_policy`, jeśli wywołanie funkcji dostępu do elementu kończy się za pośrednictwem nieprzechwyconego wyjątku, `terminate()` zostanie wywołana.
