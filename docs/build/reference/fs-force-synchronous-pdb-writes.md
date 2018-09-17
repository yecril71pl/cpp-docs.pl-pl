---
title: -FS (Wymuś synchroniczne PDB zapisuje) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FS
dev_langs:
- C++
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b332782cb9bcd929bcd67d4d81b7a7d0259f53cc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714600"
---
# <a name="fs-force-synchronous-pdb-writes"></a>/FS (Wymuś synchroniczne zapisy do bazy PDB)

Wymusza zapisanie pliku bazy danych (PDB) programu — utworzone przez [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) lub [/zi](../../build/reference/z7-zi-zi-debug-information-format.md)— w celu serializowana za pośrednictwem MSPDBSRV. PLIK EXE.

## <a name="syntax"></a>Składnia

```
/FS
```

## <a name="remarks"></a>Uwagi

Domyślnie gdy **/zi** lub **/zi** jest określony, kompilator blokuje pliki PDB można zapisać informacje o typie i symboliczne informacje debugowania. Może to znacznie zmniejszyć czas kompilatora do generowania informacji o typie, gdy liczba typów jest duży. Jeśli inny proces tymczasowo blokuje plik PDB — na przykład program antywirusowy — operacje zapisu przez kompilator może zakończyć się niepowodzeniem i może wystąpić błąd krytyczny. Ten problem może również się zdarzyć, gdy wiele kopii cl.exe uzyskują dostęp do tego samego pliku PDB — na przykład, jeśli rozwiązanie ma niezależny projektów, które używały tych samych pośredniego katalogi lub wyjścia katalogów i równoległe kompilacje są włączone. **/FS** — opcja kompilatora zabezpiecza kompilator przed zablokowaniem pliku PDB i wymusza przechodzić przez MSPDBSRV. EXE, który serializuje dostępu. Może być znacznie dłuższe kompilacji, a nie uniemożliwia wszystkie błędy, które mogą wystąpić, gdy wiele wystąpień programu cl.exe uzyskują dostęp do pliku PDB w tym samym czasie. Firma Microsoft zaleca, możesz zmienić swoje rozwiązanie, aby projektów niezależnych zapisu do oddzielania pośrednich i lokalizacji danych wyjściowych, lub wprowadzić jeden z projektów zależne od innych kompilacji projektu życie serializacji.

[/MP](../../build/reference/mp-build-with-multiple-processes.md) opcji umożliwia **/FS** domyślnie.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **C/C++** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia `/FS` , a następnie wybierz **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)