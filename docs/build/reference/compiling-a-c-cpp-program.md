---
title: Odwołanie do kompilatora MSVC C/C++ — Visual Studio
description: Opcje zestawu narzędzi kompilatora MSVC.
ms.date: 12/10/2018
helpviewer_keywords:
- cl.exe compiler
- cl.exe compiler, setting options
ms.assetid: f3eef5ab-d0be-4fb2-90f9-927e6ed58736
ms.openlocfilehash: 2269ba69cea2702ff190c791eb6753acb3619f7d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810305"
---
# <a name="compiling-a-cc-project"></a>Kompilowanie projektu języka C/C++

W środowisku IDE programu Visual Studio lub w wierszu polecenia można ustawić opcje kompilatora C i C++. 

## <a name="in-visual-studio"></a>In Visual Studio

Można ustawić opcje kompilatora dla każdego projektu w jego programu Visual Studio **stron właściwości** okno dialogowe. W okienku po lewej stronie wybierz **właściwości konfiguracji**, **C/C++** , a następnie wybierz kategorię opcji kompilatora. Temat dla każdej opcji kompilatora opisuje, jak ją można ustawić i gdzie występuje w środowisku programistycznym. Zobacz [opcje kompilatora MSVC](compiler-options.md) pełną listę.

## <a name="from-the-command-line"></a>Z poziomu wiersza polecenia

Można ustawić opcje kompilatora (CL.exe):

- [W wierszu polecenia](compiler-command-line-syntax.md)

- [W plikach poleceń](cl-command-files.md)

- [W zmiennej środowiskowej CL](cl-environment-variables.md)

Opcje określone w zmiennej środowiskowej CL są używane za każdym razem, gdy wywołuje się CL. Jeśli plik poleceń jest podany w zmiennej środowiskowej CL lub w wierszu polecenia, używane są opcje określone w pliku poleceń. W przeciwieństwie do wiersza polecenia lub zmiennej środowiskowej CL, plik poleceń pozwala na używanie wielu wierszy opcji i nazw plików.

Opcje kompilatora są przetwarzane „od lewej do prawej,” a w przypadku wykrycia konfliktu pierwszeństwo ma ostatnia opcja (najdalej po prawej stronie). Zmienna środowiskowa CL jest przetwarzana przed wierszem polecenia, więc w każdym konflikcie między CL i wierszem polecenia ten ostatni ma pierwszeństwo.

## <a name="additional-compiler-topics"></a>Tematy dodatkowe kompilatora

- [MSVC Compiler Options](compiler-options.md)

- [Prekompilowane pliki nagłówka](../creating-precompiled-header-files.md)

- [CL wywołuje konsolidator](cl-invokes-the-linker.md)

Aby uzyskać informacje na temat wybierania kompilatora Architektura źródłowa i docelowa, zobacz [Konfigurowanie projektów w języku C++ dla wersji 64-bitowych, x64 cele](../configuring-programs-for-64-bit-visual-cpp.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](c-cpp-building-reference.md)
