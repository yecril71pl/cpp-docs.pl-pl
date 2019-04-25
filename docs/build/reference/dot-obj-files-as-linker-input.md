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
ms.openlocfilehash: c55c3181c2ddfabddce882a473e56d952a7e5d81
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293280"
---
# <a name="obj-files-as-linker-input"></a>Pliki .Obj — Wejście konsolidatora

Narzędzia konsolidatora (LINK. Z rozszerzeniem EXE) akceptuje plików .obj, które są w Common Object File Format (COFF).

## <a name="remarks"></a>Uwagi

Firma Microsoft udostępnia pełny opis wspólny format plików obiektu. Aby uzyskać więcej informacji, zobacz [formatu PE](/windows/desktop/Debug/pe-format).

## <a name="unicode-support"></a>Obsługa formatu Unicode

Począwszy od programu Visual Studio 2005 za pomocą kompilatora MSVC firmy Microsoft obsługuje znaki Unicode w identyfikatorach, zgodnie z definicją C ISO/IEC i standardów C++. Poprzednie wersje kompilatora obsługiwane tylko znaki ASCII w identyfikatorach. Do obsługi standardu Unicode w nazwach funkcji, klas i danych statycznych, kompilatora i konsolidatora, użyj kodowania Unicode UTF-8 dla symboli COFF, pliki .obj. Kodowanie UTF-8 jest upwardly zgodnych z kodowaniem ASCII używane we wcześniejszych wersjach programu Visual Studio.

Aby uzyskać więcej informacji dotyczących kompilatora i konsolidatora, zobacz [Obsługa formatu Unicode w kompilatorze i Konsolidatorze](unicode-support-in-the-compiler-and-linker.md). Aby uzyskać więcej informacji na temat standardu Unicode, zobacz [Unicode](http://www.unicode.org/) organizacji.

## <a name="see-also"></a>Zobacz także

[Pliki wejściowe LINK](link-input-files.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[Obsługa formatu Unicode](../../text/support-for-unicode.md)<br/>
[Obsługa formatu Unicode w kompilatorze i konsolidatorze](unicode-support-in-the-compiler-and-linker.md)<br/>
[Unicode standard](http://www.unicode.org/)<br/>
[Formatu PE](/windows/desktop/Debug/pe-format)
