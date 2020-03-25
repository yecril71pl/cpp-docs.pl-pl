---
title: Obsługa formatu Unicode w kompilatorze i konsolidatorze
ms.date: 12/15/2017
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
helpviewer_keywords:
- Unicode, Visual C++
ms.openlocfilehash: 420b01263320cf86df3f99da4523cc2b8bb4d4b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168840"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Obsługa formatu Unicode w kompilatorze i konsolidatorze

Większość narzędzi C++ do tworzenia wizualizacji obsługuje dane wejściowe i wyjściowe w formacie Unicode.

## <a name="filenames"></a>Nazwy plików

Nazwy plików określone w wierszu polecenia lub w dyrektywach kompilatora (takie jak `#include`) mogą zawierać znaki Unicode.

## <a name="source-code-files"></a>Pliki kodu źródłowego

Znaki Unicode są obsługiwane w identyfikatorach, makrach, literałach ciągów i znakach oraz w komentarzach.  Obsługiwane są również uniwersalne nazwy znaków.

Unicode może być wejściowy do pliku kodu źródłowego w następujących kodowaniu:

- UTF-16 little endian z lub bez znacznika kolejności bajtów (BOM)

- Big endian UTF-16 z lub bez BOM

- UTF-8 z BOM

## <a name="output"></a>Dane wyjściowe

Podczas kompilacji kompilator wyprowadza diagnostykę do konsoli w UTF-16.  Znaki, które mogą być wyświetlane w konsoli programu, zależą od właściwości okna konsoli.  Wyjście kompilatora przekierowane do pliku znajduje się w bieżącej stronie kodowej konsoli ANSI.

## <a name="linker-response-files-and-def-files"></a>Pliki odpowiedzi konsolidatora i. Pliki DEF

Pliki odpowiedzi i DEF plików mogą być w formacie UTF-16 z BOM lub ANSI.

## <a name="asm-and-cod-dumps"></a>zrzuty. ASM i. COD

zrzuty. ASM i. COD są domyślnie w standardzie ANSI w celu zapewnienia zgodności z MASM. Użyj [/FAU](fa-fa-listing-file.md) do wyprowadzania UTF-8. Należy pamiętać, że w przypadku określenia **/FAS**Źródło wymieszaniu zostanie bezpośrednio wydrukowane i może być zniekształcone, na przykład jeśli kod źródłowy to UTF-8 i nie określono **/FAsu**.

## <a name="see-also"></a>Zobacz też

[Używanie zestawu narzędzi MSVC z poziomu wiersza polecenia](../building-on-the-command-line.md)
