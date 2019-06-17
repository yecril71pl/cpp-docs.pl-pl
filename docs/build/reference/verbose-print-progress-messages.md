---
title: /VERBOSE (Drukuj komunikaty o postępie)
ms.date: 06/13/2019
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
ms.openlocfilehash: bbf7b5966c741535f26202979cbfd71f839cc537
ms.sourcegitcommit: e79188287189b76b34eb7e8fb1bfe646bdb586bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141668"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE (Drukuj komunikaty o postępie)

Dane wyjściowe komunikaty o postępie podczas procesu łączenia.

## <a name="syntax"></a>Składnia

> **/ VERBOSE**\[ **:** {**CLR**|**ICF**|**INCR** | **LIB**|**REF**|**SAFESEH**|**UNUSEDDELAYLOAD** | **UNUSEDLIBS**}\]

## <a name="remarks"></a>Uwagi

Program łączący wysyła informacje o postępie łączenia sesji, do **dane wyjściowe** okna. W wierszu polecenia informacje są wysyłane do wyjścia standardowego i mogą zostać przekierowane do pliku.

| Opcja | Opis |
| ------------ | ----------------- |
| /VERBOSE | Wyświetla szczegóły dotyczące proces łączenia. |
| /VERBOSE:CLR | Wyświetla informacje na temat aktywności konsolidatora określonych obiektów i kompilowany przy użyciu metadanych [/CLR](clr-common-language-runtime-compilation.md). |
| /VERBOSE:ICF | Przedstawia informacje na temat aktywności konsolidatora, które powstały na skutek stosowania [/OPT: ICF](opt-optimizations.md). |
| /VERBOSE:INCR | Wyświetla informacje na temat przyrostowego procesu łączenia. |
| / VERBOSE: LIB | Wyświetla wiadomości postępu, które wskazują wyłącznie biblioteki przeszukiwane.<br/> Wyświetlane informacje obejmują proces wyszukiwania biblioteki. Wyświetla listę każdej nazwy biblioteki i obiektu (z pełną ścieżką), symbolu zamieniana z biblioteki i listy obiektów, które odwołują się symbol. |
| / VERBOSE: REF | Przedstawia informacje na temat aktywności konsolidatora, które powstały na skutek stosowania [/OPT: REF](opt-optimizations.md). |
| / VERBOSE: SAFESEH | Wyświetla informacje dotyczące modułów, które są niezgodne z podczas obsługi bezpiecznych wyjątków strukturalnych [opcja/SAFESEH](safeseh-image-has-safe-exception-handlers.md) nie został określony. |
| / VERBOSE: UNUSEDDELAYLOAD | Wyświetla informacje o wszelkich opóźnień załadować biblioteki dll, które mają nie symbole używane podczas tworzenia obrazu. |
| / VERBOSE: UNUSEDLIBS | Wyświetla informacje o dowolnych plikach bibliotek, które nie są używane podczas tworzenia obrazu. |

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Dodaj opcję **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
