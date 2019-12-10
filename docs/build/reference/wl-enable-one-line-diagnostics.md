---
title: /WL (Włącz diagnostykę w trybie on-line)
ms.date: 11/04/2016
f1_keywords:
- /wl
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
ms.openlocfilehash: b1ded1cd18eb75ed47b76c1353ad82a7fa497ba9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988567"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (Włącz diagnostykę w trybie on-line)

Dołącza dodatkowe informacje do błędu lub komunikatu ostrzegawczego.

## <a name="syntax"></a>Składnia

```
/WL
```

## <a name="remarks"></a>Uwagi

Do komunikatów o błędach i C++ ostrzeżeniach kompilatora mogą występować dodatkowe informacje, które domyślnie pojawiają się w nowym wierszu. Podczas kompilowania z wiersza polecenia dodatkowy wiersz informacji może być dołączany do komunikatu o błędzie lub ostrzeżenie. Może to być pożądane, jeśli przechwytujesz dane wyjściowe kompilacji do pliku dziennika, a następnie przetworzysz ten dziennik w celu znalezienia wszystkich błędów i ostrzeżeń. Średnik będzie oddzielał błąd lub komunikat ostrzegawczy od dodatkowego wiersza.

Nie wszystkie komunikaty o błędach i ostrzeżeniach zawierają dodatkową linię informacji. Poniższy kod generuje błąd, który zawiera dodatkową linię informacji; umożliwia przetestowanie efektu przy użyciu **/WL**.

```cpp
// compiler_option_WL.cpp
// compile with: /WL
#include <queue>
int main() {
   std::queue<int> q;
   q.fromthecontinuum();   // C2039
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **C/C++**  .

1. Kliknij stronę właściwości **wiersza polecenia** .

1. Wpisz opcję kompilatora w polu **dodatkowe opcje** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
