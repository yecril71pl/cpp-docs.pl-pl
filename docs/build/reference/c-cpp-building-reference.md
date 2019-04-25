---
title: Odwołanie kompilacji C/C++ — Visual Studio
description: Zawartość informacyjna dotycząca języka C/C++ systemu projektu i narzędzia w programie Visual Studio do kompilacji.
ms.date: 12/10/2018
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
ms.openlocfilehash: 4c3f7aa598a9c43af04c148ed0d4b3f555566ec7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294762"
---
# <a name="cc-building-reference"></a>Odwołanie kompilacji C/C++

Visual C++ zapewnia dwa sposoby kompilowanie programu C/C++. Najłatwiejszym (i najbardziej powszechnym) sposobem jest [kompilacji w środowisku IDE programu Visual Studio](../creating-and-managing-visual-cpp-projects.md). Drugi sposób to [kompilacji z wiersza polecenia przy użyciu narzędzia wiersza polecenia](../building-on-the-command-line.md). W obu przypadkach należy można tworzyć i edytować plików źródłowych przy użyciu programu Visual Studio lub dowolnego edytora w innych firm.

## <a name="in-this-section"></a>W tej sekcji

[Dokumentacja aparatu MSBuild dla projektów w języku C++](msbuild-visual-cpp-overview.md)

[Dokumentacja kompilatora MSVC](compiling-a-c-cpp-program.md)<br/>
W tym artykule opisano kompilatora MSVC, który tworzy plik obiektu zawierającego kod maszynowy, dyrektywy konsolidatora, sekcje, odwołania zewnętrzne i nazwy funkcji/danych.

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
W tym artykule opisano konsolidatora, która łączy kod z plikami obiekt utworzony przez kompilator i statycznie łączonych bibliotek, jest rozpoznawana jako odwołania do nazwy i tworzy plik wykonywalny.

[Obsługa formatu Unicode w kompilatorze i konsolidatorze](unicode-support-in-the-compiler-and-linker.md)

[MSVC dodatkowe narzędzia do kompilacji](c-cpp-build-tools.md)<br/>
Dodatkowe narzędzia wiersza polecenia dla języka C++.

[Błędy kompilacji C/C++](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)<br/>
Wprowadza sekcję błędy kompilacji w tabeli treści.

## <a name="related-sections"></a>Sekcje pokrewne

[Dokumentacja preprocesora języka C/C++](../../preprocessor/c-cpp-preprocessor-reference.md)<br/>
W tym artykule omówiono preprocesora, który przygotowuje pliki źródłowe dla kompilatora zamieniane makra, operatorów i dyrektywy.

[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](../understanding-custom-build-steps-and-build-events.md)<br/>
W tym artykule omówiono, dostosowywanie procesu kompilacji.

[Kompilowanie programu C/C++](../projects-and-build-systems-cpp.md)<br/>
Zawiera łącza do tematów opisujących, tworzenie programu z wiersza polecenia lub zintegrowanego środowiska projektowego programu Visual Studio.

[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
W tym artykule opisano ustawienia Opcje kompilatora w środowisku programistycznym lub w wierszu polecenia.

[Opcje kompilatora MSVC](compiler-options.md)<br/>
Zawiera łącza do tematów omawiających używanie opcji kompilatora.

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
W tym artykule opisano opcje konsolidatora ustawienie wewnątrz lub na zewnątrz zintegrowanego środowiska programistycznego.

[Opcje konsolidatora MSVC](linker-options.md)<br/>
Zawiera łącza do tematów omawiających używanie opcji konsolidatora.

[BSCMAKE — dokumentacja](bscmake-reference.md)<br/>
W tym artykule opisano narzędzie konserwacji przeglądarki Microsoft informacji (BSCMAKE. Z rozszerzeniem EXE), które kompilacje pliku informacyjnego przeglądarki (.bsc) z .sbr pliki tworzone podczas kompilacji.

[LIB — dokumentacja](lib-reference.md)<br/>
W tym artykule opisano menedżera biblioteki Microsoft (LIB.exe), który tworzy i którymi zarządza Biblioteka plików obiektów Common Object File Format (COFF).

[EDITBIN — dokumentacja](editbin-reference.md)<br/>
W tym artykule opisano edytora pliku binarnego Microsoft COFF (EDITBIN. Z rozszerzeniem EXE), który modyfikuje pliki binarne Common Object File Format (COFF).

[DUMPBIN — dokumentacja](dumpbin-reference.md)<br/>
W tym artykule opisano Microsoft COFF plik binarny zrzutu (DUMPBIN. Z rozszerzeniem EXE), który wyświetla informacje dotyczące plików binarnych Common Object File Format (COFF).

[NMAKE — dokumentacja](nmake-reference.md)<br/>
W tym artykule opisano narzędzie do konserwacji programów firmy Microsoft (NMAKE. Z rozszerzeniem EXE), czyli narzędzie, które kompilacje projektów oparte na polecenia zawarte w pliku opisu.
