---
title: Błąd narzędzi konsolidatora LNK2011 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2011
dev_langs:
- C++
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18562a21886508ff0766641f95ac2e15b76fd424
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095394"
---
# <a name="linker-tools-error-lnk2011"></a>Błąd narzędzi konsolidatora LNK2011

prekompilowany obiekt nie został skonsolidowany; Obraz może nie działać.

Korzystając z wstępnie skompilowanych nagłówków, LINK wymaga, że wszystkie pliki obiektów utworzonych za pomocą wstępnie skompilowanych nagłówków muszą zostać połączone w. Jeśli masz plik źródłowy, który służy do generowania prekompilowanego nagłówka do użytku z innych plikach źródłowych, możesz teraz musi zawierać pliku obiektu utworzonym wraz z prekompilowanego pliku nagłówkowego.

Na przykład jeśli skompilujesz plik o nazwie STUB.cpp tworzenia prekompilowanego nagłówka do użytku z innych plikach źródłowych, należy połączyć z STUB.obj lub otrzyma ten błąd. W następujących wierszach polecenia w pierwszej linii adresu służy do tworzenia prekompilowanego nagłówka COMMON.pch, który jest używany z PROG1.cpp i PROG2.cpp w wierszach, 2 i 3. Plik STUB.cpp zawiera tylko `#include` wierszy (takie same `#include` wiersze, tak jak PROG1.cpp i PROG2.cpp) i jest używany tylko do generowania wstępnie skompilowanych nagłówków. W ostatnim wierszu STUB.obj muszą być połączone w celu uniknięcia LNK2011.

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```