---
title: Błąd kompilatora C2813 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8b7912edeea9edbb32632953166fc2558aeed3e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062660"
---
# <a name="compiler-error-c2813"></a>Błąd kompilatora C2813

\#Import nie jest obsługiwany z /MP

C2813 jest emitowane, jeśli za pomocą polecenia kompilatora określisz **/MP** — opcja kompilatora i dwa lub więcej plików do kompilacji i co najmniej jeden z plików zawiera[#import](../../preprocessor/hash-import-directive-cpp.md) dyrektywy preprocesora. [#Import](../../preprocessor/hash-import-directive-cpp.md) — dyrektywa generuje klasy języka C++ z typów w bibliotece określonego typu, a następnie zapisuje dwa pliki nagłówkowe tych klas. [#Import](../../preprocessor/hash-import-directive-cpp.md) dyrektywy nie jest obsługiwana, ponieważ w wielu jednostkach kompilacji importowania biblioteki typów w tym samym, tych jednostek w konflikcie, gdy użytkownik próbuje zapisać te same pliki nagłówka, w tym samym czasie.

Ten błąd kompilatora i **/MP** — opcja kompilatora są nowością w programie Visual Studio 2008.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2813. Wiersza polecenia w pliku "kompilacji z:" wskazuje komentarz, aby kompilator korzystać **/MP** i **/c** opcje kompilatora do skompilowania kilka plików. Zawiera co najmniej jeden z plików [#import](../../preprocessor/hash-import-directive-cpp.md) dyrektywy. Używamy tego samego pliku dwa razy dla testowania w tym przykładzie.

```
// C2813.cpp
// compile with: /MP /c C2813.cpp C2813.cpp
#import "C:\windows\system32\stdole2.tlb"   // C2813
int main()
{
}
```