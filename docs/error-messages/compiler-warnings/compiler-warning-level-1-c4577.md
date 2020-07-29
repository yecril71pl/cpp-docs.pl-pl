---
title: Ostrzeżenie kompilatora C4577
description: Ostrzeżenie kompilatora C4577 opis i rozwiązanie.
ms.date: 09/18/2019
f1_keywords:
- C4577
helpviewer_keywords:
- C4577
ms.openlocfilehash: fb9d412196e7764326a397a4bf6e76c8723ac2ae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87196256"
---
# <a name="compiler-warning-level-1-c4577"></a>Ostrzeżenie kompilatora (poziom 1) C4577

> użyto "noexcept" bez określonego trybu obsługi wyjątków; zakończenie przy wyjątku nie jest gwarantowane. Określ/EHsc

Kompilator wykrył **`noexcept`** specyfikację, ale nie określono standardowej obsługi wyjątków C++. Kompilator nie obsługuje w pełni obsługi wyjątków zgodnie ze standardem C++, chyba że określono opcję kompilatora [/EHsc](../../build/reference/eh-exception-handling-model.md) . Aby rozwiązać ten problem, należy ustawić opcję kompilatora **/EHsc** .

To ostrzeżenie jest Nowość w programie Visual Studio 2015 i jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
