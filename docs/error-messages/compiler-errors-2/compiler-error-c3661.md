---
title: Błąd kompilatora C3661 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3661
dev_langs:
- C++
helpviewer_keywords:
- C3661
ms.assetid: 50793fd1-1829-4b29-ad0d-094ef2068b43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7c7987e9ca84009cc8705c22a8f2ec7c3c89b00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026646"
---
# <a name="compiler-error-c3661"></a>Błąd kompilatora C3661

Lista jawnego przesłaniania nie znalazła żadnych metod aby je przesłonić

Jawne przesłanianie określona co najmniej jedną nazwę typu.  Jednak nie było żadnej funkcji o podpisie niezbędne w typów, który jest zgodny podpis funkcji nadrzędnych.  Próba zastąpienia opartego na nazwie typu, w określonym typy, które pasuje do podpisu przesłanianie funkcji musi istnieć jeden lub więcej funkcji wirtualnych.

Aby uzyskać więcej informacji, zobacz [jawne zastępowanie](../../windows/explicit-overrides-cpp-component-extensions.md).