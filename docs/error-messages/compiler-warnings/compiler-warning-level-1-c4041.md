---
title: Kompilator ostrzeżenie (poziom 1) C4041
ms.date: 11/04/2016
f1_keywords:
- C4041
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
ms.openlocfilehash: 6e1f2a2396447038f6a117f66d4002bea7fd7486
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513675"
---
# <a name="compiler-warning-level-1-c4041"></a>Kompilator ostrzeżenie (poziom 1) C4041

ograniczenie kompilatora: Kończenie wyników przeglądarki

Informacje o przeglądarce Przekroczono ograniczenie kompilatora.

To ostrzeżenie może być spowodowany przez kompilowanie za pomocą [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (w tym zmiennych lokalnych informacji przeglądarki).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Kompiluj przy użyciu /Fr (informacje o przeglądarce bez zmienne lokalne).

1. Wyłącz wyników przeglądarki (Kompiluj bez /FR lub /Fr).