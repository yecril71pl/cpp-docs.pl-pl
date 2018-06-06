---
title: / DEPENDENTLOADFLAG (flagi zależnych obciążenia domyślny zestaw)
description: Opcja /DEPENDENTLOADFLAG ustawia domyślną flagi dla biblioteki DLL ładowane przy użyciu metody LoadLibrary
ms.custom: ''
ms.date: 05/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- dependentloadflag
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a171f3c2edbbbf614a986ff78dd2405e734a1d1
ms.sourcegitcommit: d1f576a0f59678edc3d93508cf46485138332178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753724"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/ DEPENDENTLOADFLAG (flagi zależnych obciążenia domyślny zestaw)

Ustawia flagi obciążenia domyślne używane podczas `LoadLibrary` jest używana do załadowania biblioteki dll.

## <a name="syntax"></a>Składnia

> **/ DEPENDENTLOADFLAG**[**:**_loadflags_]

### <a name="arguments"></a>Argumenty

|||
|-|-|
*loadflags*|Opcjonalna wartość 16-bitową liczbę całkowitą stylu "C" decimal, ósemkową zerem lub szesnastkowe z wiodącym `0x`, określa flagi zależnych obciążenia do zastosowania do wszystkich [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187) wywołania. Wartość domyślna to 0.

## <a name="remarks"></a>Uwagi

Ta opcja jest nowa w programie Visual Studio 2017 i ma zastosowanie tylko do aplikacji działających w systemie Windows 10 RS1 i nowszych wersjach. Ta opcja jest ignorowana przez inne systemy operacyjne, które Uruchom aplikację.

W obsługiwanych systemach operacyjnych, ta opcja ma wpływ zmiany wywołania `LoadLibrary("dependent.dll")` do odpowiednikiem `LoadLibraryEx("dependent.dll", 0, loadflags)`. Wywołuje się [LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091) nie dotyczy to. Ta opcja nie dotyczą rekursywnie bibliotek DLL załadowanych przez aplikację.

Ta flaga można zapobiec DLL sadzenia ataków. Na przykład, jeśli aplikacja używa `LoadLibrary` załadować zależnej biblioteki DLL, osoba atakująca może DLL o takiej samej nazwie w roślin ścieżka wyszukiwania używana przez `LoadLibrary`, takich jak bieżącego katalogu, które mogą być sprawdzane przed katalogów systemu, jeśli jest w trybie awaryjnym wyszukiwania biblioteki DLL wyłączone. Tryb awaryjny wyszukiwania biblioteki DLL umieszcza użytkownika bieżącego katalogu później w kolejności wyszukiwania i jest domyślnie włączone w systemie Windows XP z dodatkiem SP2 lub nowszym. Aby uzyskać więcej informacji, zobacz [kolejność wyszukiwania biblioteki dll](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx).

Jeśli określono opcję łącze `/DEPENDENTLOADFLAG:0xA00` (wartości z połączonych flag `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), nawet po wyłączeniu trybu awaryjnego wyszukiwania biblioteki DLL na komputerze użytkownika, ścieżka wyszukiwania biblioteki DLL jest ograniczona do katalogów chronionych, które utrudnia osobie atakującej Zmiana. Dla informacji o flagach dostępne, a ich wartości numerycznych i symbolicznych, zobacz *wartość elementu dwFlags* opis parametru w [LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Ustawianie opcji konsolidatora DEPENDENTLOADFLAG w środowisku projektowym Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** strony właściwości.

1. Wybierz opcję w **dodatkowe opcje**.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](setting-linker-options.md)
- [Opcje konsolidatora](linker-options.md)
- [Jak połączyć niejawnie z biblioteki DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Określić jakiej metody łączenia użyć](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187)
- [LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091)
- [Kolejność wyszukiwania biblioteki dll](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)
