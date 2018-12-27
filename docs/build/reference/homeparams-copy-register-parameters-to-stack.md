---
title: /homeparams (Kopiuj parametry rejestru do stosu)
ms.date: 12/17/2018
f1_keywords:
- /homeparams
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
ms.openlocfilehash: ffb5ca602feb7a369bb31d0277834786d66ac12a
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627482"
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

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Otwórz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Wpisz opcję kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)