---
title: Błąd narzędzi konsolidatora LNK1211
ms.date: 12/05/2017
f1_keywords:
- LNK1211
helpviewer_keywords:
- LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
ms.openlocfilehash: 7c918cacb87460c2aad30285b750d9b170425534
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242672"
---
# <a name="linker-tools-error-lnk1211"></a>Błąd narzędzi konsolidatora LNK1211

> informacje o wstępnie skompilowanym typie nie znaleziono; "*filename*" nie został skonsolidowany lub nadpisany

*Filename* skompilowane przy użyciu pliku obiektu [/Yc](../../build/reference/yc-create-precompiled-header-file.md), nie został określony w poleceniu łącze lub została zastąpiona.

Jeśli tworzysz bibliotekę debugowania, która używa wstępnie skompilowanych nagłówków, a jeśli określisz **/Yc** i [/z7](../../build/reference/z7-zi-zi-debug-information-format.md), Visual C++ generuje plik wstępnie skompilowanym obiektu, który zawiera informacje o debugowaniu. Ten błąd występuje tylko podczas plik wstępnie skompilowanym obiekt jest przechowywany w bibliotece, korzystanie z biblioteki do tworzenia obrazu wykonywalnego i pliki obiektów, które są wywoływane nie ma przechodnie odwołań do żadnej funkcji, który definiuje plik wstępnie skompilowanym obiektu.

Istnieją dwie metody, aby obejść tę sytuację:

- Określ [/Yd](../../build/reference/yd-place-debug-information-in-object-file.md) opcję kompilatora, aby dodać informacje o debugowaniu z prekompilowanego pliku nagłówkowego do każdego obiektu modułu. Ta metoda jest mniej pożądana, ponieważ zazwyczaj tworzy moduły dużych obiektów, które można wydłużyć czas wymagany do połączenia aplikacji.

- Określ [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) i przekaż nazwę ciągu dowolnego, podczas tworzenia pliku wstępnie skompilowanego nagłówka, który nie zawiera żadnych definicji funkcji. Spowoduje to nieprzekazywanie kompilatora Tworzenie symbolu w pliku obiektu prekompilowanych i emitować odwołanie do tego symbolu w każdym pliku obiektu używanej prekompilowanego pliku nagłówkowego skojarzony z plikiem wstępnie skompilowanych obiektów.

Podczas kompilowania modułu z **/Yc** i **/Yl**, kompilator tworzy symbol podobne do `__@@_PchSym_@00@...@symbol_name`, gdzie wielokropek (...) reprezentuje ciąg znaków generowanych przez kompilator i zapisuje go w Moduł obiektu. Każdego pliku źródłowego, który kompilujesz z prekompilowanego pliku nagłówkowego odnosi się do określonego symbolu, co powoduje, że konsolidator, aby zawierał moduł obiektu i jego informacje debugowania z biblioteki.
