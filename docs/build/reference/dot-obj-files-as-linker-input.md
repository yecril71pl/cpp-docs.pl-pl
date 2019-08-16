---
title: Pliki .Obj — Wejście konsolidatora
ms.date: 12/29/2017
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
ms.openlocfilehash: 3e02ccc09ae8c9c2f3df88bc1767ff0188baa1f4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492938"
---
# <a name="obj-files-as-linker-input"></a>Pliki .Obj — Wejście konsolidatora

Narzędzie konsolidatora (LINK. EXE) akceptuje pliki. obj, które znajdują się w typowym formacie plików obiektów (COFF).

## <a name="remarks"></a>Uwagi

Firma Microsoft oferuje pełny opis typowego formatu pliku obiektu. Aby uzyskać więcej informacji, zobacz [Format PE](/windows/win32/Debug/pe-format).

## <a name="unicode-support"></a>Obsługa Unicode

Począwszy od programu Visual Studio 2005, kompilator Microsoft MSVC obsługuje znaki Unicode w identyfikatorach zgodnie z definicją ISO/IEC C C++ i Standard. Poprzednie wersje kompilatora obsługują tylko znaki ASCII w identyfikatorach. Aby zapewnić obsługę Unicode w nazwach funkcji, klas i elementów statycznych, kompilator i konsolidator używają kodowania Unicode UTF-8 dla symboli COFF w plikach. obj. Kodowanie UTF-8 jest w większym zakresie zgodne z kodowaniem ASCII używanym przez wcześniejsze wersje programu Visual Studio.

Aby uzyskać więcej informacji na temat kompilatora i konsolidatora, zobacz [Obsługa standardu Unicode w kompilatorze i konsolidatorze](unicode-support-in-the-compiler-and-linker.md). Aby uzyskać więcej informacji na temat standardu Unicode, zobacz organizację [Unicode](https://www.unicode.org/) .

## <a name="see-also"></a>Zobacz także

[Pliki wejściowe LINK](link-input-files.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[Obsługa formatu Unicode](../../text/support-for-unicode.md)<br/>
[Obsługa formatu Unicode w kompilatorze i konsolidatorze](unicode-support-in-the-compiler-and-linker.md)<br/>
[Standard Unicode](https://www.unicode.org/)<br/>
[Format PE](/windows/win32/Debug/pe-format)
