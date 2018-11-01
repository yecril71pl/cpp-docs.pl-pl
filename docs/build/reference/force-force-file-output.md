---
title: /FORCE (Wymuszaj produkt wyjściowy pliku)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: 5555a76cc792c15bea9c6c393debbd0fb38e30e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445660"
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