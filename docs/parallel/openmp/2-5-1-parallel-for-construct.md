---
title: 2.5.1 równoległe konstrukcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfff3b0c17dd098b5d802af61a7ca1f81cb02845
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373964"
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