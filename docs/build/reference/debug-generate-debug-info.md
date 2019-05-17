---
title: /DEBUG (Generowanie informacji o debugowaniu)
ms.date: 05/16/2019
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
helpviewer_keywords:
- DEBUG linker option
- /DEBUG linker option
- -DEBUG linker option
- PDB files
- debugging [C++], debug information files
- generate debug info linker option
- pdb files, generating debug info
- .pdb files, generating debug info
- debugging [C++], linker option
- program databases [C++]
ms.assetid: 1af389ae-3f8b-4d76-a087-1cdf861e9103
ms.openlocfilehash: 2ec466a6356ace437d32eb517bf2da291938f5db
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837144"
---
# <a name="debug-generate-debug-info"></a>/DEBUG (Generowanie informacji o debugowaniu)

```
/DEBUG[:{FASTLINK|FULL|NONE}]
```

## <a name="remarks"></a>Uwagi

**/DEBUG** opcji Tworzenie informacji debugowania dla pliku wykonywalnego.

Program łączący umieszcza informacje debugowania z plikiem bazy danych (PDB) programu. Podczas kolejnych kompilacjach program powoduje zaktualizowanie pliku PDB.

Plik wykonywalny (plik .exe lub DLL) utworzone na potrzeby debugowania zawiera nazwę i ścieżkę odpowiedniego pliku PDB. Debuger odczytuje nazwę osadzonego i używa pliku PDB podczas debugowania programu. Konsolidator używa podstawowej nazwy programu i rozszerzenia .pdb nazwę bazy danych programu i osadza ścieżki, w której został utworzony. Aby zastąpić to ustawienie domyślne, należy ustawić [/PDB](pdb-use-program-database.md) i określ inną nazwę pliku.

**Fastlink** opcja jest dostępna w programie Visual Studio 2017 i nowszym. Tę opcję, pozostawia informacje dotyczące symboli prywatnych w produktach poszczególnych kompilacji używany do tworzenia pliku wykonywalnego. Generuje on ograniczony pliku PDB, będącej indeksem na informacje o debugowaniu w plików obiektów i bibliotek, używany do utworzenia pliku wykonywalnego, zamiast tworzenia pełnej kopii. Tej opcji można połączyć się z dwóch do czterech razy tak szybko, jak Pełna generowania plików PDB i jest zalecana w przypadku lokalnego debugowania i znajdują się dostępne produkty kompilacji. Ta ograniczona PDB nie można używać do debugowania po produkty wymagane kompilacji nie są dostępne, takich jak podczas wdrażania pliku wykonywalnego na innym komputerze. W wierszu polecenia dla deweloperów można użyć narzędzia mspdbcmf.exe wygenerować pełny plik PDB z tej ograniczonej pliku PDB. W programie Visual Studio Użyj elementów menu Projekt lub kompilacji do generowania pełnego pliku PDB, aby utworzyć pełny plik PDB dla projektu lub rozwiązania.

**/Debug: full** opcja przenosi informacje o wszystkich symbolach prywatnych z kompilacji poszczególnych produktów (plików obiektów i bibliotek) do pojedynczego pliku PDB i mogą być częścią najbardziej czasochłonne łącze. Jednak pełny plik PDB może służyć do debugowania pliku wykonywalnego, gdy nie inne produkty kompilacji są dostępne, takich jak podczas wdrażania pliku wykonywalnego.

**/DEBUG: Brak** opcji nie generuje pliku PDB.

Po określeniu **/DEBUG** bez żadnych dodatkowych opcji Domyślnie konsolidator **/Debug: full** dla wiersza polecenia i kompilacji pliku reguł programu make dla wersji kompilacji w środowisku IDE programu Visual Studio i zarówno debug i release kompilacje w programie Visual Studio 2015 i starsze wersje. Począwszy od programu Visual Studio 2017, system kompilacji w środowisku IDE domyślnie **fastlink** po określeniu **/DEBUG** opcji kompilacji debugowania. Aby zachować zgodność z poprzednimi wersjami nie zostały zmienione inne wartości domyślne.

Kompilator [zgodne z C7](z7-zi-zi-debug-information-format.md) (/ Z7) opcja powoduje, że kompilator, aby pozostawić informacje o debugowaniu w plikach .obj. Można również użyć [bazy danych programu](z7-zi-zi-debug-information-format.md) do przechowywania informacji o debugowaniu w pliku PDB dla pliku .obj — opcja kompilatora (/Zi). Konsolidator szuka pliku PDB obiektu najpierw ścieżka bezwzględna zapisywane w pliku .obj, a następnie w katalogu, który zawiera plik .obj. Nie można określić nazwę pliku PDB lub lokalizację, aby konsolidator obiektu.

[/ INCREMENTAL](incremental-link-incrementally.md) jest implikowane, jeśli nie określono opcji/Debug.

/ DEBUG zmian wartości domyślne dla [/OPT](opt-optimizations.md) możliwość z REF z Zapora połączenia internetowego i NOREF NOICF, dzięki czemu w przypadku oryginalnej wartości domyślne, należy jawnie należy określić/OPT: REF lub/OPT: ICF.

Nie jest możliwe utworzenie .exe lub .dll, który zawiera informacje o debugowaniu. Debugowanie informacje są zawsze umieszczane w pliku PDB lub .obj.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **debugowanie** stronę właściwości.

1. Modyfikowanie **Generuj informacje o debugowaniu** właściwością pozwalającą włączyć Generowanie pliku PDB. Dzięki temu fastlink domyślnie w programie Visual Studio 2017 i nowszych wersjach.

1. Modyfikowanie **Generuj pełny plik bazy danych programu** właściwością pozwalającą włączyć/Debug: Full, aby uzyskać pełne generowanie pliku PDB dla każdej kompilacji przyrostowej.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
