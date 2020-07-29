---
title: /constexpr (Szacowanie kontrolki constexpr)
ms.date: 08/15/2017
f1_keywords:
- /constexpr
- -constexpr
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
ms.openlocfilehash: 7b3ae1cd732fe1ec234e2734ea4c6fa86db9d5af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223866"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (Szacowanie kontrolki constexpr)

Użyj opcji kompilatora **/constexpr** , aby kontrolować parametry **`constexpr`** oceny w czasie kompilacji.

## <a name="syntax"></a>Składnia

> **/constexpr: Głębokość**<em>N</em>\
> **/constexpr: Śledź**<em>N</em>\
> **/constexpr: kroki**<em>N</em>

## <a name="arguments"></a>Argumenty

**głębokość**<em>n</em> ogranicza głębokość **`constexpr`** wywołania funkcji cyklicznej do poziomu *n* poziomów. Wartość domyślna to 512.

**wyniki śledzenia**<em>n</em> pokazują do *n* **`constexpr`** ocen w diagnostyce. Wartość domyślna to 10.

**kroki**<em>n</em> zakończenie **`constexpr`** oceny po *n* krokach. Wartość domyślna to 100 000.

## <a name="remarks"></a>Uwagi

Opcje kompilatora **/constexpr** kontrolują ocenę czasu kompilowania **`constexpr`** wyrażeń. Kroki oceny, poziomy rekursji i głębokość śledzenia nieprześledzonych są kontrolowane, aby zapobiec wykorzystaniu przez kompilator zbyt dużej ilości czasu na **`constexpr`** ocenę. Aby uzyskać więcej informacji na temat **`constexpr`** elementu języka, zobacz [constexpr (C++)](../../cpp/constexpr-cpp.md).

Opcje **/constexpr** są dostępne począwszy od programu Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu.

2. W obszarze **Właściwości konfiguracji**rozwiń folder **C/C++** i wybierz stronę właściwości **wiersza polecenia** .

3. W polu **dodatkowe opcje** wprowadź wszystkie opcje kompilatora **/constexpr** . Wybierz **przycisk OK** lub **Zastosuj** , aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
