---
title: / DEPENDENTLOADFLAG (zestaw domyślne zależne obciążenia flagi)
description: Opcja /DEPENDENTLOADFLAG ustawia domyślne flagi dla bibliotek DLL załadowane przy użyciu LoadLibrary
ms.date: 05/18/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 80065bb4e67674c49761d0832395ae535bbfbf24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604290"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/ DEPENDENTLOADFLAG (zestaw domyślne zależne obciążenia flagi)

Ustawia flagi obciążenia domyślne używane podczas `LoadLibrary` jest używana do ładowania bibliotek DLL.

## <a name="syntax"></a>Składnia

> **/ DEPENDENTLOADFLAG**[**:**_loadflags_]

### <a name="arguments"></a>Argumenty

|||
|-|-|
*loadflags*|Opcjonalna wartość 16-bitową liczbę całkowitą "C" stylu w dziesiętnej, ósemkowej z zerem wiodącym lub szesnastkowe z wiodącym `0x`, określa flagi zależne obciążenia, aby mają zastosowanie do wszystkich [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) wywołania. Wartość domyślna to 0.

## <a name="remarks"></a>Uwagi

Ta opcja jest nowa w programie Visual Studio 2017 i ma zastosowanie tylko do aplikacji działających w systemie Windows 10 RS1 lub nowszym. Ta opcja jest ignorowana przez inne systemy operacyjne, które uruchomią aplikację.

W obsługiwanych systemach operacyjnych, ta opcja ma efekt zmiany wywołania `LoadLibrary("dependent.dll")` do równowartości `LoadLibraryEx("dependent.dll", 0, loadflags)`. Wywołania [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) nie ma wpływu. Ta opcja nie dotyczy rekursywnie biblioteki DLL ładowane przez aplikację.

Ta flaga może służyć do uniemożliwić DLL sadzenia ataków. Na przykład, jeśli aplikacja używa `LoadLibrary` załadować zależnej biblioteki DLL, osoba atakująca może DLL o takiej samej nazwie w roślin ścieżka wyszukiwania używana przez `LoadLibrary`, takich jak bieżącego katalogu, które można kontrolować przed katalogów systemu, jeśli jest w trybie awaryjnym wyszukiwania biblioteki DLL wyłączone. Tryb awaryjny wyszukiwania biblioteki DLL umieszcza katalogu bieżącego użytkownika w dalszej kolejności wyszukiwania i jest włączona domyślnie w systemie Windows XP z dodatkiem SP2 i nowszych wersjach. Aby uzyskać więcej informacji, zobacz [kolejności przeszukiwania bibliotek dołączanych dynamicznie](/windows/desktop/Dlls/dynamic-link-library-search-order).

W przypadku określenia opcji link `/DEPENDENTLOADFLAG:0xA00` (wartość flagi połączone `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), wówczas nawet jeśli tryb awaryjny wyszukiwania biblioteki DLL jest wyłączone na komputerze użytkownika, ścieżka wyszukiwania biblioteki DLL jest ograniczona do chronionego katalogi, które są utrudnia osobie atakującej Zmiana. Aby uzyskać informacji na temat flagi, które są dostępne, a ich symboliczne i liczbowe wartości, zobacz *Flagidw* opis parametru w [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję konsolidatora DEPENDENTLOADFLAG w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje**.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](setting-linker-options.md)
- [Opcje konsolidatora](linker-options.md)
- [Jak połączyć niejawnie biblioteki DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Określić, której metody łączenia użyjesz](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)
- [Kolejności przeszukiwania bibliotek dołączanych dynamicznie](/windows/desktop/Dlls/dynamic-link-library-search-order)
