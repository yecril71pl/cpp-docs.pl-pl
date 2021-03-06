---
title: /Zg (Generuj prototypy funkcji)
ms.date: 11/04/2016
f1_keywords:
- /zg
helpviewer_keywords:
- Zg compiler option [C++]
- /Zg compiler option [C++]
- function prototypes, generate function prototypes compiler option
- -Zg compiler option [C++]
- generate function prototypes compiler option
ms.assetid: c8df1b46-24ff-46f2-8356-e0a144b21dd2
ms.openlocfilehash: 591460b78a461aa2e33f873b79d6dcec0277f99f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446198"
---
# <a name="zg-generate-function-prototypes"></a>/Zg (Generuj prototypy funkcji)

Usuwane. Tworzy prototyp funkcji, dla każdej funkcji, zdefiniowane w pliku źródłowym, ale nie można skompilować pliku źródłowego.

## <a name="syntax"></a>Składnia

```
/Zg
```

## <a name="remarks"></a>Uwagi

Ta opcja kompilatora nie jest już dostępna. Została usunięta w programie Visual Studio 2015. Ta strona pozostaje przez użytkowników starszych wersji programu Visual Studio.

Prototyp funkcji zawiera typ zwracany funkcji i listy argumentów typu. Lista typów argumentu jest tworzony na podstawie typów parametrów formalnych w funkcji. Wszystkie prototypy funkcji już istnieje w pliku źródłowym są ignorowane.

Lista prototypy są zapisywane do wyjścia standardowego. Ta lista może się okazać przydatne sprawdzić, czy rzeczywistych argumentów i parametrów formalnych funkcji są zgodne. Aby zapisać listę, należy przekierowywanie standardowe dane wyjściowe do pliku. Następnie można użyć **#include** się na liście prototypy funkcji części pliku źródłowego. To powoduje, że kompilator sprawdza typ argumentu.

Jeśli używasz **/Zg** opcja i program zawiera parametry formalne, które mają struktury, wyliczenia, lub typu złożenia (lub wskaźniki do takich typów), deklaracja każdej struktury, wyliczenia lub typu złożenia musi mieć tag (nazwa). W poniższym przykładzie nazwa tagu jest `MyStruct`.

```C
// Zg_compiler_option.c
// compile with: /Zg
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```

**/Zg** opcji zostało uznane za przestarzałe w programie Visual Studio 2005 i został usunięty w programie Visual Studio 2015. Za pomocą kompilatora MSVC usunięto obsługę starszych, stylu C kodu. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** w [opcje kompilatora wymienione według kategorii](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
