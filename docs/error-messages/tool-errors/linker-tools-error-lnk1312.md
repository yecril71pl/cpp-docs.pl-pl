---
title: Błąd narzędzi konsolidatora LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: 49fa7e7963d6bb561e1602b58fe1f26c5f3d54bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160474"
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