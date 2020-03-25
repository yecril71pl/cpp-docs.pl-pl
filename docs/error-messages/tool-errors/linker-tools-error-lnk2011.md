---
title: Błąd narzędzi konsolidatora LNK2011
ms.date: 11/04/2016
f1_keywords:
- LNK2011
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
ms.openlocfilehash: e08f068099af68375523eae0f0cc4d63960f3261
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194814"
---
# <a name="linker-tools-error-lnk2011"></a>Błąd narzędzi konsolidatora LNK2011

wstępnie skompilowany obiekt nie jest połączony z; nie można uruchomić obrazu

Jeśli używasz prekompilowanych nagłówków, LINK wymaga, aby wszystkie pliki obiektów utworzone przy użyciu prekompilowanych nagłówków muszą być połączone. Jeśli masz plik źródłowy używany do generowania prekompilowanego nagłówka do użycia z innymi plikami źródłowymi, musisz teraz dołączyć plik obiektu utworzony razem z prekompilowanym nagłówkiem.

Na przykład, Jeśli kompilujesz plik o nazwie STUB. cpp, aby utworzyć prekompilowany nagłówek do użytku z innymi plikami źródłowymi, musisz połączyć się z klasą ZASTĘPCZą. obj lub ten błąd zostanie wyświetlony. W poniższych wierszach poleceń wiersz jeden jest używany do tworzenia prekompilowanego nagłówka, COMMON. PCH, który jest używany z PROG1. cpp i PROG2. cpp w wierszach 2 i 3. Plik ZASTĘPCZy. cpp zawiera tylko `#include` wierszy (te same wiersze `#include`, jak w PROG1. cpp i PROG2. cpp) i służy tylko do generowania prekompilowanych nagłówków. W ostatnim wierszu należy połączyć się z klasą ZASTĘPCZą. obj, aby uniknąć LNK2011.

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```
