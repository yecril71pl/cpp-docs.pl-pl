---
title: -Gs (Kontroluj wywołania sprawdzania stosu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /GS
dev_langs:
- C++
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38b97354408d87d862955c0883c72d3e1459aa61
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719280"
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (Kontroluj wywołania sprawdzania stosu)

Kontroluje sondy stosu.

## <a name="syntax"></a>Składnia

```
/Gs[size]
```

## <a name="arguments"></a>Argumenty

*Rozmiar*<br/>
(Opcjonalnie) Liczba bajtów, które zmienne lokalne mogą zajmować przed sondy stosu jest inicjowana. Jeśli **/GS** opcja jest określona bez `size` argument, jest taka sama, jak określenie **/Gs0**,

## <a name="remarks"></a>Uwagi

Sondy stosu jest sekwencją kodu, który kompilator wstawia w każdym wywołaniu funkcji. Po zainicjowaniu sondy stosu osiągnie benignly do pamięci przez ilość miejsca wymaganego do przechowywania zmiennych lokalnych funkcji.

Jeśli funkcja wymaga więcej niż `size` bajtów stosu miejsca dla zmiennych lokalnych, jego sondy stosu jest inicjowana. Domyślnie kompilator generuje kod, który inicjuje sondy stosu, gdy funkcja wymaga więcej niż jedną stronę obszar stosu. Jest to równoważne opcji kompilatora **/Gs4096** x86, x64 i platform ARM. Ta wartość umożliwia aplikacji i Windows, Menedżer pamięci zwiększyć ilość pamięci przydzielonej do stosu program dynamicznie w czasie wykonywania.

> [!NOTE]
>  Wartość domyślna **/Gs4096** umożliwia stosu program aplikacji dla Windows poprawnie rośnie w czasie wykonywania. Zaleca się, że należy zmieniać wartością domyślną, chyba że wiesz, że dokładnie Dlaczego trzeba go zmienić.

Niektóre programy — na przykład sterowniki urządzeń wirtualnych — ten mechanizm wzrostu stosu domyślnego nie jest wymagana. W takich przypadkach sondy stosu nie są konieczne, i można zatrzymać kompilator generuje je, ustawiając `size` wartości, który jest większy niż dowolnej funkcji, będzie wymagać dla zmiennej lokalnej w pamięci masowej. Nie może być spacji między **/GS** i `size`.

**/ Gs0** uaktywnia sondy stosu za każde wywołanie funkcji, wymagająca magazynu dla zmiennych lokalnych. Może to mieć negatywny wpływ na wydajność.

Możesz włączyć sondy stosu lub wyłączyć za pomocą [check_stack](../../preprocessor/check-stack.md). **/ GS** i `check_stack` pragma nie mają wpływu na standardowe procedury biblioteki C; wpływają na funkcje kompilacji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **C/C++** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)