---
title: -MANIFESTINPUT (Określ dane wejściowe manifestu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5259df2216a8c844123c308ece7ac6b0b650ab39
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705165"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Określ dane wejściowe manifestu)

Określa wejściowy plik manifestu do uwzględnienia w manifeście który jest osadzony w obrazie.

## <a name="syntax"></a>Składnia

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Plik manifestu do uwzględnienia we wbudowanym manifeście.

## <a name="remarks"></a>Uwagi

**/MANIFESTINPUT** opcja określa ścieżkę pliku wejściowego używanego do tworzenia manifestu osadzonego w obrazie wykonywalnym. Jeśli masz wiele plików wejściowych manifestu, należy użyć przełącznika wiele razy — raz dla każdego pliku wejściowego. Pliki wejściowe manifestu są scalane, tworząc manifest wbudowany. Ta opcja wymaga **/MANIFEST: OSADZANIE** opcji.

Tej opcji nie można ustawić bezpośrednio w programie Visual Studio. Zamiast tego należy użyć **dodatkowe pliki manifestu** właściwości projektu, aby określić dodatkowe pliki manifestu do uwzględnienia. Aby uzyskać więcej informacji, zobacz [dane wejściowe i dane wyjściowe, narzędzie manifestu, właściwości konfiguracji \<nazwa_projektu > okno dialogowe strony właściwości](../../ide/input-and-output-manifest-tool.md).

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)