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
ms.openlocfilehash: 2d2f3c1c7bac19fc0e401067f43e78e3770c6304
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428161"
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

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)