---
title: Ostrzeżenie LNK4224 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: 9e52dd533d897e729aba5f2b43ea6c019a024d43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182984"
---
# <a name="linker-tools-warning-lnk4224"></a>Ostrzeżenie LNK4224 narzędzi konsolidatora

> *opcja* nie jest już obsługiwana; Ignoruj

## <a name="remarks"></a>Uwagi

Określono nieprawidłową, przestarzałą opcję konsolidatora i została zignorowana.

Na przykład LNK4224 narzędzi KONSOLIDATORA może wystąpić, jeśli dyrektywa/Comment pojawia się w. obj. Dyrektywa/Comment zostałaby dodana za pośrednictwem [komentarza (CC++/)](../../preprocessor/comment-c-cpp.md) pragma przy użyciu przestarzałej opcji exestr. Użyj polecenia DUMPBIN [/All](../../build/reference/all.md) , aby wyświetlić dyrektywy konsolidatora w pliku. obj.

Jeśli to możliwe, zmodyfikuj Źródło dla. obj i Usuń pragmę. Jeśli zignorujesz to ostrzeżenie, istnieje możliwość, że plik wykonywalny skompilowany za pomocą **/CLR: Pure** nie będzie działać zgodnie z oczekiwaniami. **/CLR: Pure** kompilator Option jest przestarzały w programie visual Studio 2015 i nieobsługiwany w programie visual Studio 2017.

## <a name="example"></a>Przykład

Poniższy przykład generuje LNK4224 narzędzi KONSOLIDATORA.

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```
