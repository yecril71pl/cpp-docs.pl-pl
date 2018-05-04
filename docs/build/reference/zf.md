---
title: /ZF (Generowanie szybciej PDB) | Dokumentacja firmy Microsoft
ms.date: 03/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zf
dev_langs:
- C++
helpviewer_keywords:
- /Zf
- -Zf
author: corob-msft
ms.author: corob
ms.openlocfilehash: 968ce17302fa608888c7ae2fedf695946b0119bd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="zf-faster-pdb-generation"></a>/ZF (Generowanie szybciej PDB)

Włącz szybsze generowania plików PDB w kompilacjach równoległych minimalizując mspdbsrv.exe wywołania RPC.

## <a name="syntax"></a>Składnia

> **/Zf**

## <a name="remarks"></a>Uwagi

**/Zf** opcja umożliwia Obsługa szybsze generowania plików PDB, korzystając z [/MP (kompilacja z wieloma procesami)](mp-build-with-multiple-processes.md) opcji, lub gdy system kompilacji (na przykład [MSBuild ](/visualstudio/msbuild/msbuild-reference) lub [CMake](../../ide/cmake-tools-for-visual-cpp.md)) może działać wiele cl.exe kompilatora procesy w tym samym czasie. Ta opcja powoduje, że kompilator frontonu opóźnienia generowania indeksów typu dla każdego typu rekordu w pliku PDB aż do zakończenia kompilacji, a następnie ich żądań w jednym wywołania RPC mspdbsrv.exe zamiast wysłał żądanie RPC dla każdego rekordu. To znacznie zwiększyć przepływność kompilacji przez zmniejszenie obciążenia RPC w procesie mspdbsrv.exe w środowisku, w której wiele procesów kompilatora cl.exe działać jednocześnie.

Ponieważ **/Zf** opcja ma zastosowanie tylko do generowania plików PDB, wymaga [/zi](z7-zi-zi-debug-information-format.md) lub [/zi](z7-zi-zi-debug-information-format.md) opcji.

**/Zf** opcja jest dostępne począwszy od wersji programu Visual Studio 2017 wersji 15.1, gdzie ona jest domyślnie wyłączone. W programie Visual Studio 2017 15.7 w wersji Preview 3, ta opcja jest domyślnie włączona po **/zi** lub **/zi** opcja jest włączona.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Zf** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora w porządku alfabetycznym](compiler-options-listed-alphabetically.md)<br/>
[/MP (Kompilacja z wieloma procesami)](mp-build-with-multiple-processes.md)<br/>
