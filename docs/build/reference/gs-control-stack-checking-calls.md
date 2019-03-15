---
title: /Gs (Kontroluj wywołania sprawdzania stosu)
ms.date: 10/25/2018
f1_keywords:
- /GS
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
ms.openlocfilehash: e31b42c1d9422d44c5f106f40c4a60a38f23425b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818570"
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (Kontroluj wywołania sprawdzania stosu)

Określa próg sondy stosu.

## <a name="syntax"></a>Składnia

> **/ GS**[*rozmiar*]

## <a name="arguments"></a>Argumenty

*Rozmiar*<br/>
(Opcjonalnie) Liczba bajtów, które zmienne lokalne mogą zajmować przed sondy stosu jest inicjowana. Nie może być spacji między **/GS** i *rozmiar*.

## <a name="remarks"></a>Uwagi

A *sondy stosu* jest sekwencją kod, który kompilator wstawia na początku wywołania funkcji. Po zainicjowaniu sondy stosu osiągnie benignly do pamięci przez ilość miejsca wymaganego do przechowywania zmiennych lokalnych funkcji. To powoduje, że przezroczysty strony w pamięci stosu dodatkowe, jeśli jest to wymagane, przed uruchomieniem pozostałych funkcji systemu operacyjnego.

Domyślnie kompilator generuje kod, który inicjuje sondy stosu, gdy funkcja wymaga więcej niż jedną stronę obszar stosu. Jest to równoważne opcji kompilatora **/Gs4096** dla x86 x 64, ARM, ARM64 platformy i. Ta wartość umożliwia aplikacji i Windows, Menedżer pamięci zwiększyć ilość pamięci przydzielonej do stosu program dynamicznie w czasie wykonywania.

> [!NOTE]
> Wartość domyślna **/Gs4096** umożliwia stosu program aplikacji dla Windows poprawnie rośnie w czasie wykonywania. Zaleca się, że należy zmieniać wartością domyślną, chyba że wiesz, że dokładnie Dlaczego trzeba go zmienić.

Niektóre programy — na przykład sterowniki urządzeń wirtualnych — ten mechanizm wzrostu stosu domyślnego nie jest wymagana. W takich przypadkach sondy stosu nie są konieczne, i można zatrzymać kompilator generuje je, ustawiając *rozmiar* wartości, który jest większy niż dowolnej funkcji, będzie wymagać dla zmiennej lokalnej w pamięci masowej.

**/ Gs0** inicjuje stosu sondy za każde wywołanie funkcji, wymagająca magazynu dla zmiennych lokalnych. Może to mieć negatywny wpływ na wydajność.

X64 jest przeznaczony dla, jeśli **/GS** opcja jest określona bez *rozmiar* argument, jest taka sama jak **/Gs0**. Jeśli *rozmiar* argument ma wartość 1 do 9, ostrzeżenie D9014 jest emitowane i efekt jest taki sam jak określanie **/Gs0**.

Dla x86, ARM, ARM64 cele i **/GS** opcji bez *rozmiar* argument jest taka sama jak **/Gs4096**. Jeśli *rozmiar* argument ma wartość 1 do 9, ostrzeżenie D9014 jest emitowane i efekt jest taki sam jak określanie **/Gs4096**.

Dla wszystkich obiektów docelowych *rozmiar* argument od 10 do 2147485647 ustawiające próg na wartość na określoną wartość. A *rozmiar* 2147485648 lub nowszej przyczyny błędu krytyczny C1049.

Możesz włączyć sondy stosu lub wyłączyć za pomocą [check_stack](../../preprocessor/check-stack.md) dyrektywy. **/ GS** i `check_stack` pragma nie mają wpływu na standardowe procedury biblioteki C; wpływają na funkcje kompilacji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Wprowadź **/GS** — opcja kompilatora i opcjonalny rozmiar w **dodatkowe opcje**. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
