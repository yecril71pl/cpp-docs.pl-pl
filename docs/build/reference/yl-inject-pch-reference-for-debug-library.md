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
ms.openlocfilehash: 816ba66c94e616407a8891cd149a41e44e29358d
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825720"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Wprowadź odnośnik PCH dla bibliotek debugowania)

Opcja **/yl** generuje unikatowy symbol w prekompilowanym pliku nagłówkowym, a odwołanie do tego symbolu jest wstrzykiwane we wszystkich plikach obiektów, które używają prekompilowanego nagłówka.

## <a name="syntax"></a>Składnia

>**/Yl**\
>**/Yl**_Nazwa_ /yl\
>**/Yl-została**

### <a name="arguments"></a>Argumenty

*Nazwij*<br/>
Opcjonalna nazwa używana jako część unikatowego symbolu.

*\-*<br/>
Łącznik (-) jawnie wyłącza opcję kompilatora **/yl** .

## <a name="remarks"></a>Uwagi

Opcja kompilatora **/yl** tworzy unikatową definicję symbolu w pliku prekompilowanego nagłówka utworzonego przy użyciu opcji [/YC](yc-create-precompiled-header-file.md) . Odwołania do tego symbolu są automatycznie wprowadzane do wszystkich plików, które zawierają prekompilowany nagłówek przy użyciu opcji kompilatora [/Yu](yu-use-precompiled-header-file.md) . Opcja **/yl** jest włączona domyślnie, gdy **/YC** jest używany do tworzenia prekompilowanego pliku nagłówkowego.

Opcja **/Yl**_Nazwa_ /yl służy do tworzenia możliwego do zidentyfikowania symbolu w prekompilowanym pliku nagłówkowym. Kompilator używa argumentu *name* jako części nazwy symbolicznego symbolu, który tworzy, podobnie jak `__@@_PchSym_@00@...@name`, gdzie wielokropek (...) reprezentuje unikatowy, wygenerowany przez kompilator ciąg znaków. Jeśli argument *name* zostanie pominięty, kompilator automatycznie generuje nazwę symbolu. Zwykle nie trzeba znać nazwy symbolu. Jeśli jednak w projekcie jest używany więcej niż jeden prekompilowany plik nagłówkowy, opcja_nazwy_ **/yl**może być przydatna do określenia, które pliki obiektów używają prekompilowanego nagłówka. Możesz użyć *nazwy* jako ciągu wyszukiwania, aby znaleźć odwołanie do symbolu w pliku zrzutu.

**/Yl-została** wyłącza zachowanie domyślne i nie umieszcza symbol identyfikujący w prekompilowanym pliku nagłówkowym. Skompilowane pliki, które zawierają ten prekompilowany nagłówek, nie pobierają wspólnego odwołania do symboli.

Gdy **/YC** nie jest określony, żadna opcja **/yl** nie ma żadnego efektu, ale jeśli określono, musi być zgodna z jakąkolwiek opcją **/yl** przekazaną, gdy określono **/YC** .

Jeśli używasz opcji **/yl-została**, **/YC** i [/Z7](z7-zi-zi-debug-information-format.md) do kompilowania prekompilowanego pliku nagłówkowego, informacje o debugowaniu są przechowywane w pliku obiektu dla pliku źródłowego, który jest używany do tworzenia prekompilowanego nagłówka, a nie do oddzielnego pliku. pdb. Jeśli ten plik obiektu jest następnie częścią biblioteki, [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) błędy lub ostrzeżenia [lnk4206 narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) mogą wystąpić w kompilacjach, które używają tej biblioteki i prekompilowanego pliku nagłówkowego, jeśli plik źródłowy używany do tworzenia prekompilowanego pliku nagłówkowego nie definiuje samych symboli. Konsolidator może wykluczyć plik obiektu z łącza, wraz ze skojarzonymi informacjami o debugowaniu, gdy w komputerze nie ma odwołania do pliku obiektu. Aby rozwiązać ten problem, należy określić **/yl** (lub usunąć opcję **/yl-została** ) w przypadku używania **/YC** do tworzenia prekompilowanego pliku nagłówkowego. Dzięki temu plik obiektu z biblioteki zawierającej informacje debugowania zostanie połączony w kompilacji.

Aby uzyskać więcej informacji na temat prekompilowanych nagłówków, zobacz:

- [/Y (Prekompilowane nagłówki)](y-precompiled-headers.md)

- [Wstępnie skompilowane pliki nagłówkowe](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja** > **wiersza polecenia** **C/C++** > .

1. Dodaj opcję kompilatora_name_ **/yl**w polu **dodatkowe opcje** . Wybierz **przycisk OK** , aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
