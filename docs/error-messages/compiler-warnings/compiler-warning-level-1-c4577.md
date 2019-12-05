---
title: Ostrzeżenie kompilatora C4577
description: Ostrzeżenie kompilatora C4577 opis i rozwiązanie.
ms.date: 09/18/2019
f1_keywords:
- C4577
helpviewer_keywords:
- C4577
ms.openlocfilehash: e29e47b2a268d86f7f6a280b79a1604fe6eff8a4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810560"
---
# <a name="compiler-warning-level-1-c4577"></a>Ostrzeżenie kompilatora (poziom 1) C4577

> użyto "noexcept" bez określonego trybu obsługi wyjątków; zakończenie przy wyjątku nie jest gwarantowane. Określ/EHsc

Kompilator wykrył specyfikację `noexcept`, ale nie określono C++ standardowej obsługi wyjątków. Kompilator nie obsługuje w C++ pełni obsługi wyjątków zgodnie ze standardem, chyba że określono opcję kompilatora [/EHsc](../../build/reference/eh-exception-handling-model.md) . Aby rozwiązać ten problem, należy ustawić opcję kompilatora **/EHsc** .

To ostrzeżenie jest Nowość w programie Visual Studio 2015 i jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
