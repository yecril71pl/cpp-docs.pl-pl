---
title: Błąd kompilatora C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: fb4a0e6f3f6ec227b978ae0b7d3864b2134de986
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677607"
---
# <a name="compiler-error-c2834"></a>Błąd kompilatora C2834

"operator operator" musi być globalnie kwalifikowany

`new` i `delete` operatory są powiązane z klasą, gdzie się znajdują. Rozpoznawanie zakresów nie można wybrać wersję programu `new` lub `delete` z innej klasy. Aby zaimplementować wiele form `new` lub `delete` operatora, tworzy wersji operatora z bardzo formalnych parametrów.