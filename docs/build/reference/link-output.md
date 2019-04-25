---
title: Dane wyjściowe LINK
ms.date: 11/04/2016
f1_keywords:
- link
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
ms.openlocfilehash: 183f83501d930188032ec4209623ef7cf1a30efa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269179"
---
# <a name="link-output"></a>Dane wyjściowe LINK

Dane wyjściowe Link zawiera pliki .exe, biblioteki dll, mapfile i komunikatów.

##  <a name="_core_output_files"></a> Pliki wyjściowe

Domyślny plik wyjściowy z LINKU jest plik .exe. Jeśli [/dll](dll-build-a-dll.md) opcja zostanie określona, LINK tworzy plik dll. Można kontrolować nazwę pliku wyjściowego z [nazwę pliku wyjściowego (/ OUT)](out-output-file-name.md) opcji.

W trybie przyrostowym LINK tworzy plik .ilk do przechowywania informacji o stanie na później kompilacje przyrostowe programu. Aby uzyskać szczegółowe informacje o plikach .ilk, zobacz [.ilk — pliki](dot-ilk-files-as-linker-input.md). Aby uzyskać więcej informacji na temat przyrostowe konsolidowanie Zobacz [łącza przyrostowe (/ INCREMENTAL)](incremental-link-incrementally.md) opcji.

Gdy LINK tworzy program, który zawiera eksportuje (zazwyczaj DLL), ale sprzyja wytwarzaniu plik .lib, o ile nie użyto pliku .exp w kompilacji. Możesz kontrolować, nazwa pliku biblioteki importu za pomocą [/IMPLIB](implib-name-import-library.md) opcji.

Jeśli [Generowanie Mapfile (/ MAP)](map-generate-mapfile.md) opcja zostanie określona, LINK tworzy plik mapy.

Jeśli [Generuj informacje o debugowaniu (/ DEBUG)](debug-generate-debug-info.md) opcja zostanie określona, LINK tworzy PDB w celu uwzględnienia informacji o debugowaniu dla programu.

##  <a name="_core_other_output"></a> Inne dane wyjściowe

Podczas wpisywania `link` bez żadnych innych wiersza polecenia danych wejściowych, LINK będzie wyświetlać instrukcję użycia, który podsumowuje opcje.

LINK wyświetla komunikat o prawach autorskich i wersji i funkcją pliku poleceń do wprowadzania, chyba że [Pomijaj transparent startowy (/ NOLOGO)](nologo-suppress-startup-banner-linker.md) jest używana opcja.

Możesz użyć [Drukuj komunikaty o postępie (/ VERBOSE)](verbose-print-progress-messages.md) opcję, aby wyświetlić dodatkowe szczegóły dotyczące kompilacji.

ŁĄCZE wysyła komunikaty błędu i ostrzeżenia w postaci LNK*nnnn*. Ten prefiks błąd i zakres liczb są również używane przez LIB, DUMPBIN i polecenia EDITBIN.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
