---
title: /homeparams (Kopiuj parametry rejestru do stosu)
ms.date: 12/17/2018
f1_keywords:
- /homeparams
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
ms.openlocfilehash: a1f9269c7deae6c9ae2e4f198006ad09dd37abc3
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57820666"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams (Kopiuj parametry rejestru do stosu)

Wymusza zapisanie parametrów przekazanych w rejestrach, również będą zapisywane do ich lokalizacji na stosie wejściu do funkcji.

## <a name="syntax"></a>Składnia

> **/ homeparams**

## <a name="remarks"></a>Uwagi

Ta opcja kompilatora jest tylko dostępne w macierzystym i przeznaczonych dla x64 kompilatory —.

X64 konwencji wywoływania wymaga obszar stosu do przydzielenia dla wszystkich parametrów, nawet w przypadku parametrów przekazanych w rejestrach. Aby uzyskać więcej informacji, zobacz [przekazywania parametru](../../build/x64-calling-convention.md#parameter-passing). Domyślnie parametry rejestru nie są kopiowane do miejsca na stosie przydzieloną im w wydawanych wersjach. Utrudnia debugowanie kompilacji wydania zoptymalizowane programu.

W przypadku kompilacji wydania, można użyć **/homeparams** opcję, aby wymusić na kompilatorze skopiuj zarejestrować parametry do stosu, aby upewnić się, że można debugować aplikację. **/ homeparams** pociąga uprzywilejowanych wydajność, ponieważ wymaga dodatkowych cykl, aby załadować Parametry rejestru na stosie.

W kompilacjach do debugowania stos zawsze jest wypełniana parametry przekazywane w rejestrach.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Wpisz opcję kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
