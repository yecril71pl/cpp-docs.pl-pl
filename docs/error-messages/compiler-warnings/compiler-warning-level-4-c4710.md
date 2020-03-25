---
title: Ostrzeżenie kompilatora (poziom 4) C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: c39848b9b3e94e35c4d0c0937a0974b717c6bd8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198179"
---
# <a name="compiler-warning-level-4-c4710"></a>Ostrzeżenie kompilatora (poziom 4) C4710

"Function": funkcja nie została wbudowana

Dana funkcja została wybrana do rozwijania wbudowanego, ale kompilator nie przeprowadził tworzenia konspektu.

Tworzenie i składanie jest wykonywane według uznania kompilatora. **Wbudowane** słowo kluczowe, takie jak słowo kluczowe **register** , jest używane jako Wskazówka dla kompilatora. Kompilator używa algorytmów heurystycznych, aby określić, czy powinien on być wbudowany w konkretną funkcję w celu przyspieszenia kodu podczas kompilowania do szybkości, czy też powinien być wbudowany w konkretną funkcję, aby zmniejszyć kod podczas kompilowania do miejsca. Kompilator będzie tylko wbudowanych bardzo małych funkcji podczas kompilowania do miejsca.

W niektórych przypadkach kompilator nie będzie wbudowanej określonej funkcji dla powodów mechanicznych. Zobacz [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) , aby zapoznać się z listą przyczyn, które kompilator nie może zawbudowanić funkcji.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .
