---
title: Odwołanie kompilacji C/C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5935c0642ba0cd69992c68c521d284c3e8733ce4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390035"
---
# <a name="cc-building-reference"></a>Odwołanie kompilacji C/C++

Visual C++ zapewnia dwa sposoby kompilowanie programu C/C++. Najłatwiejszym (i najbardziej powszechnym) sposobem jest [kompilacji w środowisku deweloperskim Visual C++](../../ide/building-cpp-projects-in-visual-studio.md). Drugi sposób to [kompilacji z wiersza polecenia przy użyciu narzędzia wiersza polecenia](../../build/building-on-the-command-line.md). W obu przypadkach można utworzyć plików źródłowych, za pomocą edytora źródła Visual C++ lub ulubionego edytora w innych firm.

Jeśli program używa pliku reguł programu make, a nie plik .vcxproj, nadal tworzyć go w środowisku programistycznym jako [projektu zewnętrznego](../../ide/building-external-projects.md).

## <a name="in-this-section"></a>W tej sekcji

[Kompilowanie programu C/C++](../../build/reference/compiling-a-c-cpp-program.md)<br/>
W tym artykule opisano, kompilator tworzy plik obiektu zawierającego kod maszynowy, dyrektywy konsolidatora, sekcje, odwołania zewnętrzne i nazwy funkcji/danych.

[Konsolidacja](../../build/reference/linking.md)<br/>
W tym artykule opisano konsolidatora, która łączy kod z plikami obiekt utworzony przez kompilator i statycznie łączonych bibliotek, jest rozpoznawana jako odwołania do nazwy i tworzy plik wykonywalny.

[Kompilacje wydania](../../build/reference/release-builds.md)<br/>
Przedstawia informacje na kiedy i dlaczego chcesz zmienić z poziomu pozycji Debuguj kompilacja — przejście do kompilacji wydania, a także w tym artykule omówiono niektóre problemy, które można napotkać podczas zmiany z poziomu pozycji Debuguj kompilację wydania.

[Optymalizacja kodu](../../build/reference/optimizing-your-code.md)<br/>
Zawiera łącza do tematów omawiających mechanizmy optymalizacji kodu:

[Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md)<br/>
Wyświetlanie i manipulowanie dane wyjściowe kompilacji zawiera następujące narzędzia wiersza polecenia:

[Błędy kompilacji C/C++](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)<br/>
Wprowadza sekcję błędy kompilacji w tabeli treści.

## <a name="related-sections"></a>Sekcje pokrewne

[Dokumentacja preprocesora języka C/C++](../../preprocessor/c-cpp-preprocessor-reference.md)<br/>
W tym artykule omówiono preprocesora, który przygotowuje pliki źródłowe dla kompilatora zamieniane makra, operatorów i dyrektywy.

[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](../../ide/understanding-custom-build-steps-and-build-events.md)<br/>
W tym artykule omówiono, dostosowywanie procesu kompilacji.

[Kompilowanie programu C/C++](../../build/building-c-cpp-programs.md)<br/>
Zawiera łącza do tematów opisujących, tworzenie programu z wiersza polecenia lub zintegrowanego środowiska projektowego programu Visual Studio.

[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
W tym artykule opisano ustawienia Opcje kompilatora w środowisku programistycznym lub w wierszu polecenia.

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
Zawiera łącza do tematów omawiających używanie opcji kompilatora.

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
W tym artykule opisano opcje konsolidatora ustawienie wewnątrz lub na zewnątrz zintegrowanego środowiska programistycznego.

[Opcje konsolidatora](../../build/reference/linker-options.md)<br/>
Zawiera łącza do tematów omawiających używanie opcji konsolidatora.

[BSCMAKE — dokumentacja](../../build/reference/bscmake-reference.md)<br/>
W tym artykule opisano narzędzie konserwacji przeglądarki Microsoft informacji (BSCMAKE. Z rozszerzeniem EXE), które kompilacje pliku informacyjnego przeglądarki (.bsc) z .sbr pliki tworzone podczas kompilacji.

[LIB — dokumentacja](../../build/reference/lib-reference.md)<br/>
W tym artykule opisano menedżera biblioteki Microsoft (LIB.exe), który tworzy i którymi zarządza Biblioteka plików obiektów Common Object File Format (COFF).

[EDITBIN — dokumentacja](../../build/reference/editbin-reference.md)<br/>
W tym artykule opisano edytora pliku binarnego Microsoft COFF (EDITBIN. Z rozszerzeniem EXE), który modyfikuje pliki binarne Common Object File Format (COFF).

[DUMPBIN — dokumentacja](../../build/reference/dumpbin-reference.md)<br/>
W tym artykule opisano Microsoft COFF plik binarny zrzutu (DUMPBIN. Z rozszerzeniem EXE), który wyświetla informacje dotyczące plików binarnych Common Object File Format (COFF).

[NMAKE — dokumentacja](../../build/nmake-reference.md)<br/>
W tym artykule opisano narzędzie do konserwacji programów firmy Microsoft (NMAKE. Z rozszerzeniem EXE), czyli narzędzie, które kompilacje projektów oparte na polecenia zawarte w pliku opisu.