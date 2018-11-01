---
title: Błąd kompilatora C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: eec529f43e23810843651888ef5722c5d0a0b2c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651948"
---
# <a name="compiler-error-c2567"></a>Błąd kompilatora C2567

Nie można otworzyć metadanych w "file", plik może zostały usunięte lub przeniesione

Plik metadanych, który był przywoływany w źródle (przy użyciu `#using`) nie został odnaleziony w tym samym katalogu przez proces zapleczu kompilatora równie przez proces fronton kompilatora. Zobacz [# dyrektywa using](../../preprocessor/hash-using-directive-cpp.md) Aby uzyskać więcej informacji.

Może być spowodowane C2567, jeśli kompilujesz z opcją **/c** dla jednej maszyny, a następnie spróbuj Generowanie łączonych kodów czasowych na innym komputerze. Aby uzyskać więcej informacji, zobacz [opcję/LTCG (Generowanie kodu Link-time)](../../build/reference/ltcg-link-time-code-generation.md)).

Może również wskazywać, że komputer będzie miał nie większej ilości pamięci.

Aby naprawić ten błąd, upewnij się, czy plik metadanych jest w tej samej lokalizacji w katalogu dla wszystkich etapów procesu kompilacji.