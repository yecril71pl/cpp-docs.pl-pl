---
title: Błąd kompilatora C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: 921992c678c1de0b74f99f544173478ebe809b2c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177459"
---
# <a name="compiler-error-c2567"></a>Błąd kompilatora C2567

nie można otworzyć metadanych w pliku "File", plik mógł zostać usunięty lub przeniesiony

Plik metadanych, do którego odwołuje się źródło (z `#using`), nie został odnaleziony w tym samym katalogu przez proces zaplecza kompilatora, ponieważ został on utworzony przez proces frontonu kompilatora. Aby uzyskać więcej informacji, zobacz [#using dyrektywie](../../preprocessor/hash-using-directive-cpp.md) .

C2567 może być spowodowana kompilacją z **/c** na jednym komputerze, a następnie próba generowania kodu w czasie konsolidacji na innym komputerze. Aby uzyskać więcej informacji, zobacz [/LTCG (generowanie kodu w czasie konsolidacji)](../../build/reference/ltcg-link-time-code-generation.md)).

Może również wskazywać, że komputer nie ma więcej pamięci.

Aby naprawić ten błąd, upewnij się, że plik metadanych znajduje się w tej samej lokalizacji katalogu dla wszystkich faz procesu kompilacji.
