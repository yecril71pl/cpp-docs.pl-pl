---
title: /MANIFESTINPUT (Określ dane wejściowe manifestu)
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: d7c8351c915f5666ada9939df686c81c86ab89ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337513"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Określ dane wejściowe manifestu)

Określa plik wejściowy manifestu do uwzględnienia w manifeście, który jest osadzony w obrazie.

## <a name="syntax"></a>Składnia

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>Parametry

*Pod nazwą*<br/>
Plik manifestu do uwzględnienia w osadzonym manifeście.

## <a name="remarks"></a>Uwagi

Opcja **/MANIFESTINPUT** określa ścieżkę pliku wejściowego, który ma być używany do tworzenia osadzonego manifestu w obrazie wykonywalnym. Jeśli masz wiele plików wejściowych manifestu, użyj przełącznika wiele razy — raz dla każdego pliku wejściowego. Pliki wejściowe manifestu są scalane w celu utworzenia osadzonego manifestu. Ta opcja wymaga opcji **/MANIFEST:EMBED.**

Tej opcji nie można ustawić bezpośrednio w programie Visual Studio. Zamiast tego należy użyć **właściwości Dodatkowe pliki manifestu** projektu, aby określić dodatkowe pliki manifestu do uwzględnienia. Aby uzyskać więcej informacji, zobacz [Manifest Tool Property Pages](manifest-tool-property-pages.md).

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
