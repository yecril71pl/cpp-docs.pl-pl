---
title: Błąd kompilatora C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: f9090e098d7f523bf7bc12b7fa4d9312f6ca5466
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212907"
---
# <a name="compiler-error-c2030"></a>Błąd kompilatora C2030

destruktor z ułatwieniami dostępu "protected private" nie może być składową klasy zadeklarowanej jako "Sealed"

Klasa środowisko wykonawcze systemu Windows zadeklarowana jako **`sealed`** nie może mieć chronionego destruktora prywatnego. Tylko publiczne wirtualne i prywatne destruktory niewirtualne są dozwolone w typach zapieczętowanych. Aby uzyskać więcej informacji, zobacz [klasy referencyjne i struktury](../../cppcx/ref-classes-and-structs-c-cx.md).

Aby naprawić ten błąd, Zmień dostępność destruktora.
