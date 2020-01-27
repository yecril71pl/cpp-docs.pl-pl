---
title: /DEPENDENTLOADFLAG (Ustaw domyślne zależne flagi ładowania)
description: Opcja/DEPENDENTLOADFLAG ustawia domyślne zależne flagi ładowania dla bibliotek DLL ładowanych przez ten moduł.
ms.date: 01/22/2020
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 5e31a0d747e7186814cba3ae1c4cf243569d87a8
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725711"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (Ustaw domyślne zależne flagi ładowania)

::: moniker range="vs-2015"

Opcja **/DEPENDENTLOADFLAG** wymaga programu Visual Studio 2017 lub nowszego.

::: moniker-end

::: moniker range=">=vs-2017"

Ustawia domyślne flagi ładowania używane, gdy system operacyjny rozwiązuje statycznie połączone Importowanie modułu.

## <a name="syntax"></a>Składnia

> **/DEPENDENTLOADFLAG**[ __:__ *load_flags*]

### <a name="arguments"></a>Argumenty

*load_flags*<br/>
Opcjonalna wartość całkowita, która określa flagi ładowania do zastosowania podczas rozpoznawania połączonych statycznie zależności importu modułu. Wartość domyślna to 0. Aby zapoznać się z listą obsługiwanych wartości flag, zobacz wpisy `LOAD_LIBRARY_SEARCH_*` w [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

## <a name="remarks"></a>Uwagi

Gdy system operacyjny rozwiązuje statycznie połączone Importowanie modułu, używa [domyślnej kolejności wyszukiwania](/windows/win32/dlls/dynamic-link-library-search-order). Użyj opcji **/DEPENDENTLOADFLAG** , aby określić wartość *load_flags* , która zmienia ścieżkę wyszukiwania używaną do rozpoznania tych importów. W obsługiwanych systemach operacyjnych zmienia kolejność wyszukiwania statycznej rozdzielczości importowania, podobnie jak [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa) w przypadku używania parametrów `LOAD_LIBRARY_SEARCH`. Aby uzyskać informacje na temat kolejności wyszukiwania ustawionej przez *load_flags*, zobacz [kolejność wyszukiwania przy użyciu flag LOAD_LIBRARY_SEARCH](/windows/win32/dlls/dynamic-link-library-search-order#search-order-using-load_library_search-flags).

Ta flaga może służyć do wydzielenia przez jeden wektor [ataku z przesadzeniem biblioteki DLL](/windows/win32/dlls/dynamic-link-library-security) . Rozważmy na przykład aplikację, która ma statycznie połączoną bibliotekę DLL:

- Osoba atakująca może zakładać bibliotekę DLL o tej samej nazwie wcześniej w ścieżce wyszukiwania rozdzielczości importowania, takiej jak katalog aplikacji. Katalogi chronione są trudniejsze, ale nie są możliwe do zmiany przez osobę atakującą.

- Jeśli brakuje biblioteki DLL w katalogach aplikacji,%Windows%\System32 i% Windows%, rozwiązanie do importowania zostanie przechodzące do bieżącego katalogu. Osoba atakująca może zakładać bibliotekę DLL.

W obu przypadkach, jeśli określisz opcję łącza `/DEPENDENTLOADFLAG:0x800` (wartość flagi `LOAD_LIBRARY_SEARCH_SYSTEM32`), ścieżka wyszukiwania modułu jest ograniczona do katalogu%Windows%\System32. Oferuje pewną ochronę przed atakami na inne katalogi. Aby uzyskać więcej informacji, zobacz [zabezpieczenia biblioteki dołączanej dynamicznie](/windows/win32/dlls/dynamic-link-library-security).

Aby wyświetlić wartość ustawioną przez opcję **/DEPENDENTLOADFLAG** w dowolnej bibliotece DLL, użyj polecenia [polecenia DUMPBIN](dumpbin-reference.md) z opcją [/LOADCONFIG](loadconfig.md) .

Opcja **/DEPENDENTLOADFLAG** jest nowa w programie Visual Studio 2017. Dotyczy tylko aplikacji uruchomionych w systemie Windows 10 RS1 i nowszych wersjach. Ta opcja jest ignorowana przez inne systemy operacyjne, na których jest uruchamiana aplikacja.

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję konsolidatora DEPENDENTLOADFLAG w środowisku deweloperskim programu Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz opcję **Właściwości konfiguracji** > **konsolidator** > strony właściwości **wiersza polecenia** .

1. Wprowadź opcję w opcjach **dodatkowych**.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja konsolidatora MSVC](linking.md)
- [MSVC Opcje konsolidatora](linker-options.md)
- [Łączenie pliku wykonywalnego z biblioteką DLL niejawnie](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Określanie, która Metoda łączenia ma być używana](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [Kolejność wyszukiwania biblioteki dołączanej dynamicznie](/windows/win32/Dlls/dynamic-link-library-search-order)
- [Zabezpieczenia biblioteki dołączanej dynamicznie](/windows/win32/dlls/dynamic-link-library-security)

::: moniker-end
