---
title: -Zg (Generuj prototypy funkcji) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zg
dev_langs:
- C++
helpviewer_keywords:
- Zg compiler option [C++]
- /Zg compiler option [C++]
- function prototypes, generate function prototypes compiler option
- -Zg compiler option [C++]
- generate function prototypes compiler option
ms.assetid: c8df1b46-24ff-46f2-8356-e0a144b21dd2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27042a66944652508bd9e97110a232175a97233c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724662"
---
# <a name="zg-generate-function-prototypes"></a>/Zg (Generuj prototypy funkcji)

Usuwane. Tworzy prototyp funkcji, dla każdej funkcji, zdefiniowane w pliku źródłowym, ale nie można skompilować pliku źródłowego.

## <a name="syntax"></a>Składnia

```
/Zg
```

## <a name="remarks"></a>Uwagi

Ta opcja kompilatora nie jest już dostępna. Została usunięta w programie Visual C++ 2015. Ta strona pozostaje dla użytkowników starsze wersje programu Visual C++.

Prototyp funkcji zawiera typ zwracany funkcji i listy argumentów typu. Lista typów argumentu jest tworzony na podstawie typów parametrów formalnych w funkcji. Wszystkie prototypy funkcji już istnieje w pliku źródłowym są ignorowane.

Lista prototypy są zapisywane do wyjścia standardowego. Ta lista może się okazać przydatne sprawdzić, czy rzeczywistych argumentów i parametrów formalnych funkcji są zgodne. Aby zapisać listę, należy przekierowywanie standardowe dane wyjściowe do pliku. Następnie można użyć **#include** się na liście prototypy funkcji części pliku źródłowego. To powoduje, że kompilator sprawdza typ argumentu.

Jeśli używasz **/Zg** opcja i program zawiera parametry formalne, które mają struktury, wyliczenia, lub typu złożenia (lub wskaźniki do takich typów), deklaracja każdej struktury, wyliczenia lub typu złożenia musi mieć tag (nazwa). W poniższym przykładzie nazwa tagu jest `MyStruct`.

```C
// Zg_compiler_option.c
// compile with: /Zg
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```

**/Zg** opcji zostało uznane za przestarzałe w programie Visual Studio 2005 i został usunięty w programie Visual Studio 2015. Kompilator języka Visual C++ usunięto obsługę starszych, stylu C kodu. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** w [opcje kompilatora wymienione według kategorii](../../build/reference/compiler-options-listed-by-category.md).

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