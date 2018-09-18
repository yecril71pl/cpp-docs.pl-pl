---
title: Błąd kompilatora C2834 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2834
dev_langs:
- C++
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b94e1a3fba9bc3589af020340651b4546347cf1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089349"
---
# <a name="compiler-error-c2834"></a>Błąd kompilatora C2834

"operator operator" musi być globalnie kwalifikowany

`new` i `delete` operatory są powiązane z klasą, gdzie się znajdują. Rozpoznawanie zakresów nie można wybrać wersję programu `new` lub `delete` z innej klasy. Aby zaimplementować wiele form `new` lub `delete` operatora, tworzy wersji operatora z bardzo formalnych parametrów.