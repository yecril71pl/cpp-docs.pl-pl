---
title: MSVC C/C++ kompilator Reference-Visual Studio
description: Opcje zestawu narzędzi kompilatora MSVC.
ms.date: 12/10/2018
helpviewer_keywords:
- cl.exe compiler
- cl.exe compiler, setting options
ms.assetid: f3eef5ab-d0be-4fb2-90f9-927e6ed58736
ms.openlocfilehash: c75176b139895d7b00d88aca1c58604b47386894
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077378"
---
# <a name="compiling-a-cc-project"></a>Kompilowanie projektu CC++ /

Opcje języka C++ C i kompilatora można ustawić w środowisku IDE programu Visual Studio lub w wierszu polecenia.

## <a name="in-visual-studio"></a>W programie Visual Studio

Można ustawić opcje kompilatora dla każdego projektu w oknie dialogowym **strony właściwości** programu Visual Studio. W lewym okienku wybierz **Właściwości konfiguracji**, **C/C++**  , a następnie wybierz kategorię opcji kompilatora. Temat dla każdej opcji kompilatora opisuje, jak ją można ustawić i gdzie występuje w środowisku programistycznym. Aby uzyskać pełną listę, zobacz [Opcje kompilatora MSVC](compiler-options.md) .

## <a name="from-the-command-line"></a>Z wiersza polecenia

Można ustawić opcje kompilatora (CL.exe):

- [W wierszu polecenia](compiler-command-line-syntax.md)

- [W plikach poleceń](cl-command-files.md)

- [W zmiennej środowiskowej CL](cl-environment-variables.md)

Opcje określone w zmiennej środowiskowej CL są używane za każdym razem, gdy wywołuje się CL. Jeśli plik poleceń jest podany w zmiennej środowiskowej CL lub w wierszu polecenia, używane są opcje określone w pliku poleceń. W przeciwieństwie do wiersza polecenia lub zmiennej środowiskowej CL, plik poleceń pozwala na używanie wielu wierszy opcji i nazw plików.

Opcje kompilatora są przetwarzane „od lewej do prawej,” a w przypadku wykrycia konfliktu pierwszeństwo ma ostatnia opcja (najdalej po prawej stronie). Zmienna środowiskowa CL jest przetwarzana przed wierszem polecenia, więc w każdym konflikcie między CL i wierszem polecenia ten ostatni ma pierwszeństwo.

## <a name="additional-compiler-topics"></a>Tematy dodatkowe kompilatora

- [Opcje kompilatora MSVC](compiler-options.md)

- [Prekompilowane pliki nagłówka](../creating-precompiled-header-files.md)

- [CL wywołuje konsolidator](cl-invokes-the-linker.md)

Aby uzyskać informacje na temat wybierania hosta kompilatora i architektury docelowej, [Zobacz C++ konfigurowanie projektów dla 64-bitowych i x64 obiektów docelowych](../configuring-programs-for-64-bit-visual-cpp.md).

## <a name="see-also"></a>Zobacz też

[Dokumentacja kompilacji w języku C/C++](c-cpp-building-reference.md)
