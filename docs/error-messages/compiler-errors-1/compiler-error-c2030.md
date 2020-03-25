---
title: Błąd kompilatora C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: e3f3936e6fd37da16c923cb482f45cec11833b3c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208035"
---
# <a name="compiler-error-c2030"></a>Błąd kompilatora C2030

destruktor z ułatwieniami dostępu "protected private" nie może być składową klasy zadeklarowanej jako "Sealed"

Klasa środowisko wykonawcze systemu Windows zadeklarowana jako `sealed` nie może mieć chronionego destruktora prywatnego. Tylko publiczne wirtualne i prywatne destruktory niewirtualne są dozwolone w typach zapieczętowanych. Aby uzyskać więcej informacji, zobacz [klasy referencyjne i struktury](../../cppcx/ref-classes-and-structs-c-cx.md).

Aby naprawić ten błąd, Zmień dostępność destruktora.
