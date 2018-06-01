---
title: Ostrzeżenie LNK4224 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4224
dev_langs:
- C++
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bdffdf3469cc3a0e5d41b0504b882513d44b63c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703990"
---
# <a name="linker-tools-warning-lnk4224"></a>Ostrzeżenie LNK4224 narzędzi konsolidatora

> *Opcja* nie jest już obsługiwany; zignorowano

## <a name="remarks"></a>Uwagi

— Opcja konsolidatora nieprawidłowy, przestarzałe został określony i zignorowany.

Na przykład LNK4224 może wystąpić, jeśli dyrektywa/Comment pojawia się w. obiektu Dyrektywa/Comment zostałyby dodane za pośrednictwem [komentarz (C/C++)](../../preprocessor/comment-c-cpp.md) pragma przy użyciu opcji exestr przestarzałe. Użyj polecenia dumpbin [/ALL](../../build/reference/all.md) do wyświetlenia w pliku .obj dyrektywy konsolidatora.

Jeśli to możliwe zmodyfikuj źródła dla plików .obj i Usuń pragma. Jeśli możesz zignorować to ostrzeżenie, istnieje możliwość, że .executable skompilowana z **/CLR: pure** nie będzie działać zgodnie z oczekiwaniami. **/CLR: pure** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

## <a name="example"></a>Przykład

Poniższy przykład generuje LNK4224.

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```