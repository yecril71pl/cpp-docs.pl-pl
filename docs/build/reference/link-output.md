---
title: Dane wyjściowe LINK
ms.date: 11/04/2016
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
ms.openlocfilehash: 253f88ed50b9f064edf976277a4618e4f101ec7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331793"
---
# <a name="link-output"></a>Dane wyjściowe LINK

Dane wyjściowe łącza obejmują pliki exe, biblioteki DLL, pliki map i wiadomości.

## <a name="output-files"></a><a name="_core_output_files"></a>Pliki wyjściowe

Domyślnym plikiem wyjściowym z LINK jest plik exe. Jeśli określono opcję [/DLL,](dll-build-a-dll.md) LINK tworzy plik dll. Nazwę pliku wyjściowego można kontrolować za pomocą opcji [Nazwa pliku wyjściowego (/OUT).](out-output-file-name.md)

W trybie przyrostowym link tworzy plik .ilk do przechowywania informacji o stanie dla późniejszych przyrostowych kompilacji programu. Aby uzyskać szczegółowe informacje o plikach .ilk, zobacz [.ilk Pliki](dot-ilk-files-as-linker-input.md). Aby uzyskać więcej informacji na temat łączenia przyrostowego, zobacz opcję [Łączenie przyrostowe (/PRZYROSTOWE).](incremental-link-incrementally.md)

Gdy LINK tworzy program, który zawiera eksport (zwykle DLL), tworzy również plik lib, chyba że plik exp został użyty w kompilacji. Nazwę pliku biblioteki importu można kontrolować za pomocą opcji [/IMPLIB.](implib-name-import-library.md)

Jeśli określono opcję [Generuj plik map (/MAP),](map-generate-mapfile.md) funkcja LINK utworzy plik mapy.

Jeśli określono opcję [Generuj informacje o debugowaniu (/DEBUG),](debug-generate-debug-info.md) funkcja LINK tworzy bazę danych PDB zawierającą informacje debugowania dla programu.

## <a name="other-output"></a><a name="_core_other_output"></a>Inne dane wyjściowe

Po wpisaniu `link` bez innych danych wejściowych wiersza polecenia, LINK wyświetla instrukcję użycia, która podsumowuje jego opcje.

LINK wyświetla komunikat o prawach autorskich i wersji oraz echa wejścia pliku polecenia, chyba że używana jest opcja [Pomiń baner startowy (/NOLOGO).](nologo-suppress-startup-banner-linker.md)

Można użyć opcji [Drukuj komunikaty postępu (/VERBOSE),](verbose-print-progress-messages.md) aby wyświetlić dodatkowe szczegóły dotyczące kompilacji.

LINK wydaje komunikaty o błędach i ostrzeżeniach w formie LNK*nnnn*. Ten prefiks błędu i zakres liczb są również używane przez LIB, DUMPBIN i EDITBIN.

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
