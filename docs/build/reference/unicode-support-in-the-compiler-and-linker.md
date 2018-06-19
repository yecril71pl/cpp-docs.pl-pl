---
title: Obsługa standardu Unicode w kompilatorze i Konsolidatorze | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/15/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
dev_langs:
- C++
helpviewer_keywords:
- Unicode, Visual C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec0b84cd62f3fcca378ab55de16006925e685b37
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376195"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Obsługa formatu Unicode w kompilatorze i konsolidatorze

Większość narzędzi kompilacji Visual C++ obsługuje Unicode w danych wejściowych i wyjściowych.

## <a name="filenames"></a>Nazwy plików

Określona w wierszu polecenia lub w dyrektywy kompilatora nazw plików (takich jak `#include`) może zawierać znaków Unicode.

## <a name="source-code-files"></a>Pliki kodu źródłowego

Znaki Unicode są obsługiwane w identyfikatory, makra, literały ciągów i znakowe i komentarze.  Uniwersalne nazwy znaków są również obsługiwane.

Unicode można wprowadzić do pliku kodu źródłowego w następujących kodowań:

- UTF-16 little endian z lub bez znacznika kolejności bajtów (BOM)

- UTF-16 big endian z lub bez BOM

- UTF-8 z BOM

## <a name="output"></a>Dane wyjściowe

Podczas kompilacji kompilator generuje diagnostyczne w konsoli, UTF-16.  Znaki, które mogą być wyświetlane w konsoli są zależne od właściwości okna konsoli.  Dane wyjściowe kompilatora, przekierowywany do pliku jest bieżąca strona kodowa konsoli ANSI.

## <a name="linker-response-files-and-def-files"></a>Pliki odpowiedzi konsolidatora i. Pliki DEF

Pliki odpowiedzi i DEF, pliki mogą być albo UTF-16 BOM lub ANSI.

## <a name="asm-and-cod-dumps"></a>zrzuty .asm i .cod

zrzuty .asm i .cod są w formacie ANSI domyślnie w celu zapewnienia zgodności z MASM. Użyj [/FAu](../../build/reference/fa-fa-listing-file.md) do wyjściowego UTF-8. Należy pamiętać, że jeśli określisz **/FAS**, intermingled źródła tylko bezpośrednio wydruku i może wyglądać zniekształcony, na przykład jeśli kod źródłowy jest UTF-8 i nie określono **/FAsu**.

## <a name="see-also"></a>Zobacz także

[Kompilowanie kodu C/C++ w wierszu polecenia](../../build/building-on-the-command-line.md)