---
title: "Dane wyjściowe LINK | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: link
dev_langs: C++
helpviewer_keywords:
- mapfiles [C++]
- ILK files
- output files [C++], linker
- files [C++], LINK
- .ilk files
- LINK tool [C++], output
- import libraries [C++], creating
- executable files [C++], as linker output
- mapfiles [C++], LINK output
- linker [C++], output files
- DLLs [C++], as linker output
- LINK tool [C++], mapfile
ms.assetid: a98b557c-1947-447a-be1f-616fb45a9580
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d01f19f31f83324beab1e44efe181086d6432175
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="link-output"></a>Dane wyjściowe LINK
Dane wyjściowe Link zawiera pliki .exe, biblioteki DLL mapfiles i komunikatów.  
  
##  <a name="_core_output_files"></a>Pliki wyjściowe  
 Domyślny plik wyjściowy z łącza jest pliku .exe. Jeśli [/dll](../../build/reference/dll-build-a-dll.md) zostanie określona opcja, LINK tworzy plik dll. Można kontrolować, nazwa pliku wyjściowego z [nazwę pliku wyjściowego (/ OUT)](../../build/reference/out-output-file-name.md) opcji.  
  
 W trybie przyrostowe łącze tworzy plik .ilk do przechowywania informacji o stanie dla nowszej kompilacji przyrostowej programu. Aby uzyskać więcej informacji o plikach .ilk, zobacz [.ilk — pliki](../../build/reference/dot-ilk-files-as-linker-input.md). Aby uzyskać więcej informacji na temat konsolidowania przyrostowego zobacz [przyrostowo łącza (/ INCREMENTAL)](../../build/reference/incremental-link-incrementally.md) opcji.  
  
 Gdy łącze tworzy program, który zawiera eksportuje (zazwyczaj DLL), także program tworzy plik .lib, chyba że użyto pliku .exp w kompilacji. Można kontrolować, nazwa pliku biblioteki importu z [/IMPLIB](../../build/reference/implib-name-import-library.md) opcji.  
  
 Jeśli [Generowanie Mapfile (/ MAP)](../../build/reference/map-generate-mapfile.md) zostanie określona opcja, łącze tworzy plik mapowania.  
  
 Jeśli [Generuj informacje o debugowaniu (/ DEBUG)](../../build/reference/debug-generate-debug-info.md) zostanie określona opcja, łącze tworzy PDB zawierają informacje o debugowaniu dla programu.  
  
##  <a name="_core_other_output"></a>Inne dane wyjściowe  
 Podczas wpisywania `link` bez żadnych innych danych wiersza polecenia, LINK wyświetla instrukcji użycia, która zawiera podsumowanie jej opcji.  
  
 Wyświetla komunikat o prawach autorskich i wersji i zwraca plik poleceń do wprowadzania, chyba że łącze [Pomijaj transparent startowy (/ NOLOGO)](../../build/reference/nologo-suppress-startup-banner-linker.md) jest używana opcja.  
  
 Można użyć [Drukuj komunikaty o postępie (/ VERBOSE)](../../build/reference/verbose-print-progress-messages.md) opcję, aby wyświetlić dodatkowe informacje o kompilacji.  
  
 ŁĄCZE wystawia błędu i ostrzeżenia wiadomości w postaci LNK*nnnn*. Ten błąd prefiks i zakres numerów są również używane przez LIB, DUMPBIN i polecenia EDITBIN.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)