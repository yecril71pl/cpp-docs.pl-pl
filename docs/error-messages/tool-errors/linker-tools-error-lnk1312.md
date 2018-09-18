---
title: Błąd narzędzi konsolidatora LNK1312 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1312
dev_langs:
- C++
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 335a3976675f36e3da295bc23c8e17440a56a505
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088656"
---
# <a name="linker-tools-error-lnk1312"></a>Błąd narzędzi konsolidatora LNK1312

nieprawidłowy lub uszkodzony plik: nie można zaimportować zestawu

Podczas tworzenia zestawu, pliki inne niż moduł lub zestawu skompilowanego z **/CLR** został przekazany do **assemblymodule** — opcja konsolidatora.  Jeśli przekazany plik do obiektu **assemblymodule**, po prostu Przekaż obiekt bezpośrednio do konsolidatora, zamiast do **assemblymodule**.

## <a name="example"></a>Przykład

Poniższy przykład utworzono plik .obj.

```
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie LNK1312.

```
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```