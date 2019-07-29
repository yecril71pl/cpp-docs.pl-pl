---
title: /MANIFESTINPUT (Określ dane wejściowe manifestu)
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: 7b7bd54f98003d9158276fcf75fd61ffb5348585
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606458"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Określ dane wejściowe manifestu)

Określa plik wejściowy manifestu, który ma zostać uwzględniony w manifeście osadzonym w obrazie.

## <a name="syntax"></a>Składnia

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Plik manifestu do uwzględnienia w manifeście osadzonym.

## <a name="remarks"></a>Uwagi

Opcja **/MANIFESTINPUT** określa ścieżkę pliku wejściowego, który ma zostać użyty do utworzenia osadzonego manifestu w obrazie wykonywalnym. Jeśli masz wiele plików wejściowych manifestu, użyj przełącznika wiele razy — jeden raz dla każdego pliku wejściowego. Pliki wejściowe manifestu są scalane w celu utworzenia manifestu osadzonego. Ta opcja wymaga opcji **/manifest: embed** .

Tej opcji nie można ustawić bezpośrednio w programie Visual Studio. Zamiast tego należy użyć właściwości **dodatkowe pliki manifestu** projektu, aby określić dodatkowe pliki manifestu do uwzględnienia. Aby uzyskać więcej informacji, zobacz [stronę właściwości narzędzia manifestu](manifest-tool-property-pages.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
