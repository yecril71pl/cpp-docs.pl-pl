---
title: -Yi (Wstaw Odnośnik PCH dla bibliotek debugowania) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /yl
dev_langs:
- C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a73e79cd50343292ae63dfa831a7638d6444fc64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378473"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Wprowadź odnośnik PCH dla bibliotek debugowania)

**/Yl** opcja generuje unikatowego symbolu w pliku prekompilowanego nagłówka, a odwołania do tego symbolu jest wprowadzonym we wszystkich plikach obiektu, które używają prekompilowanego nagłówka.

## <a name="syntax"></a>Składnia

>**/Yl**  
>**/Yl**_nazwy_  
>**/Yl-**  

### <a name="arguments"></a>Argumenty

*Nazwa*  
Opcjonalna nazwa używana jako część unikatowego symbolu.

*\-*  
Łączniki (-) jawnie wyłącza **/Yl** — opcja kompilatora.

## <a name="remarks"></a>Uwagi

**/Yl** — opcja kompilatora tworzy definicję unikatowego symbolu w pliku prekompilowanego nagłówka, utworzony przy użyciu [/Yc](../../build/reference/yc-create-precompiled-header-file.md) opcji. Odwołania do tego symbolu są automatycznie dodane w wszystkie pliki, które obejmują prekompilowanego nagłówka przy użyciu [/Yu](../../build/reference/yu-use-precompiled-header-file.md) — opcja kompilatora. **/Yl** opcja jest domyślnie włączona po **/Yc** służy do tworzenia prekompilowanego pliku nagłówkowego.

**/Yl**_nazwa_ opcja służy do tworzenia do zidentyfikowania symbol w prekompilowanego pliku nagłówkowego. Kompilator używa *nazwa* argument jako część nazwy symbolu ozdobione tworzy, podobnie jak \_ \_ @@ \_PchSym\_@00@... @ *nazwa*, jeżeli ciąg znaków oznacza wielokropek (...) unikatowego generowane przez kompilator. Jeśli *nazwa* argument zostanie pominięty, kompilator automatycznie generuje nazwę symbolu. Zwykle nie trzeba znać nazwę symbolu. Jednak gdy projektu używa więcej niż jeden plik prekompilowanego nagłówka, **/Yl**_nazwa_ opcja może być przydatne do określenia, który obiekt pliki użycia, które prekompilowanego nagłówka. Można użyć *nazwa* jako ciąg wyszukiwania, aby znaleźć odwołania symboli w pliku zrzutu.

**/Yl-** wyłącza domyślne zachowanie i nie stanowi symbol identyfikujący prekompilowanego pliku nagłówkowego. Skompilowane pliki, które obejmują prekompilowanego nagłówka nie są typowe odwołania symboli.

Gdy **/Yc** nie zostanie określony, wszelkie **/Yl** opcja nie ma znaczenia, ale jeśli określone, musi ona zgodna z żadną **/Yl** opcji przekazywany, gdy **/Yc** jest określona.

Jeśli używasz **/Yl-**, **/Yc** i [/z7](../../build/reference/z7-zi-zi-debug-information-format.md) opcje tworzenia pliku prekompilowanego nagłówka, informacje o debugowaniu są przechowywane w pliku obiektu źródłowego użyty do utworzenia pliku prekompilowanego nagłówka, zamiast pliku .pdb oddzielne. Jeśli ten plik obiektu jest przeprowadzane część biblioteki, [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) błędy lub [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) ostrzeżenia mogą występować w kompilacji korzystających z tej biblioteki i prekompilowanego pliku nagłówkowego, jeśli plik źródłowy użyty do utworzenia prekompilowany plik nagłówka nie definiuje żadnych symboli samej siebie. Konsolidator może wyłączyć pliku obiektu z łącza, oraz skojarzone informacje debugowania, gdy nic w pliku obiektu odwołuje się do klienta biblioteki. Aby rozwiązać ten problem, określ **/Yl** (lub usuń **/Yl-** opcji) korzystając **/Yc** do utworzenia prekompilowanego pliku nagłówkowego. Daje to pewność, że plik obiektu z biblioteki, który zawiera informacje o debugowaniu pobiera połączone w kompilacji.

Aby uzyskać więcej informacji o prekompilowanych nagłówków zobacz:

- [/Y (Prekompilowane nagłówki)](../../build/reference/y-precompiled-headers.md)

- [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Dodaj **/Yl**_nazwa_ w — opcja kompilatora **dodatkowe opcje** pole. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  
