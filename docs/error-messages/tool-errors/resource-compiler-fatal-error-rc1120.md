---
title: Błąd krytyczny kompilatora zasobów RC1120
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: 855a76ff63145695a7063944701d7acc684e0084
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173013"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Błąd krytyczny kompilatora zasobów RC1120

za mało pamięci, wymagana liczba bajtów

Kompilator zasobów nie przeprowadził magazynu dla elementów, które przechowuje w jego stertie. Zwykle jest to wynikiem zbyt wielu symboli.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać ten problem, można użyć następujących rozwiązań

1. Zwiększ ilość miejsca na pliki wymiany systemu Windows. Aby uzyskać więcej informacji na temat zwiększania przestrzeni wymiany plików, zobacz pamięć wirtualna w pomocy systemu Windows.

1. Eliminuj zbędne pliki dołączane, szczególnie niepotrzebne `#define`s i prototypy funkcji.

1. Podziel bieżący plik na co najmniej dwa pliki i skompiluj je oddzielnie.

1. Usuń inne programy lub sterowniki działające w systemie, które mogą zużywać znaczną ilość pamięci.
