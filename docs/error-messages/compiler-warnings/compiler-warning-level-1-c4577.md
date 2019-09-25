---
title: Ostrzeżenie kompilatora C4577
description: Ostrzeżenie kompilatora C4577 opis i rozwiązanie.
ms.date: 09/18/2019
helpviewer_keywords:
- C4577
ms.openlocfilehash: 637023f4c27f93238fbbd13b4a0e652e6cd958e0
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71241102"
---
# <a name="compiler-warning-level-1-c4577"></a>Ostrzeżenie kompilatora (poziom 1) C4577

> użyto "noexcept" bez określonego trybu obsługi wyjątków; zakończenie przy wyjątku nie jest gwarantowane. Określ/EHsc

Kompilator wykrył `noexcept` specyfikację, ale nie określono C++ standardowej obsługi wyjątków. Kompilator nie obsługuje w C++ pełni obsługi wyjątków zgodnie ze standardem, chyba że określono opcję kompilatora [/EHsc](../../build/reference/eh-exception-handling-model.md) . Aby rozwiązać ten problem, należy ustawić opcję kompilatora **/EHsc** .

To ostrzeżenie jest Nowość w programie Visual Studio 2015 i jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
