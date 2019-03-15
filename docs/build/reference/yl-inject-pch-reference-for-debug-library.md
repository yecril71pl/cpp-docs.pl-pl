---
title: /Yl (Wprowadź odnośnik PCH dla bibliotek debugowania)
ms.date: 01/29/2018
f1_keywords:
- /yl
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
ms.openlocfilehash: 92e47836e0fdae077defa0fe35b515ab4ca20a66
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810292"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Wprowadź odnośnik PCH dla bibliotek debugowania)

**/Yl** opcja powoduje wygenerowanie unikatowego symbolu w pliku wstępnie skompilowanego nagłówka i odwołania do tego symbolu są wstrzykiwane we wszystkich plikach obiektu, korzystających z prekompilowanego pliku nagłówkowego.

## <a name="syntax"></a>Składnia

>**/Yl**
> **/Yl**_nazwa_
> **/Yl-**

### <a name="arguments"></a>Argumenty

*Nazwa*<br/>
Opcjonalna nazwa używana jako część unikatowy symbol.

*\-*<br/>
Łączniki (-) wyraźnie wyłącza **/Yl** — opcja kompilatora.

## <a name="remarks"></a>Uwagi

**/Yl** — opcja kompilatora tworzy definicję unikatowego symbolu w pliku wstępnie skompilowanego nagłówka utworzone za pomocą [/Yc](yc-create-precompiled-header-file.md) opcji. Odwołania do tego symbolu są automatycznie wstrzykiwane we wszystkich plikach, które zawierają prekompilowany plik nagłówkowy przy użyciu [/Yu](yu-use-precompiled-header-file.md) — opcja kompilatora. **/Yl** opcja jest domyślnie włączona, gdy **/Yc** służy do tworzenia prekompilowanego pliku nagłówkowego.

**/Yl**_nazwa_ opcja służy do utworzenia do zidentyfikowania symboli w pliku wstępnie skompilowanego nagłówka. Kompilator używa *nazwa* jako część nazwy dekoracyjne symbol argument, tworzy, podobnie jak `__@@_PchSym_@00@...@name`, jeżeli ciąg znaków reprezentuje przycisk wielokropka (...), unikatową generowanych przez kompilator. Jeśli *nazwa* argument zostanie pominięty, kompilator automatycznie generuje nazwę symbolu. Zwykle nie trzeba znać nazwę symbolu. Jednak gdy projekt korzysta z więcej niż jeden plik prekompilowanego pliku nagłówkowego, **/Yl**_nazwa_ opcja może być przydatne na potrzeby określania, który obiekt pliki użycia, które prekompilowanego nagłówka. Możesz użyć *nazwa* jako ciąg wyszukiwania, aby znaleźć odwołanie do symbolu w pliku zrzutu.

**/Yl-** wyłącza domyślne zachowanie i nie umieścić symbol identyfikujący w pliku wstępnie skompilowanego nagłówka. Skompilowane pliki, które obejmują prekompilowanego pliku nagłówkowego nie są typowe odwołanie do symbolu.

Podczas **/Yc** nie zostanie określony, wszystkie **/Yl** opcja nie obowiązuje, ale jeśli określony, musi on być zgodny dowolne **/Yl** opcji przekazywany, gdy **/Yc** jest określona.

Jeśli używasz **/Yl-**, **/Yc** i [/z7](z7-zi-zi-debug-information-format.md) sposoby tworzenia prekompilowanego pliku nagłówkowego, informacje o debugowaniu są przechowywane w pliku obiektu dla pliku źródłowego, użyty do utworzenia prekompilowany plik nagłówkowy, a nie pliku .pdb oddzielne. Jeśli ten plik obiektu jest podejmowana częścią biblioteki [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) błędy lub [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) ostrzeżenia może wystąpić w kompilacjach, które używają tej biblioteki i prekompilowanego pliku nagłówkowego, jeśli plik źródłowy użyty do utworzenia prekompilowany plik nagłówka nie definiuje żadnych symboli sam. Konsolidator może wyłączyć pliku obiektu z łącza, oraz skojarzone informacje debugowania, gdy żadne postanowienie w pliku obiektu nie odwołuje się do klienta biblioteki. Aby rozwiązać ten problem, należy określić **/Yl** (lub usunąć **/Yl-** opcja) zastosowania **/Yc** można utworzyć pliku wstępnie skompilowanego nagłówka. Daje to gwarancję, że plik obiektu z biblioteki, który zawiera informacje o debugowaniu łączony w kompilacji.

Aby uzyskać więcej informacji na temat wstępnie skompilowanych nagłówków zobacz:

- [/Y (Prekompilowane nagłówki)](y-precompiled-headers.md)

- [Prekompilowane pliki nagłówka](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Dodaj **/Yl**_nazwa_ w — opcja kompilatora **dodatkowe opcje** pole. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
