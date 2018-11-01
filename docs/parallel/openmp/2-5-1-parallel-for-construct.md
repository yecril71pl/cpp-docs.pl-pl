---
title: 2.5.1 Konstrukcja równoległa
ms.date: 11/04/2016
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
ms.openlocfilehash: e74fa958a70fb10aadd39ccc6b4e56670bc072b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590336"
---
# <a name="251-parallel-for-construct"></a>2.5.1 Konstrukcja równoległa

**Równoległe w** dyrektywa jest skrót **równoległe** region, który zawiera tylko jeden **dla** dyrektywy. Składnia **równoległe w** dyrektywy jest następująca:

```
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Ta dyrektywa zezwala na wszystkie klauzule **równoległe** dyrektywy i **dla** dyrektywy, z wyjątkiem `nowait` klauzuli przy użyciu identycznych znaczenie i ograniczeń. Semantyka są takie same jak jawne określenie **równoległe** dyrektywy bezpośrednio następuje **dla** dyrektywy.

## <a name="cross-references"></a>Odsyłacze:

- **równoległe** dyrektywy, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.

- **Aby uzyskać** dyrektywy, zobacz [sekcji 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stronie 11.

- Klauzule atrybutu danych, zobacz [2.7.2 klauzule atrybutu udostępniania danych](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25.