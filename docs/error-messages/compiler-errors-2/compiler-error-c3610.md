---
title: Błąd kompilatora C3610
ms.date: 11/04/2016
f1_keywords:
- C3610
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
ms.openlocfilehash: 9965e6420171b2ea48c8fb7bacc0a5a37ea2f227
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344610"
---
# <a name="compiler-error-c3610"></a>Błąd kompilatora C3610

"valuetype": typ wartościowy musi być "boxed" przed można wywołać metody "method"

Domyślnie typ wartości nie jest na stosie zarządzanym. Przed wywołaniem metody z klasy środowiska wykonawczego .NET, takich jak `Object`, musisz przenieść typu wartości do zarządzanej sterty.

C3610 jest dostępna, przy użyciu opcji kompilatora przestarzałe **: oldsyntax**.
