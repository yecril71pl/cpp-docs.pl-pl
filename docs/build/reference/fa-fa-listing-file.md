---
title: /FA, /Fa (Umieszczanie pliku na liście)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
ms.openlocfilehash: b78704ea12365d9e10222d75c6807517f7cdb893
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292838"
---
# <a name="fa-fa-listing-file"></a>/FA, /Fa (Umieszczanie pliku na liście)

Tworzy plik listingu z kodem asemblera.

## <a name="syntax"></a>Składnia

> **/FA**[**c**\][**s**\][**u**] **/Fa**_nazwy ścieżki_

## <a name="remarks"></a>Uwagi

**/FA** — opcja kompilatora generuje plik listingu asemblera dla każdej jednostki translacji w kompilacji i zazwyczaj odpowiada plik źródłowy C lub C++. Domyślnie tylko asemblera znajduje się w pliku listy, który jest zakodowanymi w formacie ANSI. Opcjonalny **c**, **s**, i **u** argumenty **/FA** kontroli tego, czy maszyny kodu lub kodu źródłowego są dane wyjściowe wraz z asemblera Wyświetlanie listy, i czy listy jest zakodowany w formacie UTF-8.

Domyślnie każdy plik listingu pobiera tej samej nazwie podstawowej co plik źródłowy i ma rozszerzenie .asm. Gdy kod maszynowy znajduje się za pomocą **c** opcji plik listingu z rozszerzeniem .cod. Możesz zmienić nazwę i rozszerzenie pliku listy i katalog, w której jest tworzona przy użyciu **/Fa** opcji.

### <a name="fa-arguments"></a>/FA argumentów

brak<br/>
Tylko język asemblera znajduje się na liście.

**c**<br/>
Opcjonalna. Zawiera kod maszynowy na liście.

**s**<br/>
Opcjonalna. Zawiera kod źródłowy, na liście.

**u**<br/>
Opcjonalna. Koduje plik listy w formacie UTF-8 i zawiera znacznika kolejności bajtów. Domyślnie plik jest zakodowane jako ANSI. Użyj `u` do Utwórz plik listingu, w którym są wyświetlane poprawnie w dowolnym systemie lub jeśli używasz Unicode pliki kodów źródłowych jako dane wejściowe do kompilatora.

Jeśli oba **s** i **u** są określone, a jeśli plik kodu źródłowego przy użyciu kodowania Unicode, inne niż UTF-8, a następnie wierszy kodu w pliku .asm mogą nie wyświetlać się poprawnie.

### <a name="fa-argument"></a>/Fa argumentu

brak<br/>
Jeden *źródła*sam plik jest tworzony dla każdego pliku kodu źródłowego w kompilacji.

*Nazwa pliku*<br/>
Plik listingu o nazwie *filename*.asm znajduje się w bieżącym katalogu. To jest prawidłowe tylko podczas kompilowania pliku z kodem jedno źródło.

*filename.extension*<br/>
Plik listingu o nazwie *filename.extension* znajduje się w bieżącym katalogu. To jest prawidłowe tylko podczas kompilowania pliku z kodem jedno źródło.

*directory*__\\__<br/>
Jeden *$source_file*plików .asm jest tworzone i umieszczane w określonym *katalogu* dla każdego pliku kodu źródłowego w kompilacji. Należy pamiętać, wymagane ukośnik odwrotny na końcu. Dozwolone są tylko ścieżki na bieżącym dysku.

*katalog*__\\__*nazwy pliku*<br/>
Plik listingu o nazwie *filename*.asm znajduje się w określonym *katalogu*. To jest prawidłowe tylko podczas kompilowania pliku z kodem jedno źródło.

*directory*__\\__*filename.extension*<br/>
Plik listingu o nazwie *filename.extension* znajduje się w określonym *katalogu*. To jest prawidłowe tylko podczas kompilowania pliku z kodem jedno źródło.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **pliki wyjściowe** stronę właściwości.

1. Modyfikowanie **produkt wyjściowy asemblera** właściwość umożliwiająca ustawienie **/FAC** i **/FAS** opcje asemblera, maszyna i kod źródłowy. Modyfikowanie **Użyj Unicode dla asemblera ofercie** właściwość umożliwiająca ustawienie **/fau** opcji ANSI lub UTF-8 danych wyjściowych. Modyfikowanie **lokalizacja listy ASM** można ustawić **/Fa** opcji do wyświetlania listy nazwę i lokalizację pliku.

Należy pamiętać, że ustawienie oba **produkt wyjściowy asemblera** i **Użyj Unicode dla asemblera ofercie** właściwości może spowodować, że [wiersza polecenia ostrzeżenie d9025 dla](../../error-messages/tool-errors/command-line-warning-d9025.md). Aby połączyć tych opcji w środowisku IDE, należy użyć **dodatkowe opcje** pole **wiersza polecenia** zamiast stronie właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> lub <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>. Aby określić **/fau**, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Przykład

Następujące polecenie w wierszu tworzy połączone źródło i kod maszynowy listę o nazwie HELLO.cod:

```cmd
CL /FAcs HELLO.CPP
```

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)
