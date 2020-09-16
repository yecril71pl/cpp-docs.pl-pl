---
title: Błąd narzędzi konsolidatora LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: 69af2bd2c22fdb1188cf0b7119791e451e80f966
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686499"
---
# <a name="linker-tools-error-lnk1312"></a>Błąd narzędzi konsolidatora LNK1312

nieprawidłowy lub uszkodzony plik: nie można zaimportować zestawu

Podczas kompilowania zestawu, plik inny niż moduł lub zestaw skompilowany z **/CLR** został przekazano do **/ASSEMBLYMODULE** opcji konsolidatora.  Jeśli przeszedł plik obiektu do **/ASSEMBLYMODULE**, wystarczy przekazać obiekt bezpośrednio do konsolidatora, a nie do **/ASSEMBLYMODULE**.

## <a name="examples"></a>Przykłady

Poniższy przykład utworzył plik. obj.

```cpp
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

Poniższy przykład generuje LNK1312.

```cpp
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```
