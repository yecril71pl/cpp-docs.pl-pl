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
ms.openlocfilehash: fe76e0d40a2a19a002136a7e095875ad2903d434
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818456"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (Przeszukiwanie manifestu)

Określa zachowanie wyszukiwania plików manifestu.

## <a name="syntax"></a>Składnia

```
/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Uwagi

**/ALLOWISOLATION:No** wskazuje bibliotek DLL ładowanych tak, jakby nie było żadnych manifestu i powoduje, że konsolidator ustawia `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit w opcjonalnym nagłówku `DllCharacteristics` pola.

**/ ALLOWISOLATION** powoduje, że system operacyjny do manifestu, wyszukiwania i obciążeniami.

**/ ALLOWISOLATION** jest ustawieniem domyślnym.

Po wyłączeniu izolacji dla pliku wykonywalnego modułu ładującego Windows nie będzie próbował znaleźć manifest aplikacji do nowo utworzonego procesu. Nowy proces nie będzie domyślny kontekst aktywacji, nawet jeśli dostępny jest manifestu wewnątrz pliku wykonywalnego lub umieszczone w tym samym katalogu co plik wykonywalny o nazwie <em>nazwę pliku wykonywalnego</em>**. exe.manifest**.

Aby uzyskać więcej informacji, zobacz [odwołania plików manifestu](/windows/desktop/SbsCs/manifest-files-reference).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **pliku manifestu** stronę właściwości.

1. Modyfikowanie **Zezwalaj na izolację** właściwości.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
