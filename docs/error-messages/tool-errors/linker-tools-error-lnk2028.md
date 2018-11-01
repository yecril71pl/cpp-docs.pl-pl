---
title: Błąd narzędzi konsolidatora LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: ed2dc1a95d4dd7c447b360da21b5046e20f79083
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643680"
---
# <a name="linker-tools-error-lnk2028"></a>Błąd narzędzi konsolidatora LNK2028

"*exported_function*" (*decorated_name*) przywoływany w funkcji "*function_containing_function_call*" (*decorated_name*)

## <a name="remarks"></a>Uwagi

Podczas próby zaimportowania funkcji natywnej do czystego obrazu, należy pamiętać, że niejawne konwencji wywoływania różnią się macierzystych i czystych kompilacji.

**/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

## <a name="example"></a>Przykład

Ten przykładowy kod generuje składnika za pomocą funkcji eksportowanych, natywnego, którego Konwencja wywołania jest niejawnie [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>Przykład

Poniższy przykład tworzy czystego klienta, który używa funkcji macierzystej. Jednak konwencji wywoływania, w obszarze **/CLR: pure** jest [__clrcall](../../cpp/clrcall.md). Poniższy przykład spowoduje wygenerowanie LNK2028.

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```