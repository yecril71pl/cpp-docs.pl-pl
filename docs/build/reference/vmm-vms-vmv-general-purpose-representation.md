---
title: -vmm, - vms, - vmv (ogólnego przeznaczenia reprezentacja) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vms
- /vmm
- /vmv
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd2f79238c890d43678332203acbe9d935a54102
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm, /vms, /vmv (Ogólna reprezentacja celu)
Używane podczas [/vmb, / vmg (metoda reprezentacji)](../../build/reference/vmb-vmg-representation-method.md) został wybrany jako [metoda reprezentacji](../../build/reference/vmb-vmg-representation-method.md). Te opcje wskazują modelu dziedziczenia definicji klasy nie zostały jeszcze napotkano.  
  
## <a name="syntax"></a>Składnia  
  
```  
/vmm  
/vms  
/vmv  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcje zostały opisane w poniższej tabeli.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/vmm**|Określa najbardziej ogólna reprezentacja wskaźnika do elementu członkowskiego klasy jedną, który używa dziedziczenie wielokrotne.<br /><br /> Odpowiednie [— słowo kluczowe dziedziczenia](../../cpp/inheritance-keywords.md) i argument [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) jest **multiple_inheritance**.<br /><br /> Taka reprezentacja jest większy niż wymagane dla pojedynczego dziedziczenia.<br /><br /> W przypadku wirtualnych modelu dziedziczenia definicji klasy, dla którego jest zadeklarowany jako wskaźnik do elementu członkowskiego, kompilator generuje błąd.|  
|**/vms**|Określa najbardziej ogólna reprezentacja wskaźnika do elementu członkowskiego klasy, który korzysta z dziedziczenia lub żaden pojedyncze dziedziczenie się.<br /><br /> Odpowiednie [— słowo kluczowe dziedziczenia](../../cpp/inheritance-keywords.md) i argument [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) jest **pojedynczego dziedziczenia**.<br /><br /> Jest to najmniejsza możliwa reprezentacja wskaźnika do elementu członkowskiego klasy.<br /><br /> Jeśli model dziedziczenia definicji klasy, dla którego jest zadeklarowany jako wskaźnik do elementu członkowskiego jest wiele lub wirtualne, kompilator generuje błąd.|  
|**/vmv**|Określa najbardziej ogólna reprezentacja wskaźnika do elementu członkowskiego klasy, aby używa wirtualnego dziedziczenia. Nigdy nie powoduje, że wystąpił błąd i jest ustawieniem domyślnym.<br /><br /> Odpowiednie [— słowo kluczowe dziedziczenia](../../cpp/inheritance-keywords.md) i argument [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) jest **virtual_inheritance**.<br /><br /> Ta opcja wymaga większych wskaźnik i dodatkowy kod, aby zinterpretować wskaźnika niż inne opcje.|  
  
 Po określeniu jednej z tych opcji modelu dziedziczenia modelu jest używany dla wszystkich wskaźników do elementów członkowskich klasy, niezależnie od ich typ dziedziczenia i określa, czy wskaźnik jest zadeklarowany jako przed lub po klasie. W związku z tym jeśli zawsze używać klasy dziedziczące pojedynczo, można zmniejszyć rozmiar kodu przez kompilowania przy użyciu **/VMS**; jednak jeśli chcesz użyć w przypadku większości (kosztem największy reprezentacja danych), kompilować z **/vmv**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/ vmb, / vmg (metoda reprezentacji)](../../build/reference/vmb-vmg-representation-method.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)