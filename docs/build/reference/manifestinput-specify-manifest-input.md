---
title: /MANIFESTINPUT (Określ dane wejściowe manifestu)
ms.date: 11/04/2016
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: 30e0d4b71943dec8e0efe9112caf7cdf57f66809
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442695"
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