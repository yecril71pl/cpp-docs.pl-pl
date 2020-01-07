---
title: /DEPENDENTLOADFLAG (Ustaw domyślne zależne flagi ładowania)
description: Opcja/DEPENDENTLOADFLAG ustawia domyślne flagi dla bibliotek DLL ładowanych przy użyciu funkcji LoadLibrary
ms.date: 12/22/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 3a403f22c88ccd3e25ba95c183656ad2ffafd05a
ms.sourcegitcommit: ef34a11cb04511221bf5c7b9f4f55ad91a7a603f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2019
ms.locfileid: "75330001"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (Ustaw domyślne zależne flagi ładowania)

Ustawia domyślne flagi ładowania używane, gdy `LoadLibrary` jest używany do ładowania bibliotek DLL.

## <a name="syntax"></a>Składnia

> **/DEPENDENTLOADFLAG**[ __:__ *load_flags*]

### <a name="arguments"></a>Argumenty

*load_flags*<br/>
Opcjonalna 16-bitowa liczba całkowita w stylu "C" w liczbie dziesiętnej, ósemkowej z zerem wiodącym lub szesnastkowym z wiodącym `0x`, który określa flagi ładowania zależnego do zastosowania do wszystkich wywołań funkcji [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) . Wartość domyślna to 0.

## <a name="remarks"></a>Uwagi

Ta opcja jest nowa w programie Visual Studio 2017. Dotyczy tylko aplikacji uruchomionych w systemie Windows 10 RS1 i nowszych wersjach. Ta opcja jest ignorowana przez inne systemy operacyjne, na których jest uruchamiana aplikacja.

W obsługiwanych systemach operacyjnych ta opcja ma wpływ na zmianę wywołań `LoadLibrary("dependent.dll")` na odpowiednik `LoadLibraryEx("dependent.dll", 0, load_flags)`. Nie dotyczy to wywołań [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) . Ta opcja nie jest stosowana rekursywnie do bibliotek DLL ładowanych przez aplikację.

Ta flaga może być używana w celu trudniejszego ataków na tworzenie [bibliotek DLL](/windows/win32/dlls/dynamic-link-library-security) . Na przykład jeśli aplikacja używa `LoadLibrary` do załadowania zależnej biblioteki DLL, osoba atakująca może zakładać bibliotekę DLL o takiej samej nazwie w ścieżce wyszukiwania używanej przez `LoadLibrary`, na przykład w bieżącym katalogu, który można sprawdzić przed katalogami systemowymi, jeśli bezpieczny tryb wyszukiwania DLL jest wyłączony. Tryb bezpiecznego wyszukiwania biblioteki DLL umieszcza bieżący katalog użytkownika później w kolejności wyszukiwania i jest domyślnie włączony w systemie Windows XP z dodatkiem SP2 i nowszych wersjach. Aby uzyskać więcej informacji, zobacz [kolejność wyszukiwania biblioteki dołączanej dynamicznie](/windows/win32/Dlls/dynamic-link-library-search-order).

W przypadku określenia opcji linku `/DEPENDENTLOADFLAG:0xA00` (wartość połączonych flag `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), a nawet jeśli na komputerze użytkownika jest wyłączony tryb wyszukiwania bezpiecznych bibliotek DLL, ścieżka wyszukiwania biblioteki DLL jest ograniczona do katalogu aplikacji, po którym następuje katalog%Windows%\System32. Opcja `/DEPENDENTLOADFLAG:0x800` jest jeszcze bardziej restrykcyjna, ograniczając wyszukiwanie do katalogu%Windows%\System32. Katalogi chronione są trudniejsze, ale nie są możliwe do zmiany przez osobę atakującą. Aby uzyskać informacje na temat dostępnych flag oraz ich symbolicznych i liczbowych wartości, zobacz opis parametru *flagiDW* w [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw). Aby uzyskać informacje na temat kolejności wyszukiwania używanej w przypadku używania różnych zależnych flag obciążenia, zobacz [kolejność wyszukiwania przy użyciu flag LOAD_LIBRARY_SEARCH](/windows/win32/dlls/dynamic-link-library-search-order#search-order-using-load_library_search-flags).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję konsolidatora DEPENDENTLOADFLAG w środowisku deweloperskim programu Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz opcję **Właściwości konfiguracji** > **konsolidator** > strony właściwości **wiersza polecenia** .

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
