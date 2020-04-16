---
title: Zakres wartości char
ms.date: 11/04/2016
ms.assetid: 15ae9781-ec21-4333-bba8-6d2383bbf7f1
ms.openlocfilehash: 8cb2609aca910056b5243fddc868710581e576e7
ms.sourcegitcommit: 9266fc76ac2e872e35a208b4249660dfdfc87cba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81480903"
---
# <a name="range-of-char-values"></a>Zakres wartości char

**ANSI 3.2.1.1** Czy "zwykły" **char** ma taki sam zakres wartości jak **znak podpisany** lub **niepodpisany char**

Wszystkie podpisane wartości znaków wahają się od -128 do 127. Wszystkie niepodpisane wartości znaków wahają się od 0 do 255.

Opcja [`/J`](../build/reference/j-default-char-type-is-unsigned.md) kompilatora zmienia domyślny typ **dla char** z **podpisanego char** na **niepodpisany znak**.

## <a name="see-also"></a>Zobacz też

[Znaków](../c-language/characters.md)
