---
title: Błąd kompilatora C3610 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3610
dev_langs:
- C++
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b46b3669978ff3735d5a16015ca0a01e65f07ae9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037856"
---
# <a name="compiler-error-c3610"></a>Błąd kompilatora C3610

"valuetype": typ wartościowy musi być "boxed" przed można wywołać metody "method"

Domyślnie typ wartości nie jest na stosie zarządzanym. Przed wywołaniem metody z klasy środowiska wykonawczego .NET, takich jak `Object`, musisz przenieść typu wartości do zarządzanej sterty.

C3610 jest dostępna, przy użyciu opcji kompilatora przestarzałe **: oldsyntax**.
