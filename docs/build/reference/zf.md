---
title: /ZF (szybsze generowanie pliku PDB)
ms.date: 03/29/2018
f1_keywords:
- /Zf
helpviewer_keywords:
- /Zf
- -Zf
ms.openlocfilehash: 2c3f8d08f59c3a6803eda67126ef8a8f9ba6b1fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595743"
---
# <a name="zf-faster-pdb-generation"></a>/ZF (szybsze generowanie pliku PDB)

Włącz szybsze generowanie plików PDB w kompilacjach równoległych, minimalizując wywołania RPC mspdbsrv.exe.

## <a name="syntax"></a>Składnia

> **/Zf**

## <a name="remarks"></a>Uwagi

**/Zf** opcja umożliwia Obsługa szybsze generowanie plików PDB w kompilatorze, korzystając z [/MP (kompilacja z wieloma procesami)](mp-build-with-multiple-processes.md) opcji, lub gdy system kompilacji (na przykład [MSBuild ](/visualstudio/msbuild/msbuild-reference) lub [CMake](../../ide/cmake-tools-for-visual-cpp.md)) może działać wiele cl.exe kompilatora procesów w tym samym czasie. Ta opcja powoduje, że kompilator frontonu opóźnienia generowania indeksów typu dla każdego rekordu typu w pliku PDB aż do zakończenia kompilacji, a następnie żąda je wszystkie w jednym wywołaniu RPC do mspdbsrv.exe dokonywane żądanie RPC dla każdego rekordu. To znacznie zwiększyć przepływność kompilacji dzięki zmniejszeniu obciążenia RPC na temat procesu mspdbsrv.exe w środowisku, w którym wiele procesów kompilator cl.exe uruchamiane jednocześnie.

Ponieważ **/Zf** opcja ma zastosowanie tylko do generowania plików PDB, wymaga [/zi](z7-zi-zi-debug-information-format.md) lub [/zi](z7-zi-zi-debug-information-format.md) opcji.

**/Zf** opcja jest dostępna począwszy od wersji programu Visual Studio 2017 wersja 15.1, gdzie go jest domyślnie wyłączona. Począwszy od programu Visual Studio 2017 w wersji 15.7 3 (wersja zapoznawcza), ta opcja jest domyślnie włączona po **/zi** lub **/zi** opcja jest włączona.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zf** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora w porządku alfabetycznym](compiler-options-listed-alphabetically.md)<br/>
[/MP (Kompilacja z wieloma procesami)](mp-build-with-multiple-processes.md)<br/>
