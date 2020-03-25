---
title: Ostrzeżenie LNK4006 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4006
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
ms.openlocfilehash: d949ba259de8e131f6191e757119b4c42effc3d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194320"
---
# <a name="linker-tools-warning-lnk4006"></a>Ostrzeżenie LNK4006 narzędzi konsolidatora

symbol jest już zdefiniowany w obiekcie; Druga Definicja została zignorowana

Dana `symbol`, wyświetlana w jego postaci dekoracyjnej, została wielokrotnie zdefiniowana. Gdy to ostrzeżenie zostanie napotkane, `symbol` zostanie dodane dwa razy, ale zostanie użyty tylko jego pierwszy formularz.

To ostrzeżenie można uzyskać, jeśli próbujesz scalić dwa libs importowania w jeden.

W przypadku ponownego kompilowania biblioteki wykonawczej C można zignorować ten komunikat.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać ten problem, można użyć następujących rozwiązań

1. Dana `symbol` może być spakowaną funkcją, utworzoną przez kompilację z [/Gy](../../build/reference/gy-enable-function-level-linking.md). Ten symbol został uwzględniony w więcej niż jednym pliku, ale został zmieniony między kompilacjami. Ponownie skompiluj wszystkie pliki, które zawierają `symbol`.

1. Dana `symbol` mogła być zdefiniowana inaczej w dwóch obiektach Członkowskich w różnych bibliotekach.

1. Wartość bezwzględna może być zdefiniowana dwa razy, z inną wartością w każdej definicji.

1. Jeśli komunikat o błędzie jest odbierany podczas łączenia bibliotek, `symbol` już istnieje w bibliotece dodawanej do programu.
