---
title: /NOLOGO (Pomiń transparent początkowy) (Konsolidator)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
ms.openlocfilehash: 1b966c1f7af556a85aadcafaa8ed43da5b3f75df
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422159"
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO (Pomiń transparent początkowy) (Konsolidator)

```
/NOLOGO
```

## <a name="remarks"></a>Uwagi

Opcja/nologo uniemożliwia wyświetlanie liczby o prawach autorskich komunikat i wersji.

Ta opcja powoduje również pominięcie wyświetlania pliku polecenia. Aby uzyskać więcej informacji, zobacz [pliki poleceń LINK](../../build/reference/link-command-files.md).

Domyślnie te informacje są wysyłane przez konsolidator, aby w oknie danych wyjściowych. W wierszu polecenia jest wysyłane do wyjścia standardowego i mogą zostać przekierowane do pliku.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Ta opcja powinna być używana tylko z poziomu wiersza polecenia.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Nie można zmienić tę opcję konsolidatora w programowo.

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)
