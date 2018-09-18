---
title: Kompilator ostrzeżenie (poziom 1) C4041 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ff2c8066557e420ecd7de561d7731b7be733315
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085787"
---
# <a name="compiler-warning-level-1-c4041"></a>Kompilator ostrzeżenie (poziom 1) C4041

ograniczenie kompilatora: Kończenie wyników przeglądarki

Informacje o przeglądarce Przekroczono ograniczenie kompilatora.

To ostrzeżenie może być spowodowany przez kompilowanie za pomocą [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (w tym zmiennych lokalnych informacji przeglądarki).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Kompiluj przy użyciu /Fr (informacje o przeglądarce bez zmienne lokalne).

1. Wyłącz wyników przeglądarki (Kompiluj bez /FR lub /Fr).