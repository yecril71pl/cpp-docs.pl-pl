---
title: /vd (Wyłącz przemieszczanie konstrukcji)
ms.date: 11/04/2016
f1_keywords:
- /vd
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
ms.openlocfilehash: df8891cc71dd5a4cfd417969578c0c1b46ae3be3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223814"
---
# <a name="vd-disable-construction-displacements"></a>/vd (Wyłącz przemieszczanie konstrukcji)

## <a name="syntax"></a>Składnia

```
/vdn
```

## <a name="arguments"></a>Argumenty

**0**<br/>
Pomija element członkowski przemieszczenia konstruktora vtordisp/destruktora. Wybierz tę opcję tylko wtedy, gdy masz pewność, że wszystkie konstruktory klas i destruktory wywołują funkcje wirtualne praktycznie.

**1**<br/>
Umożliwia utworzenie ukrytego elementu członkowskiego przemieszczenia konstruktora vtordisp/destruktora. Jest to opcja domyślna.

**2**<br/>
Umożliwia użycie [operatora dynamic_cast](../../cpp/dynamic-cast-operator.md) dla konstruowanego obiektu. Na przykład dynamic_cast z wirtualnej klasy bazowej do klasy pochodnej.

**/VD2 zmieni** dodaje pole vtordisp, gdy istnieje Wirtualna baza z funkcjami wirtualnymi. **/vd1** powinny być wystarczające. Najbardziej typowym przypadkiem, gdzie **/VD2 zmieni** jest konieczność, gdy jedyną funkcją wirtualną w wirtualnej bazie danych jest destruktor.

## <a name="remarks"></a>Uwagi

Te opcje mają zastosowanie tylko do kodu C++, który używa wirtualnych baz.

Visual C++ implementuje obsługę przemieszczeń konstrukcyjnych C++ w sytuacjach, w których jest używane Dziedziczenie wirtualne. Przemieszczanie konstrukcji rozwiązuje problem utworzony, gdy funkcja wirtualna, zadeklarowana w wirtualnej bazie i zastąpiona w klasie pochodnej, jest wywoływana z konstruktora podczas konstruowania klasy pochodnej.

Problem polega na tym, że funkcja wirtualna może zostać przeniesiona do nieprawidłowego **`this`** wskaźnika w wyniku rozbieżności między przemieszczeniami do wirtualnych baz klas i przemieszczeniami do klas pochodnych. Rozwiązanie zapewnia jednolite przemieszczenie konstrukcji o nazwie vtordisp pole dla każdej wirtualnej bazy klasy.

Domyślnie pola vtordisp są wprowadzane za każdym razem, gdy kod definiuje konstruktory i destruktory zdefiniowane przez użytkownika, a także przesłania funkcje wirtualne baz wirtualnych.

Te opcje mają wpływ na całe pliki źródłowe. Użyj [vtordisp](../../preprocessor/vtordisp.md) , aby pominąć i ponownie włączyć pola vtordisp w oparciu o klasę klasy.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **C/C++** .

1. Kliknij stronę właściwości **wiersza polecenia** .

1. Wpisz opcję kompilatora w polu **dodatkowe opcje** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
