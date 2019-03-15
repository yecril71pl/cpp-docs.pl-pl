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
ms.openlocfilehash: af7962a4b3b5805e7e0c4d59752254c8ade17f7b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814309"
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

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
