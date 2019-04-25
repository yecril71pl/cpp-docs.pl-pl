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
ms.openlocfilehash: 178acc548fb9c89dcfde104d2a12d85637440e28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294255"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (Szacowanie kontrolki constexpr)

Użyj **/constexpr** opcje kompilatora sterowania parametrami dla **constexpr** oceny w czasie kompilacji.

## <a name="syntax"></a>Składnia

> **/ constexpr: DEPTH**<em>N</em>
>  **/constexpr: backtrace**<em>N</em>
> ** /constexpr: Steps**<em>N</em>

## <a name="arguments"></a>Argumenty

**głębokość**<em>N</em> Limit głębokości cyklicznego **constexpr** wywołania do funkcji *N* poziomów. Wartość domyślna to 512.

**backtrace**<em>N</em> Pokaż maksymalnie *N* **constexpr** ocen w diagnostyce. Wartość domyślna wynosi 10.

**kroki**<em>N</em> Zakończ **constexpr** szacowania po *N* kroki. Wartość domyślna to 100 000.

## <a name="remarks"></a>Uwagi

**/Constexpr** opcje kompilatora kontrolować obliczania kompilacji **constexpr** wyrażenia. Kroki oceny, poziom rekursji i głębi backtrace są kontrolowane można uniemożliwić kompilatorowi zbyt dużo czasu podstawą przedstawiają analizę wydatków **constexpr** oceny. Aby uzyskać więcej informacji na temat **constexpr** elementu języka, zobacz [constexpr (C++)](../../cpp/constexpr-cpp.md).

**/Constexpr** opcje są dostępne począwszy od wersji programu Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz swój projekt **stron właściwości** okno dialogowe.

2. W obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** folder i wybierz polecenie **wiersza polecenia** stronę właściwości.

3. Wprowadź dowolne **/constexpr** kompilatora opcji na liście **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
