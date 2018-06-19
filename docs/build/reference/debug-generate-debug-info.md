---
title: -DEBUG (generowanie informacji o debugowaniu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f93c47a0f96cf0b75b453bcea97212d4ab2fd6d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375730"
---
# <a name="debug-generate-debug-info"></a>/DEBUG (Generowanie informacji o debugowaniu)
```  
/DEBUG[:{FASTLINK|FULL|NONE}]  
```  
  
## <a name="remarks"></a>Uwagi  

**/DEBUG** opcja tworzy informacji debugowania dla pliku wykonywalnego.    
  
Konsolidator umieszcza informacje o debugowaniu plik programu (PDB) bazy danych. Podczas kolejnych kompilacjach program aktualizuje pliku PDB.  
  
Plik wykonywalny (pliku .exe lub DLL), utworzone dla debugowania zawiera nazwę i ścieżkę odpowiedniego pliku PDB. Debuger odczytuje nazwę osadzonego i używa pliku PDB podczas debugowania programu. Konsolidator używa podstawowej nazwy programu i rozszerzenia .pdb nazwę bazy danych programu i osadza ścieżki, w której został utworzony. Aby zastąpić to ustawienie domyślne, należy ustawić [/PDB](../../build/reference/pdb-use-program-database.md) i określ inną nazwę pliku.  

**/DEBUG:FASTLINK** opcji pozostawia informacje dotyczące symboli prywatnych w produktach poszczególnych kompilacji używany do tworzenia pliku wykonywalnego. Generuje on ograniczony pliku PDB indeksujący informacje debugowania w plikach obiektu i bibliotek używany do tworzenia pliku wykonywalnego zamiast tworzenia pełnej kopii. Ta opcja może połączyć się z dwóch do czterech razy szybciej niż pełne generowania plików PDB i jest zalecana w przypadku debugowania lokalnie i dostępnych produktów kompilacji. Ta ograniczona PDB nie można używać do debugowania podczas kompilacji wymagane produkty nie są dostępne, np. Jeśli plik wykonywalny jest wdrażana na innym komputerze. W wierszu polecenia dewelopera narzędzie mspdbcmf.exe służy do generowania pełnego pliku PDB z tej ograniczonej PDB. W programie Visual Studio Użyj elementów menu Projekt lub kompilacji podczas generowania pełnego pliku PDB, aby utworzyć pełny plik PDB dla projektu lub rozwiązania.  
  
**/DEBUG:FULL** opcja przenosi wszystkie informacje dotyczące symboli prywatnych z produktów poszczególnych kompilacji (pliki obiektu i bibliotek) do pojedynczego pliku PDB i może być czasochłonne najbardziej częścią łącza. Jednak pełny plik PDB można debugować plik wykonywalny, jeśli żadne inne produkty kompilacji nie są dostępne, takich jak podczas wdrażania pliku wykonywalnego.  
  
**/DEBUG: Brak** opcji nie generuje pliku PDB.  
  
Po określeniu **/DEBUG** bez żadnych dodatkowych opcji Domyślnie konsolidator **/DEBUG:FULL** dla wiersza polecenia i kompilacji pliku reguł programu make dla wersji kompilacji w programie Visual Studio IDE i debugowania i wydania kompilacje w Visual Studio 2015 i wcześniejszych wersjach. Począwszy od programu Visual Studio 2017 system kompilacji w środowisku IDE domyślnie **/DEBUG:FASTLINK** po określeniu **/DEBUG** opcji dla kompilacje debugowania. Innych wartości domyślnych zostały zmienione w celu zachowania zgodności z poprzednimi wersjami.  
  
Kompilator [C7 zgodne](../../build/reference/z7-zi-zi-debug-information-format.md) (/ Z7) opcja powoduje, że kompilator, aby pozostawić informacje debugowania w plikach .obj. Można również użyć [bazy danych programu](../../build/reference/z7-zi-zi-debug-information-format.md) do przechowywania informacji o debugowaniu w pliku PDB dla plików .obj — opcja kompilatora (/ zi). Konsolidator szuka pliku PDB obiektu najpierw ścieżka bezwzględna zapisywane w pliku .obj, a następnie w katalogu, który zawiera plik .obj. Nie można określić nazwę pliku PDB lub lokalizację, aby konsolidator obiektu.  
  
[/ INCREMENTAL](../../build/reference/incremental-link-incrementally.md) technicznego, gdy określono opcję/Debug.  
  
/ DEBUG zmienia ustawienia domyślne dla [/OPT](../../build/reference/opt-optimizations.md) możliwość z REF z Zapora połączenia internetowego i NOREF NOICF, tak aby oryginalnej wartości domyślne, należy jawnie określić /OPT:REF lub/OPT: ICF.  
  
Nie jest możliwe utworzenie .exe lub .dll, który zawiera informacje o debugowaniu. Debugowanie informacje są zawsze umieszczane w pliku obj lub .pdb.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **debugowanie** strony właściwości.  
  
4.  Modyfikowanie **Generuj informacje o debugowaniu** właściwości, aby włączyć generowania plików PDB. Dzięki temu /DEBUG:FASTLINK domyślnie w programie Visual Studio 2017 r.  
  
4.  Modyfikowanie **Generuj pełny plik bazy danych programu** właściwości do włączenia /DEBUG:FULL dla pełnej generowania plików PDB dla każdej kompilacji przyrostowej.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)
