---
title: . Pliki obj jako wejście konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57907beaa30418ce31e6c46202149048d5c9dea1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="obj-files-as-linker-input"></a>Pliki .Obj — Wejście konsolidatora

Narzędzia konsolidatora (łącze. Wywołanie pliku EXE) akceptuje pliki obj w typowych obiektu pliku formatu (COFF).

## <a name="remarks"></a>Uwagi

Firma Microsoft udostępnia pełny opis typowych format pliku obiektu. Aby uzyskać więcej informacji, zobacz [formatu PE](https://msdn.microsoft.com/library/windows/desktop/ms680547).

## <a name="unicode-support"></a>Obsługa formatu Unicode

Począwszy od programu Visual Studio 2005, kompilator Microsoft Visual C++ obsługuje znaki Unicode w identyfikatorach zgodnie z definicją ISO/IEC C i C++ standardów. Poprzednie wersje kompilatora obsługiwane tylko znaki ASCII w identyfikatorach. Do obsługi standardu Unicode w nazwach funkcji, klasy i statyczne, kompilatorze i konsolidatorze Użyj kodowania Unicode UTF-8 dla symboli COFF w plikach .obj. Kodowanie UTF-8 jest upwardly zgodny z kodowaniem ASCII używane we wcześniejszych wersjach programu Visual Studio.

Aby uzyskać więcej informacji na temat kompilatorze i konsolidatorze, zobacz [obsługi formatu Unicode w kompilatorze i Konsolidatorze](../../build/reference/unicode-support-in-the-compiler-and-linker.md). Aby uzyskać więcej informacji na temat standardu Unicode, zobacz [Unicode](http://go.microsoft.com/fwlink/p/?linkid=37123) organizacji.

## <a name="see-also"></a>Zobacz także

[Pliki wejściowe LINK](../../build/reference/link-input-files.md)  
[Opcje konsolidatora](../../build/reference/linker-options.md)  
[Obsługa formatu Unicode](../../text/support-for-unicode.md)  
[Obsługa formatu Unicode w kompilatorze i konsolidatorze](../../build/reference/unicode-support-in-the-compiler-and-linker.md)  
[Unicode standard](http://go.microsoft.com/fwlink/p/?linkid=37123)  
[Formatu PE](https://msdn.microsoft.com/library/windows/desktop/ms680547)  
