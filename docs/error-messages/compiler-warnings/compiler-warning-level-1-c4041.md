---
title: Ostrzeżenie kompilatora (poziom 1) C4041
ms.date: 11/04/2016
f1_keywords:
- C4041
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
ms.openlocfilehash: 14ea6d9cae3b490107b656153bb68815026971e1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164238"
---
# <a name="compiler-warning-level-1-c4041"></a>Ostrzeżenie kompilatora (poziom 1) C4041

ograniczenie kompilatora: Trwa kończenie wyświetlania wyników przeglądarki

Informacje o przeglądarce przekraczają limit kompilatora.

To ostrzeżenie może być spowodowane kompilacją z [/fr](../../build/reference/fr-fr-create-dot-sbr-file.md) (informacje o przeglądarce, w tym zmienne lokalne).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać ten problem, można użyć następujących rozwiązań

1. Kompiluj z/fr (informacje o przeglądarce bez zmiennych lokalnych).

1. Wyłącz dane wyjściowe przeglądarki (Kompiluj bez/FR lub/fr).
