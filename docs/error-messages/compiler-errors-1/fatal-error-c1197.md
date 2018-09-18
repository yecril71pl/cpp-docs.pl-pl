---
title: Błąd krytyczny C1197 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1197
dev_langs:
- C++
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58561e7bd906fc750779ef53a4f68ec27088a3b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024765"
---
# <a name="fatal-error-c1197"></a>Błąd krytyczny C1197

Nie można odwołać "mscorlib.dll_1", ponieważ program istnieje już odwołanie do "mscorlib.dll_2"

Kompilator jest dopasowany do wersji środowiska uruchomieniowego języka wspólnego.  Jednak podjęto próbę odwołania wersję pliku środowiska uruchomieniowego języka wspólnego z poprzedniej wersji.

Aby rozwiązać ten problem, odwoływać się tylko pliki z wersji środowiska uruchomieniowego języka wspólnego dostarczanej z wersją programu Visual C++ są kompilowania za pomocą.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C1197:

```
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```