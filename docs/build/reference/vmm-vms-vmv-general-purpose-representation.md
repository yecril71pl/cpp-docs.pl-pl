---
title: / VMM, - vms, - vmv (ogólna reprezentacja celu)
ms.date: 11/04/2016
f1_keywords:
- /vms
- /vmm
- /vmv
helpviewer_keywords:
- Virtual Inheritance compiler option
- general purpose representation compiler options
- vms compiler option [C++]
- vmm compiler option [C++]
- /vmm compiler option [C++]
- -vmm compiler option [C++]
- -vms compiler option [C++]
- /vms compiler option [C++]
- vmv compiler option [C++]
- /vmv compiler option [C++]
- Single Inheritance compiler option
- -vmv compiler option [C++]
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
ms.openlocfilehash: 7a46cecdbf96ad891ce218df4769a60590e562a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316733"
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm, /vms, /vmv (Ogólna reprezentacja celu)

Używany podczas [/vmb, / vmg (metoda reprezentacji)](vmb-vmg-representation-method.md) jest wybrany jako [metoda reprezentacji](vmb-vmg-representation-method.md). Te opcje wskazują model dziedziczenia definicji klasy nie zostały jeszcze — wystąpił.

## <a name="syntax"></a>Składnia

```
/vmm
/vms
/vmv
```

## <a name="remarks"></a>Uwagi

Opcje są opisane w poniższej tabeli.

|Opcja|Opis|
|------------|-----------------|
|**/vmm**|Określa najbardziej ogólną reprezentacją wskaźnika do składowej klasy jako jedną, która używa wielokrotnego dziedziczenia.<br /><br /> Odpowiedni [słów kluczowych dziedziczenia](../../cpp/inheritance-keywords.md) i argument [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) jest **multiple_inheritance**.<br /><br /> Taka reprezentacja jest większy niż wymagane dla pojedyncze dziedziczenie.<br /><br /> Jeśli model dziedziczenia definicji klasy, dla którego jest zadeklarowany jako wskaźnik do elementu członkowskiego jest wirtualny, kompilator generuje błąd.|
|**/vms**|Określa najbardziej ogólną reprezentacją wskaźnika do składowej klasy to taki, który używa nie dziedziczenia lub pojedyncze dziedziczenie.<br /><br /> Odpowiedni [słów kluczowych dziedziczenia](../../cpp/inheritance-keywords.md) i argument [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) jest **pojedynczego dziedziczenia**.<br /><br /> Jest to najmniejsza możliwa reprezentacja wskaźnika do składowej klasy.<br /><br /> Jeśli model dziedziczenia definicji klasy, dla którego jest zadeklarowany jako wskaźnik do elementu członkowskiego jest wiele lub wirtualny, kompilator generuje błąd.|
|**/vmv**|Określa najbardziej ogólną reprezentacją wskaźnika do składowej klasy jako jedną, która używa wirtualnego dziedziczenia. Nigdy nie powoduje błąd i jest ustawieniem domyślnym.<br /><br /> Odpowiedni [słów kluczowych dziedziczenia](../../cpp/inheritance-keywords.md) i argument [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) jest **virtual_inheritance**.<br /><br /> Ta opcja wymaga większych wskaźnika i dodatkowy kod do interpretacji wskaźnika niż inne opcje.|

Po określeniu jednej z tych opcji modelu dziedziczenia tego modelu jest używany dla wszystkich wskaźników do składowych klasy, niezależnie od ich typ dziedziczenia i tego, czy wskaźnik jest zadeklarowany przed lub po klasie. W związku z tym, jeśli zawsze używasz klasy dziedziczące, można zmniejszyć rozmiar kodu przy kompilacji z **/VMS**; Jednakże, jeśli chcesz mieć najbardziej ogólną wielkość (kosztem największych reprezentacja danych), należy skompilować z **/vmv**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/vmb, /vmg (Metoda reprezentacji)](vmb-vmg-representation-method.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
