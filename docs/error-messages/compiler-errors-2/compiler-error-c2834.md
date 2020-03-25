---
title: Błąd kompilatora C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: a6a7bc0591fd51c808c303e94eeaaffd6111ffcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201932"
---
# <a name="compiler-error-c2834"></a>Błąd kompilatora C2834

operator "operator" musi być globalnie kwalifikowany

Operatory `new` i `delete` są powiązane z klasą, gdzie się znajdują. Nie można użyć rozpoznawania zakresu w celu wybrania wersji `new` lub `delete` z innej klasy. Aby zaimplementować wiele form operatora `new` lub `delete`, należy utworzyć wersję operatora z dodatkowymi formalnymi parametrami.
