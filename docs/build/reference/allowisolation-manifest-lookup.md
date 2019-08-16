---
title: /ALLOWISOLATION (Przeszukiwanie manifestu)
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
ms.openlocfilehash: 7c799f3d44428643bccc2869255ffa4e9d194d70
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493136"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (Przeszukiwanie manifestu)

Określa zachowanie wyszukiwania manifestu.

## <a name="syntax"></a>Składnia

```
/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Uwagi

**/ALLOWISOLATION: nie** wskazuje, że biblioteki DLL są załadowane tak, jakby nie było żadnego manifestu i powodują `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` , że konsolidator ustawi bit w `DllCharacteristics` polu opcjonalnego nagłówka.

**/ALLOWISOLATION** powoduje, że system operacyjny przeszukiwanie i ładowanie manifestu.

Wartość domyślna to **/ALLOWISOLATION** .

Gdy izolacja jest wyłączona dla pliku wykonywalnego, moduł ładujący systemu Windows nie będzie podejmować próby znalezienia manifestu aplikacji dla nowo utworzonego procesu. Nowy proces nie będzie miał domyślnego kontekstu aktywacji, nawet jeśli w pliku wykonywalnym lub umieszczonym w tym samym katalogu, w którym znajduje się plik wykonywalny o nazwie <em>Executable-Name</em> **. exe. manifest**.

Aby uzyskać więcej informacji, zobacz [Dokumentacja plików manifestu](/windows/win32/SbsCs/manifest-files-reference).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz pozycję **Właściwości** > konfiguracji Strona właściwości**pliku manifestu** **konsolidatora** > .

1. Zmodyfikuj właściwość **Zezwalaj na izolację** .

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
