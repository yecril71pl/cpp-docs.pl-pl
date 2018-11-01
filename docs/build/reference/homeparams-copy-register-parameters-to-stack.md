---
title: /homeparams (Kopiuj parametry rejestru do stosu)
ms.date: 11/04/2016
f1_keywords:
- /homeparams
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
ms.openlocfilehash: 952a38d2ab1268ee3dc1fda0899a3ba047281b44
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518459"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams (Kopiuj parametry rejestru do stosu)

Wymusza zapisanie parametrów przekazanych w rejestrach były zapisywane do ich lokalizacji na stosie wejściu do funkcji.

## <a name="syntax"></a>Składnia

```
/homeparams
```

## <a name="remarks"></a>Uwagi

Ta opcja kompilatora jest tylko w przypadku x64 kompilatory (kompilacja natywna i krzyżowa).

Gdy parametry są przekazywane w x64 kompilacji, Konwencje wywoływania wymagają stackspace dla parametrów, nawet w przypadku parametrów przekazanych w rejestrach. Aby uzyskać więcej informacji, zobacz [przekazywania parametru](../../build/parameter-passing.md). Jednak domyślnie kompilację wydania Parametry rejestru nie zostaną zapisane na stosie, do obszaru, który znajduje się już dla parametrów. Utrudnia to debugowanie zoptymalizowanego (wersja) kompilacji programu.

W przypadku kompilacji wydania, użyj **/homeparams** aby upewnić się, że można debugować aplikację. **/ homeparams** pociąga uprzywilejowanych wydajność, ponieważ jest wymagane cyklu załadować Parametry rejestru do stosu.

Do kompilacji debugowanej stos zawsze jest wypełniana parametry przekazywane w rejestrach.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)