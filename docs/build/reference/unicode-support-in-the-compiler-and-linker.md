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
ms.openlocfilehash: 71458ab345670c0a5715576a7da80c4e6ff2955b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807515"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Obsługa formatu Unicode w kompilatorze i konsolidatorze

Większość narzędzi kompilacji Visual C++ obsługuje Unicode w danych wejściowych i wyjściowych.

## <a name="filenames"></a>Nazwy plików

Nazwy plików określone w wierszu polecenia lub w dyrektywach kompilatora (takich jak `#include`) może zawierać znaków Unicode.

## <a name="source-code-files"></a>Pliki kodu źródłowego

Znaki Unicode są obsługiwane w identyfikatorach, makrach, literałach ciągów i znakowe oraz w komentarzach.  Uniwersalne nazwy znaków są również obsługiwane.

Unicode można wprowadzić do pliku kodu źródłowego w formie następującego kodowania:

- Little endian UTF-16 z lub bez znacznika kolejności bajtów (BOM)

- Big endian UTF-16 z lub bez BOM

- UTF-8 z BOM

## <a name="output"></a>Dane wyjściowe

Podczas kompilacji kompilator wyprowadza diagnostykę do konsoli w UTF-16.  Znaki, które mogą być wyświetlane w konsoli są zależne od właściwości okna konsoli.  Dane wyjściowe kompilatora przekierowane do pliku jest bieżąca strona kodowa konsoli ANSI.

## <a name="linker-response-files-and-def-files"></a>Pliki odpowiedzi konsolidatora i. Pliki DEF

Pliki odpowiedzi i pliki DEF mogą być UTF-16 z BOM lub ANSI.

## <a name="asm-and-cod-dumps"></a>zrzuty plików .asm i .cod

zrzuty plików .asm i .cod są w formacie ANSI, domyślnie dla zapewnienia zgodności z MASM. Użyj [/fau](fa-fa-listing-file.md) do wyprowadzenia UTF-8. Należy pamiętać, że jeśli określisz **/FAS**, zmieszane źródło tylko zostanie zostanie wydrukowane bezpośrednio i może wyglądać na zniekształcone, na przykład jeśli kod źródłowy jest UTF-8, a nie określił **/FAsu**.

## <a name="see-also"></a>Zobacz także

[Możesz używać zestawu narzędzi MSVC z wiersza polecenia](../building-on-the-command-line.md)