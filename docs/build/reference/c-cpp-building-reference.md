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
ms.openlocfilehash: 116ddca6ed9f5e0b3ea02652958931f88cc8fc13
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703225"
---
# <a name="cc-building-reference"></a>Odwołanie kompilacji C/C++

Visual C++ zapewnia dwa sposoby kompilowanie programu C/C++. Najłatwiejszym (i najbardziej powszechnym) sposobem jest [kompilacji w środowisku deweloperskim Visual C++](../../ide/building-cpp-projects-in-visual-studio.md). Drugi sposób to [kompilacji z wiersza polecenia przy użyciu narzędzia wiersza polecenia](../../build/building-on-the-command-line.md). W obu przypadkach można utworzyć plików źródłowych, za pomocą edytora źródła Visual C++ lub ulubionego edytora w innych firm.

Jeśli program używa pliku reguł programu make, a nie plik .vcxproj, nadal tworzyć go w środowisku programistycznym jako [projektu zewnętrznego](../../ide/building-external-projects.md).

## <a name="in-this-section"></a>W tej sekcji

[Kompilowanie programu C/C++](../../build/reference/compiling-a-c-cpp-program.md) opisuje kompilator tworzy plik obiektu zawierającego kod maszynowy, dyrektywy konsolidatora, sekcje, odwołania zewnętrzne i nazwy funkcji/danych.

[Łączenie](../../build/reference/linking.md) opisuje konsolidatora, która łączy kod z plikami obiekt utworzony przez kompilator i statycznie łączonych bibliotek, jest rozpoznawana jako odwołania do nazwy i tworzy plik wykonywalny.

[Kompilacje wydania](../../build/reference/release-builds.md) umożliwia wyświetlanie informacji na temat kiedy i dlaczego chcesz zmienić z kompilacji debugowania do kompilacji wydania i również w tym artykule omówiono niektóre problemy mogą wystąpić w przypadku zmiany z debugowania na kompilację wydania.

[Optymalizacja kodu](../../build/reference/optimizing-your-code.md) zawiera łącza do tematów omawiających mechanizmy optymalizacji kodu:

[Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md) zawiera następujące narzędzia wiersza polecenia do wyświetlania lub modyfikowania dane wyjściowe kompilacji:

[Błędy kompilacji C/C++](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) wprowadza sekcję błędy kompilacji w tabeli treści.

## <a name="related-sections"></a>Sekcje pokrewne

[C/C++ Preprocessor Reference](../../preprocessor/c-cpp-preprocessor-reference.md) w tym artykule omówiono preprocesora, który przygotowuje pliki źródłowe dla kompilatora zamieniane makra, operatorów i dyrektywy.

[Kroki tworzenia niestandardowych interpretacji i zdarzenia kompilacji](../../ide/understanding-custom-build-steps-and-build-events.md) Discusses Dostosowywanie procesu kompilacji.

[Kompilowanie programu C/C++](../../build/building-c-cpp-programs.md) zawiera łącza do tematów opisujących, tworzenie programu z wiersza polecenia lub zintegrowanego środowiska projektowego programu Visual Studio.

[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md) w tym artykule opisano ustawienia Opcje kompilatora w środowisku programistycznym lub w wierszu polecenia.

[Opcje kompilatora](../../build/reference/compiler-options.md) zawiera łącza do tematów omawiających używanie opcji kompilatora.

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md) w tym artykule opisano opcje konsolidatora ustawienie wewnątrz lub na zewnątrz zintegrowanego środowiska programistycznego.

[Opcje konsolidatora](../../build/reference/linker-options.md) zawiera łącza do tematów omawiających używanie opcji konsolidatora.

[Bscmake — dokumentacja](../../build/reference/bscmake-reference.md) opisano narzędzie konserwacji przeglądania firmy Microsoft informacje (BSCMAKE. Z rozszerzeniem EXE), które kompilacje pliku informacyjnego przeglądarki (.bsc) z .sbr pliki tworzone podczas kompilacji.

[Odwołanie do biblioteki LIB](../../build/reference/lib-reference.md) opisuje menedżera biblioteki Microsoft (LIB.exe), który tworzy i którymi zarządza Biblioteka plików obiektów Common Object File Format (COFF).

[Odwołanie EDITBIN](../../build/reference/editbin-reference.md) opisuje edytora pliku binarnego Microsoft COFF (EDITBIN. Z rozszerzeniem EXE), który modyfikuje pliki binarne Common Object File Format (COFF).

[Odwołanie DUMPBIN](../../build/reference/dumpbin-reference.md) opisuje Microsoft COFF plik binarny zrzutu (DUMPBIN. Z rozszerzeniem EXE), który wyświetla informacje dotyczące plików binarnych Common Object File Format (COFF).

[NMAKE — dokumentacja](../../build/nmake-reference.md) Opisuje narzędzie do konserwacji programów firmy Microsoft (NMAKE. Z rozszerzeniem EXE), czyli narzędzie, które kompilacje projektów oparte na polecenia zawarte w pliku opisu.