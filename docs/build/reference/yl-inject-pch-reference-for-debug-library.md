---
title: "-Yi (Wstaw Odnośnik PCH dla bibliotek debugowania) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /yl
dev_langs: C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6e777977f6d869d2bbc28d980f6445851e54396b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Wprowadź odnośnik PCH dla bibliotek debugowania)

**/Yl** opcja tworzy wspólny symbol dla prekompilowanego pliku nagłówkowego i injects odwołania do tego symbolu we wszystkich plikach, które używają prekompilowanego nagłówka. Dzięki temu pełne informacje dotyczące symboli prekompilowanego nagłówka dostępne do debugera we wszystkich plikach, które używają prekompilowanego nagłówka. Ta opcja jest domyślnie włączona. Użycie tej opcji może uniemożliwić błędy konsolidatora ze względu na Brak informacji o debugowaniu w bibliotekach połączone, które używają prekompilowanych nagłówków.

## <a name="syntax"></a>Składnia

>**/Yl**  
>**/Yl**_nazwy_  
>**/Yl-**  

### <a name="arguments"></a>Argumenty

*Nazwa*  
Opcjonalna nazwa używane do definiowania symboli jako pliki przechowywane i zawartymi w obiekcie zdefiniuj lub użyj prekompilowanego nagłówka.

*\-*  
Łączniki (-) jawnie wyłącza **/Yl** — opcja kompilatora.

## <a name="remarks"></a>Uwagi

**/Yl** opcja umożliwia włączenie debugera uzyskać pełne informacje na temat typów w prekompilowanego nagłówka w każdym pliku, który zawiera prekompilowanego nagłówka. Ta opcja tworzy nazwę symbolu wewnętrznego, injects definicji symbolu w pliku obiektu użyty do utworzenia prekompilowanego nagłówka przez [/Yc](../../build/reference/yc-create-precompiled-header-file.md) opcji i injects odwołanie do symbolu we wszystkich plikach zawierających wstępnie skompilowanych Nagłówek przy użyciu [/Yu](../../build/reference/yu-use-precompiled-header-file.md) — opcja kompilatora. Ponieważ wszystkich plików źródłowych, które używają prekompilowany nagłówek odwoływać się do nazwanych symbolu, konsolidator zawsze łączy plik obiektu, w którym zdefiniowano symbolu i skojarzone prekompilowanego nagłówka, informacje o debugowaniu. Ta opcja jest domyślnie włączona.

**/Yl**_nazwa_ jest używana opcja można jawnie utworzyć identyfikujące symbol dla prekompilowanego pliku nagłówkowego. Kompilator używa *nazwa* argument tworzenie podobny do symbolu \_ \_ @@ \_PchSym\_@00@... @*nazwy* , gdzie ciąg znaków oznacza generowanych przez konsolidator wielokropek (...). Jeśli argument zostanie pominięty, kompilator automatycznie generuje nazwę symbolu.

**/Yl-** wyłącza domyślne zachowanie i przesyłają identyfikujące odwołania symboli w plikach obiektu, które obejmują prekompilowanego nagłówka. Ta opcja może być wymagane dla plików skompilowany bez prekompilowanego pliku nagłówkowego obecny.

Jeśli używasz **/Yl-**, **/Yc** i [/z7](../../build/reference/z7-zi-zi-debug-information-format.md) opcje do tworzenia biblioteki, kompilator tworzy plik prekompilowanego nagłówka, który zawiera informacje o debugowaniu, który jest przechowywany w Plik obiektu zamiast pliku PDB. [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) błędy lub [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) ostrzeżenia mogą występować w kompilacji korzystających z tej biblioteki i prekompilowanego nagłówka, jeśli plik źródłowy użyty do utworzenia prekompilowanego nagłówka nie definiuje żadnych symboli. Konsolidator mogą wyłączyć ten plik obiekt bibliotece z łącza, oraz informacje o debugowaniu skojarzone prekompilowanego nagłówka, gdy nic w pliku obiektu odwołuje się do klienta biblioteki. Aby rozwiązać ten problem, określ **/Yl** korzystając **/Yc** do utworzenia prekompilowanego pliku nagłówkowego i **/Yu** z niego korzystać. Daje to pewność, że plik obiektu, który zawiera informacje o debugowaniu jest uwzględniony w kompilacji.

Aby uzyskać więcej informacji o prekompilowanych nagłówków zobacz:

- [/Y (prekompilowane nagłówki)](../../build/reference/y-precompiled-headers.md)

- [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **wiersza polecenia** stronę właściwości w **C/C++** folderu.

1. Dodaj **/Yl**_nazwa_ w — opcja kompilatora **dodatkowe opcje** pole. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  
