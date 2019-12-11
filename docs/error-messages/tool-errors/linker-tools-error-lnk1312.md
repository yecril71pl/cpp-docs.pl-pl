---
title: Błąd narzędzi konsolidatora LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: e462d24f2eb54718ba73617146aab96bb14a66df
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990908"
---
# <a name="linker-tools-error-lnk1312"></a>Błąd narzędzi konsolidatora LNK1312

nieprawidłowy lub uszkodzony plik: nie można zaimportować zestawu

Podczas kompilowania zestawu, plik inny niż moduł lub zestaw skompilowany z **/CLR** został przekazano do **/ASSEMBLYMODULE** opcji konsolidatora.  Jeśli przeszedł plik obiektu do **/ASSEMBLYMODULE**, wystarczy przekazać obiekt bezpośrednio do konsolidatora, a nie do **/ASSEMBLYMODULE**.

## <a name="example"></a>Przykład

Poniższy przykład utworzył plik. obj.

```cpp
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

## <a name="example"></a>Przykład

Poniższy przykład generuje LNK1312.

```cpp
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```
