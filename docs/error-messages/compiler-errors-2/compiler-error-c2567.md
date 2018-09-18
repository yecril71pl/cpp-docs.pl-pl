---
title: Błąd kompilatora C2567 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2567
dev_langs:
- C++
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb09aacc1b81e9f0e0c9c96a496eccc89a061f37
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104247"
---
# <a name="compiler-error-c2567"></a>Błąd kompilatora C2567

Nie można otworzyć metadanych w "file", plik może zostały usunięte lub przeniesione

Plik metadanych, który był przywoływany w źródle (przy użyciu `#using`) nie został odnaleziony w tym samym katalogu przez proces zapleczu kompilatora równie przez proces fronton kompilatora. Zobacz [# dyrektywa using](../../preprocessor/hash-using-directive-cpp.md) Aby uzyskać więcej informacji.

Może być spowodowane C2567, jeśli kompilujesz z opcją **/c** dla jednej maszyny, a następnie spróbuj Generowanie łączonych kodów czasowych na innym komputerze. Aby uzyskać więcej informacji, zobacz [opcję/LTCG (Generowanie kodu Link-time)](../../build/reference/ltcg-link-time-code-generation.md)).

Może również wskazywać, że komputer będzie miał nie większej ilości pamięci.

Aby naprawić ten błąd, upewnij się, czy plik metadanych jest w tej samej lokalizacji w katalogu dla wszystkich etapów procesu kompilacji.