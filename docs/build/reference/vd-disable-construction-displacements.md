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
ms.openlocfilehash: 229306fe93dedcf5c87d53e2227c8f17baef07c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652962"
---
# <a name="vd-disable-construction-displacements"></a>/vd (Wyłącz przemieszczanie konstrukcji)

## <a name="syntax"></a>Składnia

```
/vdn
```

## <a name="arguments"></a>Argumenty

**0**<br/>
Pomija elementu członkowskiego przemieszczenia konstruktora/destruktora vtordisp. Wybierz tę opcję tylko wtedy, gdy masz pewność, wszystkie konstruktory i destruktory klas wywołanie wirtualnej działa praktycznie.

**1**<br/>
Umożliwia tworzenie elementów członkowskich przemieszczenia konstruktora/destruktora vtordisp ukryte. Ten wybór jest ustawieniem domyślnym.

**2**<br/>
Pozwala na używanie [dynamic_cast Operator](../../cpp/dynamic-cast-operator.md) na obiekcie, który jest konstruowany. Na przykład dynamic_cast z wirtualnej klasy bazowej do klasy pochodnej.

**/ vd2** dodaje pole vtordisp, gdy baza wirtualna z funkcjami wirtualnymi. **/ vd1** powinny być wystarczające. Najczęściej zamierzone, gdzie **/vd2** jest niezbędne jest, gdy funkcja tylko wirtualna w sieci wirtualnej podstawowym destruktora.

## <a name="remarks"></a>Uwagi

Te opcje są stosowane tylko dla kodu C++, który korzysta z baz wirtualnych.

Visual C++ implementuje obsługi przemieszczenia konstrukcji języka C++ w sytuacjach, gdzie używane jest wirtualne dziedziczenie. Przemieszczanie konstrukcji rozwiązać problem utworzony, jeśli funkcja wirtualna, zadeklarowanej w wirtualnej podstawowej i przesłonięcia w klasie pochodnej, jest wywoływana z konstruktora podczas konstruowania dalsze klasę pochodną.

Problem polega na to, czy funkcja wirtualna może być przekazywane do nieprawidłowych `this` wskaźnika w wyniku rozbieżności między przemieszczanie do wirtualnego podstaw klasę i przemieszczanie się jej klas pochodnych. Rozwiązanie udostępnia dostosowanie przemieszczenia pojedynczego konstrukcji, dla każdego wirtualnego podstawy klasę o nazwie polem vtordisp.

Domyślnie vtordisp — pola zostały wprowadzone, zawsze wtedy, gdy kod definiuje zdefiniowanych przez użytkownika konstruktorów i destruktorów i zastępuje również funkcji wirtualnych z bazami wirtualnymi.

Te opcje dotyczą całych plików źródłowych. Użyj [vtordisp](../../preprocessor/vtordisp.md) do pominięcia i ponownego włączenia pól vtordisp działające na zasadzie klasa po klasie.

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