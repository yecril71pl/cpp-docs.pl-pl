---
title: '/Experimental: preprocesor (Włącz tryb zgodności preprocesora)'
description: Użyj opcji kompilatora preprocesora/Experimental:, aby włączyć obsługę kompilatora eksperymentalnego dla preprocesora, który jest zgodny ze standardem.
ms.date: 10/31/2019
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: cb1ac63d2c12083975139455d8625544cb419adf
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754042"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>/Experimental: preprocesor (Włącz tryb zgodności preprocesora)

Ta opcja włącza eksperymentalny, oparty na tokenach proces preprocesora, który jest ściśle zgodny ze standardami języka C++ 11, w tym funkcjami preprocesora C99. Aby uzyskać więcej informacji, zobacz [MSVC eksperymentalny preprocesora — Omówienie](../../preprocessor/preprocessor-experimental-overview.md).

## <a name="syntax"></a>Składnia

> **/Experimental: preprocesor**[ **-** ]

## <a name="remarks"></a>Uwagi

Użyj opcji kompilatora **preprocesora/Experimental:** , aby włączyć eksperymentalny preprocesor. Możesz użyć **/Experimental: preprocesor-** Option, aby jawnie określić tradycyjny preprocesor.

Opcja **/Experimental: preprocesora** jest dostępna w programie Visual Studio 2017 w wersji 15,8.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji** > strony właściwości **wiersza polecenia** **C++ C/**  > .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić **/Experimental: preprocesora** , a następnie wybierz **przycisk OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)
