---
title: '/Zc: preprocesor (Włącz tryb zgodności preprocesora)'
description: Użyj opcji kompilatora preprocesora/Zc:, aby włączyć obsługę kompilatora dla preprocesora.
ms.date: 09/10/2020
f1_keywords:
- preprocessor
- /Zc:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /Zc:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 356434e4892966b9a9304021dd5d8770dcc2f8b1
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042905"
---
# <a name="zcpreprocessor-enable-preprocessor-conformance-mode"></a>`/Zc:preprocessor` (Włącz tryb zgodności preprocesora)

Ta opcja włącza preprocesor oparty na tokenach, który jest zgodny ze standardami C99 i C++ 11 i nowszymi. Aby uzyskać więcej informacji, zobacz temat [MSVC New preprocesora Overview](../../preprocessor/preprocessor-experimental-overview.md).

## <a name="syntax"></a>Składnia

> **`/Zc:preprocessor`**[**-**]

## <a name="remarks"></a>Uwagi

Użyj **`/Zc:preprocessor`** opcji kompilatora, aby włączyć preprocesor. Można użyć **`/Zc:preprocessor-`** opcji, aby jawnie określić tradycyjny (niezgodny) preprocesor.

Ta **`/Zc:preprocessor`** opcja jest dostępna w programie Visual Studio 2019 w wersji 16,5. Starsza, Niepełna wersja nowej opcji preprocesora jest dostępna w wersjach programu Visual Studio, począwszy od wersji 15,8 programu Visual Studio 2017. Aby uzyskać więcej informacji, zobacz [`/experimental:preprocessor`](experimental-preprocessor.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić *`/Zc:preprocessor`* , a następnie wybierz przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)
