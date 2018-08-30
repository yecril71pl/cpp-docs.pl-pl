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
ms.openlocfilehash: ffbc1d7fc7f74121c37c9e80a538ec60f2265701
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219565"
---
# <a name="obj-files-as-linker-input"></a>Pliki .Obj — Wejście konsolidatora

Narzędzia konsolidatora (LINK. Z rozszerzeniem EXE) akceptuje plików .obj, które są w Common Object File Format (COFF).

## <a name="remarks"></a>Uwagi

Firma Microsoft udostępnia pełny opis wspólny format plików obiektu. Aby uzyskać więcej informacji, zobacz [formatu PE](/windows/desktop/Debug/pe-format).

## <a name="unicode-support"></a>Obsługa formatu Unicode

Począwszy od programu Visual Studio 2005, kompilator Microsoft Visual C++ obsługuje znaki Unicode w identyfikatorach, zgodnie z definicją C ISO/IEC i standardów C++. Poprzednie wersje kompilatora obsługiwane tylko znaki ASCII w identyfikatorach. Do obsługi standardu Unicode w nazwach funkcji, klas i danych statycznych, kompilatora i konsolidatora, użyj kodowania Unicode UTF-8 dla symboli COFF, pliki .obj. Kodowanie UTF-8 jest upwardly zgodnych z kodowaniem ASCII używane we wcześniejszych wersjach programu Visual Studio.

Aby uzyskać więcej informacji dotyczących kompilatora i konsolidatora, zobacz [Obsługa formatu Unicode w kompilatorze i Konsolidatorze](../../build/reference/unicode-support-in-the-compiler-and-linker.md). Aby uzyskać więcej informacji na temat standardu Unicode, zobacz [Unicode](http://go.microsoft.com/fwlink/p/?linkid=37123) organizacji.

## <a name="see-also"></a>Zobacz także

[Pliki wejściowe LINK](../../build/reference/link-input-files.md)  
[Opcje konsolidatora](../../build/reference/linker-options.md)  
[Obsługa formatu Unicode](../../text/support-for-unicode.md)  
[Obsługa formatu Unicode w kompilatorze i konsolidatorze](../../build/reference/unicode-support-in-the-compiler-and-linker.md)  
[Unicode standard](http://go.microsoft.com/fwlink/p/?linkid=37123)  
[Formatu PE](/windows/desktop/Debug/pe-format)  
