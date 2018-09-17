---
title: -FORCE (Wymuszaj produkt wyjściowy pliku) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
dev_langs:
- C++
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95a746a37183f26585fd013327a964b922589221
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699768"
---
# <a name="force-force-file-output"></a>/FORCE (Wymuszaj produkt wyjściowy pliku)

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>Uwagi

Opcja/Force informuje konsolidator, aby utworzył plik .exe prawidłowe lub biblioteki DLL nawet wtedy, gdy symbolu występują odwołania, ale nie zdefiniowane lub mnożenia zdefiniowane.

Opcja/Force można wykonać opcjonalny argument:

- Użyj /FORCE:MULTIPLE, aby utworzyć plik wyjściowy, czy Konsolidacja znajduje więcej niż jedną definicję symbolu.

- Użyj opcji/Force: UNRESOLVED, aby utworzyć plik wyjściowy, czy Konsolidacja znajdzie Niezdefiniowany symbol. / FORCE: NIEROZPOZNANY jest ignorowana, jeśli symbol punktu wejścia nie został rozwiązany.

/ FORCE bez argumentów oznacza zarówno wielokrotne, nierozwiązany.

Plik utworzony przy użyciu tej opcji może nie działać zgodnie z oczekiwaniami. Konsolidator nie będzie łączyć przyrostowo, jeśli nie określono opcji/Force.

Jeśli moduł został skompilowany z **/CLR**, **/FORCE** nie utworzy obraz.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)