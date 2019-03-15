---
title: /FS (Wymuś synchroniczne zapisy do bazy PDB)
ms.date: 11/04/2016
f1_keywords:
- /FS
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
ms.openlocfilehash: 97ffb9529087329cf327ba704523b93d5d9b99b1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817598"
---
# <a name="fs-force-synchronous-pdb-writes"></a>/FS (Wymuś synchroniczne zapisy do bazy PDB)

Wymusza zapisanie pliku bazy danych (PDB) programu — utworzone przez [/zi](z7-zi-zi-debug-information-format.md) lub [/zi](z7-zi-zi-debug-information-format.md)— w celu serializowana za pośrednictwem MSPDBSRV. PLIK EXE.

## <a name="syntax"></a>Składnia

```
/FS
```

## <a name="remarks"></a>Uwagi

Domyślnie gdy **/zi** lub **/zi** jest określony, kompilator blokuje pliki PDB można zapisać informacje o typie i symboliczne informacje debugowania. Może to znacznie zmniejszyć czas kompilatora do generowania informacji o typie, gdy liczba typów jest duży. Jeśli inny proces tymczasowo blokuje plik PDB — na przykład program antywirusowy — operacje zapisu przez kompilator może zakończyć się niepowodzeniem i może wystąpić błąd krytyczny. Ten problem może również się zdarzyć, gdy wiele kopii cl.exe uzyskują dostęp do tego samego pliku PDB — na przykład, jeśli rozwiązanie ma niezależny projektów, które używały tych samych pośredniego katalogi lub wyjścia katalogów i równoległe kompilacje są włączone. **/FS** — opcja kompilatora zabezpiecza kompilator przed zablokowaniem pliku PDB i wymusza przechodzić przez MSPDBSRV. EXE, który serializuje dostępu. Może być znacznie dłuższe kompilacji, a nie uniemożliwia wszystkie błędy, które mogą wystąpić, gdy wiele wystąpień programu cl.exe uzyskują dostęp do pliku PDB w tym samym czasie. Firma Microsoft zaleca, możesz zmienić swoje rozwiązanie, aby projektów niezależnych zapisu do oddzielania pośrednich i lokalizacji danych wyjściowych, lub wprowadzić jeden z projektów zależne od innych kompilacji projektu życie serializacji.

[/MP](mp-build-with-multiple-processes.md) opcji umożliwia **/FS** domyślnie.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **C/C++** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia `/FS` , a następnie wybierz **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
