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
ms.openlocfilehash: c0d5110615f66dcf4f7dc170d89ee58c2e8fa5cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316538"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (Włącz diagnostykę w trybie on-line)

Dołącza informacje dodatkowe błąd lub ostrzeżenie.

## <a name="syntax"></a>Składnia

```
/WL
```

## <a name="remarks"></a>Uwagi

Błędach i komunikaty ostrzegawcze z kompilatora C++ może następować dodatkowe informacje, na wyświetlonej domyślnie w nowym wierszu. Podczas kompilowania z wiersza polecenia wiersz dodatkowych informacji, można dołączyć do błędu lub komunikat ostrzegawczy. Może to być pożądane, jeśli Przechwyć dane wyjściowe kompilacji do pliku dziennika, a następnie przetworzyć tego dziennika, aby znaleźć wszystkie błędy i ostrzeżenia. Średnik będzie oddzielić błędu lub ostrzeżenia, od dodatkowy wiersz.

Nie wszystkie komunikaty o błędach i ostrzeżenia mają dodatkowy wiersz informacji. Poniższy kod zostanie wygenerowany błąd, który ma dodatkowy wiersz informacji. będzie można sprawdzić efekt, gdy używasz **/WL**.

```
// compiler_option_WL.cpp
// compile with: /WL
#include <queue>
int main() {
   std::queue<int> q;
   q.fromthecontinuum();   // C2039
}
```

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
