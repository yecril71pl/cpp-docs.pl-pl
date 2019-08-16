---
title: /DEPENDENTLOADFLAG (Ustaw domyślne zależne flagi ładowania)
description: Opcja/DEPENDENTLOADFLAG ustawia domyślne flagi dla bibliotek DLL ładowanych przy użyciu funkcji LoadLibrary
ms.date: 05/18/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 072fa1103d049c7d5c395ae88d268f3b47e20b4f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492957"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (Ustaw domyślne zależne flagi ładowania)

Ustawia domyślne flagi ładowania używane podczas `LoadLibrary` ładowania bibliotek DLL.

## <a name="syntax"></a>Składnia

> **/DEPENDENTLOADFLAG** [ **:** _loadflags_]

### <a name="arguments"></a>Argumenty

*loadflags*<br/>
Opcjonalna 16-bitowa liczba całkowita w stylu "C" w liczbie dziesiętnej, ósemkowej z zerem wiodącym lub szesnastkowym z wiodącym `0x`znakiem, który określa zależne flagi obciążenia do zastosowania do wszystkich wywołań funkcji [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) . Wartość domyślna to 0.

## <a name="remarks"></a>Uwagi

Ta opcja jest nowa w programie Visual Studio 2017 i ma zastosowanie tylko do aplikacji uruchomionych w systemie Windows 10 RS1 i nowszych wersjach. Ta opcja jest ignorowana przez inne systemy operacyjne, na których jest uruchamiana aplikacja.

W obsługiwanych systemach operacyjnych ta opcja ma wpływ na zmianę wywołań `LoadLibrary("dependent.dll")` na `LoadLibraryEx("dependent.dll", 0, loadflags)`odpowiednik. Nie dotyczy to wywołań [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) . Ta opcja nie stosuje cyklicznie do bibliotek DLL ładowanych przez aplikację.

Ta flaga może służyć do zapobiegania atakom z przesadzeniem biblioteki DLL. Na przykład jeśli aplikacja używa `LoadLibrary` do załadowania zależnej biblioteki DLL, osoba atakująca może zakładać bibliotekę DLL o takiej samej nazwie w ścieżce wyszukiwania używanej przez `LoadLibrary`, na przykład w bieżącym katalogu, która może być sprawdzana przed katalogami systemowymi, jeśli tryb wyszukiwania w bezpiecznym formacie dll jest wyłączony. Tryb bezpiecznego wyszukiwania biblioteki DLL umieszcza bieżący katalog użytkownika później w kolejności wyszukiwania i jest domyślnie włączony w systemie Windows XP z dodatkiem SP2 i nowszych wersjach. Aby uzyskać więcej informacji, zobacz [kolejność wyszukiwania biblioteki dołączanej dynamicznie](/windows/win32/Dlls/dynamic-link-library-search-order).

W przypadku określenia opcji `/DEPENDENTLOADFLAG:0xA00` łącze (wartość połączonych flag `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), nawet jeśli tryb wyszukiwania bezpiecznych bibliotek DLL jest wyłączony na komputerze użytkownika, ścieżka wyszukiwania biblioteki DLL jest ograniczona do chronionych katalogów, które są trudniejsze dla osoby atakującej stąp. Aby uzyskać informacje na temat dostępnych flag oraz ich symbolicznych i liczbowych wartości, zobacz opis parametru *flagiDW* w [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję konsolidatora DEPENDENTLOADFLAG w środowisku deweloperskim programu Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja właściwości** > **wiersza polecenia** **konsolidatora** > .

1. Wprowadź opcję w opcjach **dodatkowych**.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja konsolidatora MSVC](linking.md)
- [Opcje konsolidatora MSVC](linker-options.md)
- [Łączenie pliku wykonywalnego z biblioteką DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Łączenie pliku wykonywalnego z biblioteką DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [Kolejność wyszukiwania biblioteki dołączanej dynamicznie](/windows/win32/Dlls/dynamic-link-library-search-order)
