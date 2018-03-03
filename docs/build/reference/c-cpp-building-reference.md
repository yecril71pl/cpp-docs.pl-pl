---
title: "Odwołanie kompilacji C/C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e2269be27dd039357c11d38a2be83b5fc9d6504
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cc-building-reference"></a>Odwołanie kompilacji C/C++
Visual C++ udostępnia dwa sposoby tworzenia programu C/C++. Sposób najprostszym (i najbardziej typowych) polega na [kompilacji w środowisku programowania Visual C++](../../ide/building-cpp-projects-in-visual-studio.md). Innym sposobem jest [kompilacji z wiersza polecenia przy użyciu narzędzia wiersza polecenia](../../build/building-on-the-command-line.md). W obu przypadkach można utworzyć plików źródłowych, za pomocą edytora źródła Visual C++ lub dowolnego edytora innych firm.  
  
 Jeśli program używa pliku reguł programu make zamiast pliku .vcxproj, można nadal jego tworzenia w środowisku programistycznym jako [projektu zewnętrznego](../../ide/building-external-projects.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kompilowanie programu C/C++](../../build/reference/compiling-a-c-cpp-program.md)  
 W tym artykule opisano kompilatora, która tworzy plik obiektu zawierającego kod maszynowy, dyrektywy konsolidatora, sekcje, odwołań zewnętrznych i nazwy funkcji i danych.  
  
 [Konsolidacja](../../build/reference/linking.md)  
 Opisuje konsolidator, która łączy kodu z plików obiekt utworzony przez kompilator i biblioteki statycznie połączonej, usuwa odwołania do nazwy i tworzy plik wykonywalny.  
  
 [Kompilacje wydania](../../build/reference/release-builds.md)  
 Przedstawia informacje na kiedy i dlaczego należy zmienić debugowania kompilacji do kompilacji wydania i omówiono także niektóre problemy, które można napotkać podczas zmiany z debugowanie kompilacji wydania.  
  
 [Optymalizacja kodu](../../build/reference/optimizing-your-code.md)  
 Zawiera łącza do tematów dyskutować mechanizmu optymalizacji kodu:  
  
 [Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md)  
 Udostępnia następujące narzędzia wiersza polecenia do wyświetlania lub modyfikowania danych wyjściowych kompilacji:  
  
 [Błędy kompilacji C/C++](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)  
 Wprowadza sekcji błędy kompilacji w tabeli treści.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dokumentacja preprocesora języka C/C++](../../preprocessor/c-cpp-preprocessor-reference.md)  
 W tym artykule omówiono preprocesora, który przygotowuje pliki źródłowe dla kompilatora przez tłumaczenie makra, Operatorzy i dyrektywy.  
  
 [Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](../../ide/understanding-custom-build-steps-and-build-events.md)  
 W tym artykule omówiono Dostosowywanie procesu kompilacji.  
  
 [Kompilowanie programu C/C++](../../build/building-c-cpp-programs.md)  
 Zawiera łącza do tematów opisujących kompilowania programu z wiersza polecenia lub zintegrowane środowisko programistyczne Visual Studio.  
  
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  
 Zawiera opis opcji kompilatora ustawienie w środowisku programistycznym lub w wierszu polecenia.  
  
 [Opcje kompilatora](../../build/reference/compiler-options.md)  
 Zawiera łącza do tematów dyskutować przy użyciu opcji kompilatora.  
  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)  
 Opisuje opcje konsolidatora ustawienie wewnątrz lub na zewnątrz zintegrowane środowisko programistyczne.  
  
 [Opcje konsolidatora](../../build/reference/linker-options.md)  
 Zawiera łącza do tematów dyskutować przy użyciu opcji konsolidatora.  
  
 [BSCMAKE — dokumentacja](../../build/reference/bscmake-reference.md)  
 W tym artykule opisano narzędzie konserwacji przeglądarki Microsoft informacji (BSCMAKE. (EXE), które kompilacje pliku informacyjnego przeglądarki (.bsc) z .sbr plików utworzonych podczas kompilacji.  
  
 [LIB — dokumentacja](../../build/reference/lib-reference.md)  
 W tym artykule opisano menedżera biblioteki Microsoft (LIB.exe), który tworzy i którymi zarządza biblioteki plików obiektów wspólnej obiektu pliku formatu (COFF).  
  
 [EDITBIN — dokumentacja](../../build/reference/editbin-reference.md)  
 W tym artykule opisano edytora pliku binarnego Microsoft COFF (polecenia EDITBIN. (EXE), który modyfikuje pliki binarne wspólnej obiektu pliku formatu (COFF).  
  
 [DUMPBIN — dokumentacja](../../build/reference/dumpbin-reference.md)  
 W tym artykule opisano Microsoft COFF plik binarny zrzutu (DUMPBIN. (EXE), który wyświetla informacje o pliki binarne wspólnej obiektu pliku formatu (COFF).  
  
 [NMAKE — dokumentacja](../../build/nmake-reference.md)  
 W tym artykule opisano narzędzie do konserwacji programów firmy Microsoft (NMAKE. EXE), który jest narzędziem do kompilacji projekty oparte na polecenia zawarte w pliku opisu.