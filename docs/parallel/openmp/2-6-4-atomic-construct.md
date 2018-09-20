---
title: 2.6.4, konstrukcja atomic | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e4232ef1-4058-42ce-9de0-0ca788312aba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f92e0b0c881ec1f8d54adce4a12f58ad514ed8f5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437485"
---
# <a name="264-atomic-construct"></a>2.6.4 — konstrukcja niepodzielna

`atomic` Dyrektywy oznacza, że lokalizacja pamięci niepodzielne, aktualizowane zamiast uwidaczniania go do możliwości wielu jednoczesnych, zapisywanie wątków. Składnia `atomic` dyrektywy jest następująca:

```
#pragma omp atomic new-lineexpression-stmt
```

Instrukcja wyrażeń musi mieć jedną z następujących form:

*x binop*= *expr*

x ++

++ x

x —

--x

W poprzednim wyrażenia:

- *x* jest wyrażeniem l-wartości o typie skalarnym.

- *wyrażenie* to wyrażenie skalarne typu, a nie odwołuje się do obiekcie wyznaczonym przez *x*.

- `binop` nie jest przeciążony operator i jest jednym z +, \*, -, / &, ^, &#124;, <\<, lub >>.

Mimo że jest zdefiniowane w implementacji tego, czy implementacja zastępuje wszystkie `atomic` dyrektyw z **krytyczne** dyrektyw, które mają taki sam unikatowy *nazwa*, `atomic` — dyrektywa zezwala lepiej optymalizacji. Często sprzętu instrukcje są dostępne, można wykonać aktualizację atomic o najmniejszej obciążenie.

Tylko obciążenia i magazynu obiekcie wyznaczonym przez *x* są niepodzielne; oceny *expr* nie jest atomic. Aby uniknąć Sytuacje wyścigu, wszystkie aktualizacje lokalizacji, w sposób równoległy powinny być chronione przy użyciu `atomic` dyrektywy, z wyjątkiem tych, które są znane jako bez wyścigu.

Ograniczenia `atomic` dyrektywy jest następująca:

- Wszystkie odwołania niepodzielną do lokalizacji magazynu x w całym programie muszą mieć zgodne z typem.

## <a name="examples"></a>Przykłady:

```
extern float a[], *p = a, b;
/* Protect against races among multiple updates. */
#pragma omp atomic
a[index[i]] += b;
/* Protect against races with updates through a. */
#pragma omp atomic
p[i] -= 1.0f;

extern union {int n; float x;} u;
/* ERROR - References through incompatible types. */
#pragma omp atomic
u.n++;
#pragma omp atomic
u.x -= 1.0f;
```