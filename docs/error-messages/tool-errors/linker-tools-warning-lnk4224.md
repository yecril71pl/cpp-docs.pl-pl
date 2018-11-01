---
title: Ostrzeżenie LNK4224 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: eb0a019cc80e5218a52697b8bcd5e91b811d04d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465328"
---
# <a name="linker-tools-warning-lnk4224"></a>Ostrzeżenie LNK4224 narzędzi konsolidatora

> *Opcja* nie jest już obsługiwany; zignorowano

## <a name="remarks"></a>Uwagi

— Opcja konsolidatora nieprawidłowy, przestarzałe została określona i ignorowane.

Na przykład LNK4224 może wystąpić, jeśli w pojawia się dyrektywa/Comment. obiektu Dyrektywa/Comment były dodawane przy użyciu [komentarz (C/C++)](../../preprocessor/comment-c-cpp.md) pragma, przy użyciu opcji exestr przestarzałe. Użyj polecenia dumpbin [/ALL](../../build/reference/all.md) wyświetlić dyrektywy konsolidatora w pliku .obj.

Jeśli to możliwe modyfikowanie źródła dla plików .obj i Usuń pragmy. Jeśli zignorujesz to ostrzeżenie, jest możliwe, że .executable skompilowany przy użyciu **/CLR: pure** nie będzie działać zgodnie z oczekiwaniami. **/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie LNK4224.

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```