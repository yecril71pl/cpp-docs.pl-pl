---
title: Błąd narzędzi konsolidatora LNK1211 | Dokumentacja firmy Microsoft
ms.date: 12/05/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1211
dev_langs:
- C++
helpviewer_keywords:
- LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57948556ae7b94b9a1788b7cb4453646b5b504f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1211"></a>Błąd narzędzi konsolidatora LNK1211

> informacje o wstępnie skompilowanym typie nie można odnaleźć; "*filename*" nie został skonsolidowany lub nadpisany

*Filename* pliku obiektu, skompilowanego za pomocą [/Yc](../../build/reference/yc-create-precompiled-header-file.md), nie został określony w poleceniu łącze lub została zastąpiona.

W przypadku tworzenia bibliotek debugowania, która używa prekompilowanych nagłówków i jeśli określisz **/Yc** i [/z7](../../build/reference/z7-zi-zi-debug-information-format.md), Visual C++ generuje plik wstępnie skompilowany obiekt, który zawiera informacje o debugowaniu. Ten błąd występuje tylko gdy plik wstępnie skompilowany obiekt jest przechowywany w bibliotece, korzystanie z biblioteki do tworzenia obrazu wykonywalnego i plików obiektów, do których istnieją odwołania nie mają przechodnie odwołań do żadnej funkcji, który definiuje plik wstępnie skompilowany obiekt.

Istnieją dwie metody, aby uniknąć tej sytuacji:

- Określ [/Yd](../../build/reference/yd-place-debug-information-in-object-file.md) opcję kompilatora, aby dodać informacje o debugowaniu z prekompilowanego nagłówka do każdego obiektu modułu. Ta metoda jest mniej pożądana, ponieważ zazwyczaj generuje modułów dużych obiektów, które można zwiększyć czas wymagany do połączenia aplikacji.

- Określ [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) i podaj nazwę dowolnego ciągu dowolnych, podczas tworzenia pliku prekompilowanego nagłówka, który nie zawiera żadnych definicji funkcji. Dzięki temu kompilatora do tworzenia symbolu w pliku wstępnie skompilowany obiekt i Dodaj odwołanie do tego symbolu w każdym pliku obiektu, który używany prekompilowanego pliku nagłówkowego skojarzonego z plikiem wstępnie skompilowany obiekt.

Podczas kompilowania modułu z **/Yc** i **/Yl**, kompilator tworzy symbol podobny do `__@@_PchSym_@00@...@symbol_name`, gdzie wielokropek (...) reprezentuje ciąg znaków generowane przez kompilator i przechowuje ją w Moduł obiektu. Każdego pliku źródłowego, który kompilacji z tym prekompilowanego nagłówka odwołuje się do określonego symbolu, co powoduje, że konsolidator, aby zawierał obiektu modułu i jego informacje o debugowaniu w bibliotece.
