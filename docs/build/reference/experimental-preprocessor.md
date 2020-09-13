---
title: '/Experimental: preprocesor (Włącz tryb zgodności preprocesora)'
description: Użyj opcji kompilatora preprocesora/Experimental:, aby włączyć obsługę kompilatora eksperymentalnego dla preprocesora, który jest zgodny ze standardem.
ms.date: 09/10/2020
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 9a98289434e7154d2ec8b8753d990876a8218acf
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042098"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>`/experimental:preprocessor` (Włącz tryb zgodności preprocesora)

Ta opcja jest przestarzała począwszy od programu Visual Studio 2019 w wersji 16,5, zastąpiona przez [`/Zc:preprocessor`](zc-preprocessor.md) opcję kompilatora. **`/experimental:preprocessor`** Włącza eksperymentalny, oparty na tokenach proces preprocesora, który jest ściśle zgodny ze standardami języka C++ 11, w tym funkcjami preprocesora C99. Aby uzyskać więcej informacji, zobacz temat [MSVC New preprocesora Overview](../../preprocessor/preprocessor-experimental-overview.md).

## <a name="syntax"></a>Składnia

> **`/experimental:preprocessor`**\[**`-`**]

## <a name="remarks"></a>Uwagi

Użyj **`/experimental:preprocessor`** opcji kompilatora, aby włączyć eksperymentalny preprocesor. Można użyć **`/experimental:preprocessor-`** opcji, aby jawnie określić tradycyjny preprocesor.

Ta **`/experimental:preprocessor`** opcja jest dostępna w programie Visual Studio 2017 w wersji 15,8. Począwszy od programu Visual Studio 2019 w wersji 16,5, nowy preprocesor jest kompletny i dostępny w ramach [`/Zc:preprocessor`](zc-preprocessor.md) opcji kompilatora.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić *`/experimental:preprocessor`* , a następnie wybierz przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)
