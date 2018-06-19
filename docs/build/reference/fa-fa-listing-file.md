---
title: / FA, /Fa (umieszczanie pliku) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
dev_langs:
- C++
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1840d2f2ff7d968fdcc19e2013a89af9cec32d24
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378954"
---
# <a name="fa-fa-listing-file"></a>/FA, /Fa (Umieszczanie pliku na liście)
Tworzy listę plik zawierający kod asemblera.  
  
## <a name="syntax"></a>Składnia  
  
> **/FA**[**c**\][**s**\][**u**]  
> **/Fa**_nazwy ścieżki_  
  
## <a name="remarks"></a>Uwagi  
`/FA` — Opcja kompilatora zostanie wygenerowany plik listy asemblera dla każdej jednostki tłumaczenia w kompilacji, które zazwyczaj odpowiada plik źródłowy języka C lub C++. Domyślnie tylko asemblera znajduje się w pliku listy, które są kodowane jako ANSI. Opcjonalny `c`, `s`, i `u` argumenty `/FA` kontroli komputera Określa, czy kod lub kodu źródłowego są dane wyjściowe wraz z asemblera wyświetlania i czy listę został zakodowany jako UTF-8.  
  
Domyślnie każdy plik pobiera taką samą nazwę podstawową jak plik źródłowy i ma rozszerzenie .asm. Jeśli kod maszynowy znajduje się za pomocą `c` opcji pliku listy ma rozszerzenie .cod. Można zmienić nazwę i rozszerzenie pliku listy i katalog, w którym jest tworzona przy użyciu `/Fa` opcji.  

### <a name="fa-arguments"></a>/FA argumentów  
brak  
Tylko język asemblera znajduje się na liście.  
  
`c`  
Opcjonalna. Zawiera kod maszynowy na liście.  
  
`s`  
Opcjonalna. Zawiera kod źródłowy na liście.  
  
`u` Opcjonalne. Koduje plik listy w formacie UTF-8 i zawiera znacznika kolejności bajtów. Domyślnie plik jest zakodowany jako ANSI. Użyj `u` do utworzenia pliku listy, który jest wyświetlane prawidłowo w każdym systemie, lub jeśli używasz Unicode kod plików źródłowych jako dane wejściowe do kompilatora.  
  
Jeśli oba `s` i `u` są określone, a jeśli plik kod źródłowy używa kodowania Unicode, inne niż UTF-8, a następnie wierszy kodu w pliku .asm mogą nie wyświetlać się poprawnie.  
  
### <a name="fa-argument"></a>/Fa argumentu  
brak  
Jeden *źródła*.asm plik jest tworzony dla każdego pliku kodu źródłowego w kompilacji.  
  
*Nazwa pliku* plik listy o nazwie *filename*.asm znajduje się w bieżącym katalogu. To jest prawidłowe tylko podczas kompilowania pliku kodu jednego źródła.  
  
*filename.Extension*  
Plik listy o nazwie *filename.extension* znajduje się w bieżącym katalogu. To jest prawidłowe tylko podczas kompilowania pliku kodu jednego źródła.  
  
*Katalog*\  
Jeden *source_file*.asm pliku jest tworzony i umieszczane w określonym *katalogu* dla każdego pliku kodu źródłowego w kompilacji. Należy pamiętać, wymagane końcowy ukośnik odwrotny. Dozwolone są tylko ścieżki na bieżącym dysku.  
  
*katalog*\\*filename* plik listy o nazwie *filename*.asm znajduje się w określonym *katalogu*. To jest prawidłowe tylko podczas kompilowania pliku kodu jednego źródła.  
  
*katalog*\\*filename.extension*  
Plik listy o nazwie *filename.extension* znajduje się w określonym *katalogu*. To jest prawidłowe tylko podczas kompilowania pliku kodu jednego źródła.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Otwórz **C/C++** i wybierz polecenie **pliki wyjściowe** strony właściwości.  
  
3.  Modyfikowanie **wynik zestawów** właściwości można ustawić `/FAc` i `/FAs` opcje asemblera, maszyna i kod źródłowy. Modyfikowanie **Użyj Unicode do asemblera wyświetlania** właściwości można ustawić `/FAu` opcji dla danych wyjściowych ANSI lub UTF-8. Modyfikowanie **lokalizacja listy ASM** można ustawić `/Fa` opcję wyświetlania list nazwę pliku i lokalizację.  
  
Należy pamiętać, że ustawienie zarówno **wynik zestawów** i **Użyj Unicode do asemblera wyświetlania** właściwości może spowodować [wiersza polecenia ostrzeżenie D9025](../../error-messages/tool-errors/command-line-warning-d9025.md). Aby połączyć tych opcji w środowisku IDE, należy użyć **dodatkowe opcje** w **wiersza polecenia** właściwości strony zamiast tego.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> lub <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>. Aby określić `/FAu`, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="example"></a>Przykład  
Następujące polecenie w wierszu tworzy połączonego źródła i przykładowy kod komputera o nazwie HELLO.cod:  
  
```  
CL /FAcs HELLO.CPP  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)