---
title: /MANIFESTINPUT (Określ dane wejściowe manifestu)
ms.date: 11/04/2016
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: bf192664a7a2402b06621167d91dff67ce0741a9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814229"
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

Tej opcji nie można ustawić bezpośrednio w programie Visual Studio. Zamiast tego należy użyć **dodatkowe pliki manifestu** właściwości projektu, aby określić dodatkowe pliki manifestu do uwzględnienia. Aby uzyskać więcej informacji, zobacz [dane wejściowe i dane wyjściowe, narzędzie manifestu, właściwości konfiguracji \<nazwa_projektu > okno dialogowe strony właściwości](input-and-output-manifest-tool.md).

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
